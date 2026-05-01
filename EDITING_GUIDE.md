# Bill Brien Retreat Case App — Editing Cheat Sheet

## How to open and edit
1. Open VS Code
2. File → Open Folder → select the `retreat-case` folder
3. Click `index.html` in the sidebar
4. Use **Cmd+F** (Mac) or **Ctrl+F** (Windows) to search for text you want to change
5. Save with **Cmd+S** / **Ctrl+S**
6. Open `index.html` in Chrome to preview (just double-click the file)
7. After each save, refresh Chrome to see changes

---

## Common edits (copy-paste ready)

### 1. CHANGE THE MENTIMETER CODE
Search for: `XXXX XXXX`
Replace with your actual Mentimeter code, e.g.: `4829 1037`
(appears 4 times — once per poll)

### 2. CHANGE A DISCUSSION QUESTION
Search for the question text, e.g.:
  `What is your differential diagnosis`
Edit the text between the quotes.

### 3. ADD A NEW DISCUSSION QUESTION
Copy this line and paste it where you want it:
```
+prompt("Your new question here?","Discuss for 3 minutes")
```
The second part (time) is optional — you can also write:
```
+prompt("Your new question here?")
```

### 4. SWAP AN IMAGE
DON'T touch the code. Just:
- Save your new image to the `images/` folder
- Name it EXACTLY the same as the file you're replacing
  e.g., replace `reticulin.jpg` with your new `reticulin.jpg`

### 5. ADD A NEW IMAGE
Two steps:
a) Save the image in the `images/` folder (e.g., `new_stain.jpg`)
b) In the code, add this line where you want it:
```
+img('new_stain.jpg','Caption describing the image')
```

### 6. CHANGE CBC VALUES
Search for: `Aug 2025` or `Feb 2026` or the numbers `139`, `59`, etc.
Edit the numbers directly.

### 7. CHANGE A MUTATION IN THE NGS TABLE
Search for: `c.524G` or `Arg175His` or `4.1%`
Edit the text directly.

### 8. ADD/REMOVE A DATABASE CARD
Each database card is a block that starts with:
  `+'<div class="card db-card"`
and ends with:
  `</div></div></div>'`
Delete the whole block to remove a database.
Copy and modify a block to add a new one.

### 9. CHANGE MENTIMETER POLL QUESTION TEXT
Search for: `Mentimeter Poll #1`
The description text is right after it in the same line.

### 10. ADD A WHOLE NEW SECTION
This is more advanced. Copy an entire `function sec_()` block,
rename it (e.g., `sec11`), add it to the STAGES array at the top,
and add a case in the switch statement. Ask Claude if stuck.

---

## Things to be careful about

⚠️  DON'T delete any of these characters: + ' " ( ) { }
     They're part of the code structure.

⚠️  Text uses SINGLE QUOTES (') not double quotes (")
     inside the JavaScript functions.

⚠️  If you need an APOSTROPHE in your text (like "don't"),
     write it as: don\u2019t  (this is the Unicode curly apostrophe)
     or escape it as: don\'t

⚠️  Special characters that need escaping:
     Apostrophe:  \'  or use \u2019
     Less-than:   &lt;
     Greater-than: &gt;
     Ampersand:   &amp;

⚠️  If something breaks (page goes blank), undo with Cmd+Z
     until it works again, then try a smaller edit.

---

## Testing your changes

1. Save the file (Cmd+S)
2. Go to Chrome, open index.html
3. Refresh the page (Cmd+R)
4. Click through all 10 sections to make sure nothing broke
5. If a section is blank → you probably have a quote/bracket error
   → Undo (Cmd+Z) and try again

---

## Quick reference: helper functions you can use

img('filename.jpg','Caption text')     → inserts an image with caption
prompt("Question?","Time hint")        → inserts a teal discussion prompt
prompt("Question?")                    → prompt without time hint
menti(1,"Question text")              → inserts a Mentimeter poll card
                                         (change the number 1-4 for each poll)

---

## Deploying after edits

After making your edits:
1. Go to app.netlify.com/drop
2. Drag the ENTIRE retreat-case folder (with index.html AND images/)
3. Get your new URL
4. If you already deployed before, you can re-deploy to the same URL
   by logging into Netlify (free account) and dragging the folder
   onto your existing site's "Deploys" page

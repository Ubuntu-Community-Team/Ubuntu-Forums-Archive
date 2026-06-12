---
title: "Removing File Extension in Python"
date: 2010-11-28
forum: General Help
---

### Post by gerowen on 2010-11-28
I've had a little python program/script I wrote a long time ago for my wife that converts .lit files to pdf.  I'm re-working the way it runs to include some zenity windows so she can click on the file she wants to convert instead of having to type in the full path, or drag its icon into a command window.  Anyway, part of the current version asks, "What is the Title of the Book", and then it uses that input to generate the filename of the PDF.  I would like it to take the original filename, remove the file extension, and take the remaining string as input for the resulting PDF file instead of bothering the user to type the name of the book.

---

### Post by DaithiF on 2010-11-28
try **os.path.splitext **
e.g.

```
file = 'somefile.lit'
(name,ext) = os.path.splitext(file)

```

---

### Post by aeiah on 2010-11-28
instead of using zenity, why not just add it to the right-click menu? both nautilus and thunar have custom actions. then you could just right click on the .lit (or several at once) and select 'convert to pdf' and it could output them to the same directory or the desktop.

but anyway, id just split it on the last dot myself

```

for file in sys.argv[1:]: # for all arguments (selected .lit files)
        title = file.split('.')[-1]
        #etc

```

---

### Post by gerowen on 2010-11-28
Thanks to both of you!  I've got it removing the extension, except now I'm not sure of how to get python to actually retrieve the value of the selected file as a string.  I'm thinking about just redoing the whole thing as a regular bash script, because there's nothing that I'm really doing that can't be done with bash.  Here's the lines I have in python right now though for getting the original filename, and while in the terminal it displays the path to the file I select, the variable returns a value of 0.

```

os.system('zenity --info --title="Lit2PDF" --text="Please select the file you wish to convert."')
print ""
infile=os.system('zenity --file-selection --filename=$HOME --title="Select a LIT file"')

```

---


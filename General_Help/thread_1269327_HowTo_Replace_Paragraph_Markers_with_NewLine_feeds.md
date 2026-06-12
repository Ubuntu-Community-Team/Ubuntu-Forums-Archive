---
title: "HowTo: Replace Paragraph Markers with NewLine feeds in OOo Writer"
date: 2009-09-18
forum: General Help
---

### Post by Onesimus on 2009-09-18
**The Problem**
You have a document where you want to replace all (or some) of the paragraph markers with newline feeds (Normally inserted into a document by typing: Shift+Return).  Unfortunately, the ‘Search for’ box in the Find & Replace Dialog Window (Ctrl+F) interprets the regular expression \n as a newline whilst the ‘Replace with’ box interprets \n as a paragraph mark. See the wiki page (Section 16) for more details: [http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Regular_Expressions_in_Writer](http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Regular_Expressions_in_Writer)

**The Solution**
Before starting this tutorial it would be wise to save your document !

Step 1:  Switch on ‘Nonprinting characters’ with Ctrl+F10 or View->Nonprinting Characters.
[INDENT]This isn’t necessary but helps to visualise what is occurring.[/INDENT]

Step 2:  Insert a newline character into the document  (Shift+Return)

Step 3:  Select just the newline character and copy it to the clipboard (Crtl+C)

Step 4:  If all the paragraph markers in the document are to be replaced then go to Step 5, otherwise select the required text to change

Step 5:  Open the Find & Replace dialog window (Crtl+F)

Step 6:  Insert $ into the ‘Search for’ box  (This finds the paragraph markers)

Step 7:  Click ‘Find All’

Step 8:  Click ‘Close’ in the dialog window

[INDENT]The document should now highlight all the instances of the paragraph markers, as they will be currently selected.[/INDENT]

Step 9:  Paste the contents of the clipboard (Ctrl+V)

Step 10:  Optional.  Turn off the viewing of nonprinting characters (achieved by doing Step 1)

You’re done !

This was tested for OpenOffice 3.1 on Ubuntu 8.10

---


---
title: "How can I make a script run when double clicking a file with extension .doc or .docx?"
date: 2012-01-26
forum: General Help
---

### Post by ctt2 on 2012-01-26
I want to make textmaker open with my .doc files and need to know how to point it to a custom script. In going through the conventional "open with" process textmaker is not listed in the main programs or the show other applications.

On doing a "whereis textmaker" I get:
textmaker: /usr/bin/textmaker

That file is just a script which contains the following:
#!/bin/sh
# A script to run TextMaker.
"/usr/share/office2010"/textmaker "$@"

Again my goal is to open .doc and .docx with textmaker, anyone that knows how I can accomplish this would be greatly appreciated.

The program is not listed in the "show other applications" section so the obvious normal answer will not work.:confused:

---

### Post by ajgreeny on 2012-01-26
Right click on the filetype you want to open but choose "Other application" and then Custom command.  In the box that appears for the command enter the full pathway of the file you mentioned ```
/usr/bin/textmaker
``` and see if that works  You may need to ensure that the textmaker file is executable first, so check that with ```
ls -l /usr/bin/textmaker
```

---

### Post by ctt2 on 2012-01-29
Custom command is not anywhere in the open with menu.. even upon clicking the open with tab and looking through other applications. I will google the custom command option to see what I can find.

---

### Post by ctt2 on 2012-01-29
[http://askubuntu.com/questions/67382/add-custom-command-in-the-open-with-dialog](http://askubuntu.com/questions/67382/add-custom-command-in-the-open-with-dialog)

Following this method to add it to the open with list worked. Thanks for the guidance.

---


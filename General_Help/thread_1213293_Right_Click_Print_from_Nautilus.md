---
title: "Right Click Print from Nautilus"
date: 2009-07-14
forum: General Help
---

### Post by hwttdz on 2009-07-14
I recently used windows and was very happy to make use of the right click->print which can be done on multiple files.  Need to print all the files in a directory, simply ctrl+a, right click->print and it's done.  Is there a way to do this in ubuntu? It bothers me a little when something is easier in windows.  I realize I could probably "ls|xargs lpr" or "lpr *", but I'm looking for something from nautilus.

---

### Post by TheCrap on 2009-07-14
maybe the is the solution: [http://www.linux4all.net/ubuntu_printing_with_a_mouse_rightclick](http://www.linux4all.net/ubuntu_printing_with_a_mouse_rightclick)

---

### Post by hwttdz on 2009-07-17
So I had tried something similar, namely just using lpr instead of cupsdoprint.  I don't know what the advantages of one versus the other would be.  However a command that works from the cli, doesn't seem to work when it's in this script.  Any suggestions?

```
#!/bin/bash
files=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > ~/temp.txt
lpr $files
exit 0
```

Is that it's not handling the spacing right?  When I cat ~/temp.txt I see
file name.txt
where there's a space between file and name.

---

### Post by kaibob on 2009-07-17
Post deleted by Kaibob. I don't think I understood the issue being raised by the OP.

---

### Post by Konrad Ansehelm on 2010-05-09
> **hwttdz said:**
> So I had tried something similar, namely just using lpr instead of cupsdoprint.  I don't know what the advantages of one versus the other would be.  However a command that works from the cli, doesn't seem to work when it's in this script.  Any suggestions?

```
#!/bin/bash
files=$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS > ~/temp.txt
lpr $files
exit 0
```Is that it's not handling the spacing right?  When I cat ~/temp.txt I see
file name.txt
where there's a space between file and name.
It won't work with files that have spaces in them. Solution with lpr: [http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus](http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus)

---

### Post by isaquealves on 2010-12-11
Maybe the best solution is to use Nautilus Actions.

Install nautilus-actions package, execute the "Nautilus Actions Settings" from "System > Preferences" menu and add some action:

Action Tab
[INDENT]Nautilus Item
       [INDENT]Context Label : Print
           Display item in selection context menu
           Display item in location context menu (not needed)[/INDENT]
    Action Properties: Enabled
[/INDENT]
Command Tab
    [INDENT]Profile
        [INDENT]Label: Default[/INDENT]
    Command:
        [INDENT]Path: lp
        Parameters: %M (click on the legend button to see additional info)[/INDENT][/INDENT]
Edit the other tabs information as you would like to your nautilus to behave.
Save the action, restart nautilus and Bingo!
Your context menu will show up "Print"...

---

### Post by mrhhug on 2011-03-15
isaquealves, 

you sir or madam are good.
worked perfectly

---


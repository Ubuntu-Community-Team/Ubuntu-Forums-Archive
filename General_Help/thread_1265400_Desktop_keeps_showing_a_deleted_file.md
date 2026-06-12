---
title: "Desktop keeps showing a deleted file"
date: 2009-09-13
forum: General Help
---

### Post by biebel on 2009-09-13
Hey,

I placed 2 .jpg files on my desktop, made them hidden by adding a . in front of the filename and moved them to another place.

Even though there is no reference to it in the /home/user/Desktop folder they are still visible (thumbnail and filename still visible) on my desktop (even after a reboot). I can't move the icons manually (There was an error getting information about ".garfieldje.jpg".) or delete them (nothing happens when I (shift-)delete them and the "delete" is grayed out when right clicking) , but when I do a clean up by name they do get moved.
When I double click the link I get "Could not display "path/filename where I moved them to". The file is of an unknown type" so I'm guessing it's actually a simlink, but an ls -a -l in ~/Desktop doesn't reveal any simlinks.

I did a search for the text string "garfield" in every file in every folder in my home folder, but I get no results.

If anyone knows where I should look please let me know.

If I can recreate the problem after fixing it, against which package should I file a bug report?

---

### Post by drs305 on 2009-09-13
I'm having a bit of trouble following exactly what is happening, but something I'd try would be to make a copy of the two original files (wherever you placed them) and then delete the originals. Then go back and see if the Desktop items disappeared. They probably won't have, but I'd then try deleting them again now that any links are broken. 

Note this shouldn't be necessary and breaking a soft link shouldn't really be required - it's just something to try.

---

### Post by biebel on 2009-09-13
I know it's a confusing explanation. :)

I have tried what you suggested already, but it didn't help.

A step by step explanation of what happened.
1. copied 2 files from my camera to desktop
2. renamed them to .garfieldje.jpg and .garfieldje2.jpg (added the dots because I mistakinly assumed that they would not show up on the desktop like that)
3. moved them to the folder I needed them in
4. noticed they were still showing on my desktop
5. tried to delete them
6. removed every instance of the files on my computer
7. did a "sudo find / -name "*garfield*"" from cli. No result
8. did a "search for file" from gui for files * 
contains the text "garfield"
+show hidden and backup files
+follow symlinks
no positives.
9. rebooted as if I was having a windoze problem. Still no difference
10. posted here

I'm really puzzled by this one.

[edit]
So I created a new .garfieldje.jpg empty file in ~/Desktop. When I do it from cli nothing changes on the desktop, but when I do it with the gui create new file it makes a new file, allows me to edit the filename, but when I enter .garfieldje.jpg it reverts to "new file" on the desktop while the correct file name does get createed in ~/Desktop and it does open in gedit as .garfieldje.jpg when i double click it.

And here I was thinking I was getting the hang of ubuntu :/
[/edit]

---

### Post by drs305 on 2009-09-13
> **biebel said:**
> 
8. did a "search for file" from gui for files * 
**contains the text "garfield"**
+show hidden and backup files
+follow symlinks
no positives.
9. rebooted as if I was having a windoze problem. Still no difference
10. posted here

I'm really puzzled by this one.

Just a point: If searching for a jpg file via the GUI Search for Files, the 'contains the text' would eliminate returns since the search would be looking *inside* the file for the text "garfield". You would want "garfield" in the "Name contains" window. Even so, the "sudo find" command should have found it...

---

### Post by Malta paul on 2009-09-13
Try Right clicking on the file, click properties>permission and see if its /root. If so Alt+F2 'gksudo nautilus' and change the permissions to 'read and write' Rename by deleting the . it should now delete (I hope!)

:D

---

### Post by biebel on 2009-09-13
The problem is that the files don't exist anymore at all, yet my desktop keeps showing it. So the permission tab only reveals that the permissions could not be determined.

---

### Post by Malta paul on 2009-09-13
Well there is 'Gnome Commander' that will remove it for you, I use it and its great.
You can find it in Applications>Add/Remove then search.

---

### Post by biebel on 2009-09-13
I'm sorry for being rude, but I am not an utter noob...
**the files don't exist in any form in any way that can be accessed through a file manager**
They have been deleted using the commandline and no file manager will find files that don't exist...
So if you want to suggest a program for finding the original files don't bother, it won't help me at all.
Thanks for trying to help me though.

What I do need to know is which program manages the links on the desktop and where I can find its config files.

---


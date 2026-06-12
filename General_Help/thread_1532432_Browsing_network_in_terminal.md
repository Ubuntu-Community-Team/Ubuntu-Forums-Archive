---
title: "Browsing network in terminal"
date: 2010-07-16
forum: General Help
---

### Post by puma1 on 2010-07-16
I am new to ubuntu, and i am wondering what is the equivalence of doing a START>RUN \\192.168.1.XXX\c$

Is it only about mounting a network location by knowing the exact share name?

Thanks!

---

### Post by Morbius1 on 2010-07-16
If all you want is a "quick mount" then the command would be:
```
gvfs-mount smb://ip_address/share_name
```But the windows command you're talking about did more than that ( if I remember correctly ). It created a temporary mount and then launched Windows Explorer to that location. The equivalent to that is:
```
nautilus smb://ip_address/share_name
```

---

### Post by puma1 on 2010-07-16
Ok now that it is mounted what next? How do i access the mount?  thats where i am confused. i tied both commands and it seemed to have worked.. when i run again it says already  mounted..

---

### Post by puma1 on 2010-07-16
So i typed $ nautilus smb://192.168.1.100/share

and it took.. ok .. now what? what syntax do i use to access what I just mounted. in windows it would be assigned a drive letter, what is it in linux?

---

### Post by WorMzy on 2010-07-16
Check in /media, that's where Ubuntu mounts filesystems by default.

---

### Post by puma1 on 2010-07-16
went to /home/media, and there is nothing in there.

---

### Post by puma1 on 2010-07-16
ok i think i am getting it now... i used the nautilus smb:// command.. when i do that i see the mount appear on the desktop thats cool for the GUI, but from within the terminal how do I access this mount?

---

### Post by WorMzy on 2010-07-16
I meant just /media, not /home/media, but it's a moot point anyway. After testing it myself, it seems it doesn't create a "physical" mount point (such as a folder in /media), it just temporarily stores login information for the remote file system and allows you to quickly access it by entering the address into nautilus' address bar. It'll even create a temporary "places" entry in the Places menu, and in nautilus' Places sidebar.

[[img]http://www.ubuntu-pics.de/thumb/106278/workspace_1_115_6csoVF.png[/img]](http://www.ubuntu-pics.de/bild/106278/workspace_1_115_6csoVF.png)

EDIT: Actually, scratch that, it creates a directory in ~/.gvfs

You can access it via terminal by running
```
cd ~/.gvfs/<NAME OF FOLDER>
```

---

### Post by puma1 on 2010-07-16
im looking more for a terminal route..  through the gui i see where the mount is, not in the terminal.

---

### Post by WorMzy on 2010-07-16
Edited my post while you were writing yours, I think. Have a look in ~/.gvfs.

---

### Post by puma1 on 2010-07-16
nice that worked, thanks. how did you even see that folder to chck it? its a hidden folder? .gvsf?

---

### Post by marshmallow1304 on 2010-07-16
To view hidden folders in nautilus, press Ctrl+h.


You might also find useful [nautilus-open-terminal]("apt://nautilus-open-terminal"), which allows you to easily open any folder in a terminal while browsing in nautilus.

---

### Post by puma1 on 2010-07-16
when you say "in nautilus" what do you mean exactly? Do you mean the general GUI, the file browser?

---

### Post by marshmallow1304 on 2010-07-17
Yes, nautilus is the default file browser/manager in Ubuntu.

---

### Post by Morbius1 on 2010-07-17
Telling you how to mount the remote share using gvfs and then not telling you where it mounted was incredibly sloppy on my part.

I sincerely apologize.

---

### Post by puma1 on 2010-07-17
Please, you guys are helping me out i appreciate it. Couple days ago i installed Ubuntu clean on my thinkpad and said Ill jump right in. I am a life long windows guy in the IT field... but few days later with some help from you guys i have this machine screaming. just so much too learn. its like another world, so much is different. thanks for the help.

---


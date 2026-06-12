---
title: "I typed sudo chmod a+rwx HTCH-2TB/ - wat did it do?"
date: 2010-09-22
forum: General Help
---

### Post by fuzzylogic25 on 2010-09-22
I got a new drive, created it a ext4 partition to it and named it HTCH-2TB. The drive is for data/back up purposes so the OS is not on it. I couldnt paste to it so after looking online I typed:


sudo chmod a+rwx HTCH-2TB/

and also typed

sudo chown john HTCH-2TB/


I believe the last one is what I wanted, so I could modify the drive whenever I need to. However, now when i type "ls" the HTCH-2TB folder is highlighted, like the tmp folder. Why is that? what exactly has happened? how do i Change it back?

---

### Post by sisco311 on 2010-09-22
> **fuzzylogic25 said:**
> Why is that? what exactly has happened? 


It's because the directory is world writable, which means anyone can create, remove or rename files in the directory.

> **fuzzylogic25 said:**
> 
how do i Change it back?

You probably want:
```
sudo chown john: HTCH-2TB/
chmod 0755 HTCH-2TB/
```
(read/write/execute for user john, read/execute for the group john and read/execute for others)

or, if you don't want to assign read permissions for others, then
```

sudo chown john: HTCH-2TB/
chmod 0750 HTCH-2TB/

```

For more info, take a look at:
[uhelp]community/FilePermissions[/uhelp]
and
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by Rubi1200 on 2010-09-22
I don't understand why you would execute a command without knowing what it might do!

There are always people here on the forums, like sisco311, who can explain what a command will, or won't, do; maybe next time ask first?

---

### Post by t0p on 2010-09-22
This isn't aimed at the OP necessarily: but it can be very harmful to the health of your system if you type in commands as root (ie prefixed with "sudo") when you don't know what the command is going to do.  This site is pretty good in this regard, but it's not unknown for naughty children to suggest the use of malicious commands.  For instance, there is the command **sudo rm -r /** which will nuke your installation.

The command used by the OP is not on that scale.  But still... it's something to bear in mind.  If the OP's computer is used by more than one user, that command would give world-writable access to the directory in question.  Which *could* be catastrophic, depending on the circumstances.

---

### Post by s.fox on 2010-09-22
Hello,

I would recommend reading [this]("http://ubuntuforums.org/announcement.php?a=54") announcement regarding running commands that you do not understand.

-Silver Fox

---


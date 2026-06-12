---
title: "Trying to access/reformat external HDD"
date: 2009-11-23
forum: General Help
---

### Post by cmmichael on 2009-11-23
As a preliminary step to upgrading from Hardy, I need to stop procrastinating and figure out how to access an external HD, so I can back up my main HD. I have previously reformatted the external HD to ext3 by mounting it inside my desktop box, but now I have a laptop running XP, and I would like to totally reformat the drive as fat32. 

So far I have only gotten messages that I am not the owner of the drive, or I do not have permission to copy files to it.

---

### Post by t0p on 2009-11-23
For a start, you should be able to reformat the drive by using Gparted as superuser (ie with "gksudo" command prefix).  If you haven't actually installed Ubuntu yet, and are using the Ubuntu live CD, I think it's called "Partition Editor" or somesuch in the menu.  If you get the permissions error, try running it by pressing **Alt+F2** and typing into the Run box

```
gksudo gparted
```

You will be prompted for a password.  Unfortunately I don't know what the user password is in a live session.  Perhaps someone else can help?

---

### Post by alphaniner on 2009-11-23
Last I checked you don't get prompted for a password in a live session.  gParted is 'installed' by default in a live session, and is under System -> Administration.  In 9.04 and previous, it was named Partition Editor.  In 9.10 it is named gParted.

---

### Post by sgosnell on 2009-11-23
With LiveCD, you don't need a password for sudo. You can't make changes to the system on the CD, so there is no need to worry about it.  Just boot the CD, choose to try Ubuntu without any changes to your system, and when it boots up run gparted, or partition editor, whatever it says, from the System/Administration menu.  Format the external drive to FAT32, making sure you click on Apply Changes, and then boot into Windows normally and it should see the external drive and let you copy to it.

---


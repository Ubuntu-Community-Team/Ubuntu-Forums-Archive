---
title: "[help] chntpw"
date: 2011-09-04
forum: General Help
---

### Post by snoopunit on 2011-09-04
so basically i'm trying to reset/change the password on my computer. I'm running of a live CD of ubuntu 11.04 right now, and i'm having trouble changing directories to access the right files. cd /media/ works, however, trying to cd to any folder within the hdd returns an "no such file or directory" message. I'm following the guide posted here: [http://www.makeuseof.com/tag/3-ways-to-reset-the-forgotten-windows-administrator-password/](http://www.makeuseof.com/tag/3-ways-to-reset-the-forgotten-windows-administrator-password/) . 

any help is appreciated :D

---

### Post by spiky001 on 2011-09-04
Did you mount the drive (correct drive)

---

### Post by ajgreeny on 2011-09-04
What is the output of ```
ls /media/
```I suspect nothing will show as there will be no mounted drives, so open up the file manager (nautilus) and then double click on the drives (or places) icons that show in the left hand pane.  That should mount the drives for you and now you should be able to use ```
ls /media
```to see all the subfolders and also use either nautilus or terminal to navigate to wherever you want to go.

However, before you do any of that, there is a much better way to change, or reset your password shown at [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) and I suggest you try that first.  From what I read of your linked site's way of doing the same thing, it is much more complicated.

---

### Post by spiky001 on 2011-09-04
ajgreeny it looks like op is trying to reset password on windows according to his link

---

### Post by ajgreeny on 2011-09-04
> **spiky001 said:**
> ajgreeny it looks like op is trying to reset password on windows according to his link
OMG, so he is!!

Silly me;  I didn't look before I leaped into action and replied, and the lost Ubuntu password is so common, I just answered too quickly.  No windows here, so I didn't even think about that possibility.

---


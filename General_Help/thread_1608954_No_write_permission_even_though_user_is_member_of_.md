---
title: "No write permission even though user is member of folder group"
date: 2010-10-29
forum: General Help
---

### Post by roger_racoon on 2010-10-29
Hello all,
I'm having an odd problem (although I'm probably missing something obvious to a non-semi-newbie):
I have a directory used for samba shares which is owned by user **fred**, a system user which the windows clients on my network authenticate with to access the shares. I, **roger**, want to access the directories without having to put my 'sudo boots' on every time, so I made the directory group **users** and added **roger** to that group, and changed the file/folder modes from 0755 to 0775.
However I still do not have write permissions inside the directory; I still seem to be considered 'other' and hence only have read and execute.
I am still very much a rookie Linux user, so have I misunderstood the way file permissions work?
Thanks in advance,
Roger R.

---

### Post by sohlinux on 2010-10-29
easiest would be to use konqueror or similar file manager as root user then change the permissions and owners of the folders in question - just right click on the folders click properties - permissions then choose your owners and groups and chmod values

---

### Post by roger_racoon on 2010-10-29
Thanks for your reply, however I run ubuntu server, not desktop and hence don't have access to the graphical tools. Besides, wouldn't this achieve the same thing as using chgrp, chown and chmod?
Roger R.

---

### Post by sohlinux on 2010-10-30
> **roger_racoon said:**
> Thanks for your reply, however I run ubuntu server, not desktop and hence don't have access to the graphical tools. Besides, wouldn't this achieve the same thing as using chgrp, chown and chmod?
Roger R.

yes from the terminal chown and chmod should do it, if not then I dont have a solution

I also run a server and I have gnome installed too, I find it makes a lot of things easier to do gui style

---

### Post by sohlinux on 2010-10-31
if you are running a server you could try webmin which has a nice samba plugin which may help you solve your problem.

---

### Post by roger_racoon on 2010-11-03
Thanks for your help - for whatever reason the permissions now all seem to work as expected; I probably was just having a bit of a 'moment' I suppose!
Roger

---

### Post by stuarttanner on 2010-11-03
You can change permissions through sudo nautilus works for me:)

---


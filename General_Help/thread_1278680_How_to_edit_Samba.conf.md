---
title: "How to edit Samba.conf"
date: 2009-09-29
forum: General Help
---

### Post by Zoandar on 2009-09-29
Can someone tell me the trick to editing a *conf file, such as Samab.conf? I have a couple  possible fixes to problems that require editing such files, but when I edit that file and try to save it, I get an error saying I "don't have permission". I have looked extensively on two forums, but can't find any post spelling out how to do this correctly. 

Thanks. 

Zoandar

---

### Post by undecim on 2009-09-29
You need to be root (administrator) to edit those files.

To get root access, you need to use "gksu" (if using a graphical program) or "sudo" (if using a terminal program)

for example, press ALT+F2, to get the run dialog, and type "gksu gedit /etc/samba/smb.conf" to edit smb.conf with gedit.

or, from a terminal, type "sudo nano /etc/samba/smb.conf" to edit the file with nano

EDIT: Also, it is wise to make a backup of those files before editing them... running this in a terminal will make a copy of smb.conf to smb.conf.bak:

cp /etc/samba/smb.conf /etc/samba/smb.conf.bak

This way, you can restore the file later if you mess it up badly, by using:

cp /etc/samba/smb.conf.bak /etc/samba/smb.conf

You could also do the same things by type "gksu nautilus" into your ALT+F2 box, but it's not recommended, because it's easy to break stuff doing that.

---

### Post by Iowan on 2009-09-30
Personally, I like to back up the original file to have as a guide. I can then delete the lines (and comments) that I don't need, but can reference the original (backup) file if I need to check something later.

---

### Post by bodhi.zazen on 2009-09-30
sudo -e /path/to/file_needing_edit

If you like nano , and want a back-up

sudo nano -B /path/to/file_needing_edit

I usually do system admin as root so as to not need to keep entering sudo ...

sudo -i

---

### Post by Iowan on 2009-09-30
WOW! Lazy man's delight. On my system, both versions open **nano**, but the first wants to save the file where I'll lose it (/var/tmp...) and appends a weird suffix (XXUGdK6G). The second version (slightly more typing) just saves a copy with tilde (~) after the name. (Yes, I could rename them before saving, but... did I mention lazy?) Sure hope I can remember the tip!
THANKS!!!

---

### Post by Zoandar on 2009-09-30
Thanks for all the suggestions! I had gotten a little into Linux back in March of 2007, and then gotten away from it with other interests. Once I read about sudo and nano I started remembering those commands from before. 

I agree that making backups of the files before editing them is a good idea, and it is a good thing I did. One of the suggestions I had found made my notebook fail to boot the GUI in Ubuntu after I executed it, so I had to revert to the Restore option to get it back. 

I see that Ubuntu 9.04 has done away with logging in as root. But since I had used version 6 back then, this was still allowed at that time. I did try to do that before I wrote and asked for help, but wasn't able, and only more forum excavating led me to learn they had disabled it as a safety measure. 

I did, however, find a nice site that tells how to create an icon that lets you browse as an administrator. Not quite as dangerous as root login, I guess, but very handy for something like editing this conf file. 

Thanks again!

Zoandar

---


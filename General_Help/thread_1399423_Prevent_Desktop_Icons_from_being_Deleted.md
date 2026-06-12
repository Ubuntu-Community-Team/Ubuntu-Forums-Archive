---
title: "Prevent Desktop Icons from being Deleted"
date: 2010-02-05
forum: General Help
---

### Post by stpgod on 2010-02-05
I'm setting up an Ubuntu Computer Lab at my kids' school, and am trying to find a way to lock certain icons to the desktop. For example, I need each user to have Firefox on the desktop, and not be able to delete it. 

I've tried doing a chown on the Firefox shortcut and changing ownership to root, or to myself, but the student account can still just delete it with no problems. 

I've also tried using Sabayon, and while it does bring the shortcut back at each logon, it's not "Marked as Trusted" which is an annoying constant popup.

How can I ensure that when logged on, each user will have a Firefox shortcut, along with a couple other mandatory ones? Some logon script maybe? Any help is appreciated. If you don't lock down the lab, these kids will find a way to muck around with things... :)

---

### Post by Barriehie on 2010-02-05
> **stpgod said:**
> I'm setting up an Ubuntu Computer Lab at my kids' school, and am trying to find a way to lock certain icons to the desktop. For example, I need each user to have Firefox on the desktop, and not be able to delete it. 

I've tried doing a chown on the Firefox shortcut and changing ownership to root, or to myself, but the student account can still just delete it with no problems. 

I've also tried using Sabayon, and while it does bring the shortcut back at each logon, it's not "Marked as Trusted" which is an annoying constant popup.

How can I ensure that when logged on, each user will have a Firefox shortcut, along with a couple other mandatory ones? Some logon script maybe? Any help is appreciated. If you don't lock down the lab, these kids will find a way to muck around with things... :)

So if owner is root and you chmod 766 the .desktop file how does that work for you???

Barrie

---

### Post by stpgod on 2010-02-05
Same thing, they just hit "delete" and it goes right to the trash bin. Doesn't seem to be any effect.

---

### Post by Barriehie on 2010-02-05
My bad in previous post, should be chmod 755 for read and execute for group and others, NOT 766 for read and write.

Barrie

---

### Post by stpgod on 2010-02-05
No difference. Hit "Delete" and it's gone. Is there some permissions problem with my user? Does it have too much power somehow?

---

### Post by JetSirus on 2010-02-05
Use:
sudo chattr +i filename

The file can longer be deleted or changed in any way.

Use:
sudo chattr -i filename

And you can then delete and change the file.

---

### Post by stpgod on 2010-02-05
Woohoo! That seems to have done it, thanks JetSirus!

---

### Post by n1wil on 2011-10-20
Ok it seems the chattr +i command only works if you have an ext based filesystem.  

My file system is Reiserfs and these commands do not work.

I too (and for the same reason) have a need to LOCK desktop icons from being deleted.

please help  :(

---


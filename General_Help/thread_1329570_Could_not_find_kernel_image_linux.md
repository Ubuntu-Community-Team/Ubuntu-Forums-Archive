---
title: "Could not find kernel image: linux"
date: 2009-11-17
forum: General Help
---

### Post by ericus on 2009-11-17
Ok, I have messed up my install of Ubuntu NBR on my eee pc.
Yesterday I tried installing backtrack on a small partition, and then ran sudo grub-update2 and messed around with things like that to try adding it to the grub boot list.

Now when I boot this show up immediatly, not the grub menu:
```
Could not find kernel image: linux
```

And the thing is, I dont wanna go for a fresh install since I have some things in my home folder that's encrypted (unlocks when I login, but uses some long random phrase that ubuntu generated).
I can access my files from a live USB, but of course not the home folder since I've dont got that passphrase.

How can I recover grub2 so it works again?
Will be really grateful if anyone can help me with this..

---

### Post by ericus on 2009-11-17
Shame on me for bumping, but this is really important for me :(

---

### Post by chaanakya_chiraag on 2009-11-17
So you basically can't get into grub?  Have you tried reinstalling grub from the liveCD?  I'll post a link in a sec.

---

### Post by chaanakya_chiraag on 2009-11-17
try this tutorial:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ericus on 2009-11-17
Thank you. Will give it a go.

---

### Post by ericus on 2009-11-17
Okay, found the problem now, but now there is a new one.
 
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          18      144553+  83  Linux
/dev/sda2              19       18503   148480762+   5  Extended
/dev/sda5              19       18254   146480638+  83  Linux
/dev/sda6           18255       18503     2000061   82  Linux swap / Solaris

```
sda1 is the boot partition. I had one named sda3 with backtrack on it, and that was flagged as boot, so I removed it and then added the boot flag to sda1. Now the computer says there is no operating system found... And my boot files are still in sda1, I can see them when I mount it.

What is the next step? Will I ever be able to unlock the encrypted partition if I reinstall grub2? I mean there must be like some kind of configuration on how to unlock it?

---

### Post by chaanakya_chiraag on 2009-11-17
I'm not sure, but I **think** the encryption is completely separated from the grub2 thing.  So it shouldn't be a problem if you reinstall grub2.  Could someone more knowledgeable than I am please confirm/refute this?

---

### Post by ericus on 2009-11-18
Anyone, please?

---

### Post by ericus on 2009-11-18
This is what I will do when I get home from work:
* Backup existing /boot
* Delete it and do a fresh install of grub 2

Does anyone know if I ever will be able to uncrypt my /home again if I do it like this?

---

### Post by chaanakya_chiraag on 2009-11-18
Do you mean access your files?  As long as **Ubuntu** is the one handling the /home encryption, you should be fine.  As I said before, I don't think grub handles hard drive encryption.

---

### Post by ericus on 2009-11-18
Reinstalling grub2 did the trick, and now everything works as before :)

Thanks for all your help!

---

### Post by chaanakya_chiraag on 2009-11-19
No problem!  Just mark the thread solved by going to Thread Tools -> Mark Thread as Solved so that others can learn from your experience!  Thanks!

---


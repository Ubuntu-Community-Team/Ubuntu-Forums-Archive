---
title: "Will not boot into Ubuntu - Ownership problem"
date: 2011-11-11
forum: General Help
---

### Post by mcfc4eva on 2011-11-11
I did a boob.

I was getting annoyed with having to change ownership (chown) on a variety of folders/files that I needed to access, so I decided to set the following command;
> sudo chown -R michael /

It may have been something different, but along those lines. Now when I boot up the ubuntu loading screen shows and then it "black screens" and states some kind of error about not having ownership of a certain file/folder.

Is there a way I can reverse what I have done - booting from disc/recovery mode or something, if there is one?

I'm not an experienced user of ubuntu so if anyone could provide a jargon-free dummies guide - I'd be more than grateful! :)

If there is no way of recovering it, would I somehow be able to at least access the files - there are some important ones I really need!

Thanks in advance,
--Michael

---

### Post by dcstar on 2011-11-11
> **mcfc4eva said:**
> I did a boob.

I was getting annoyed with having to change ownership (chown) on a variety of folders/files that I needed to access, so I decided to set the following command;


It may have been something different, but along those lines. Now when I boot up the ubuntu loading screen shows and then it "black screens" and states some kind of error about not having ownership of a certain file/folder.
.........

You have basically wrecked the OS.

You can boot off a live CD and try and change the ownerships back to root, but you have to go into the /home tree and change the ownership of all those user folders back to the correct user.

This will still not guarantee a fix, only a reinstall will.

---

### Post by mcfc4eva on 2011-11-13
> **dcstar said:**
> You can boot off a live CD and try and change the ownerships back to root, but you have to go into the /home tree and change the ownership of all those user folders back to the correct user.
How do I do this?


Also, if it doesn't work is there a way I could at least obtain some important files?

Thanks,
--Mike

---

### Post by philinux on 2011-11-13
> **mcfc4eva said:**
> How do I do this?


Also, if it doesn't work is there a way I could at least obtain some important files?

Thanks,
--Mike

Boot off a livecd and copy files you need to a usb stick.

---

### Post by Cyclane on 2011-11-13
As you can read above this is a classic way of ruining your linux install. Best way to get it up and running again is by re installing. And indeed best way to back up your files is to boot from a live USB (ubuntu.com explains how) and copy your files to a external HD.

---


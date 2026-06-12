---
title: "way to verify data after a CD burn, like CDBurnerXP does?"
date: 2011-05-16
forum: General Help
---

### Post by nrundy on 2011-05-16
On Windows, I always used CDBurnerXP to burn data CDs. One of the features I liked was the setting to verify the data after a Burn. This helped assure me that the CDs I burned for data backup were burned accurately.

Brasero does not appear to have this feature. Should I be concerned? Is there burning software for ubuntu that does? how can I ensure the integrity of a burn without a verification feature?

---

### Post by lykwydchykyn on 2011-05-16
K3B can do this.  It's in the software center.

---

### Post by ajgreeny on 2011-05-17
> **lykwydchykyn said:**
> K3B can do this.  It's in the software center.
I agree it does if you have the full kde desktop installed, but the last time I used it in gnome, it would never verify the data after burning, and threw up an error message which I now can not remember in detail.  Is this normal or was I just unlucky?

Otherwise it is a good application, and one I used in Kubuntu with hardly a single problem.  I moved from Kubuntu when KDE4 came along, and have been with Ubuntu and gnome ever since.

---

### Post by lykwydchykyn on 2011-05-17
> **ajgreeny said:**
> I agree it does if you have the full kde desktop installed, but the last time I used it in gnome, it would never verify the data after burning, and threw up an error message which I now can not remember in detail.  Is this normal or was I just unlucky?


I don't know, I haven't used Gnome since about 2003.  I doubt it had anything to do with not having KDE installed, though; K3B is a front-end for console apps, so probably the appropriate console app was not installed or configured.  I believe there's a setup wizard for that.

---

### Post by claracc on 2011-05-18
Brasero does have this feature in menu: edit --> addons, there are two addons:

Verification of image
Verification of disk

You can tick on them and configure too.

---

### Post by ajgreeny on 2011-05-18
> **claracc said:**
> Brasero does have this feature in menu: edit --> addons, there are two addons:

Verification of image
Verification of disk

You can tick on them and configure too.
Not in my version of brasero, but there is a "File checksum" and "Image checksum" option in the Edit ->Plugins menu item, and a "Check integrity" in the Tools menu.

Presumably the same thing?

---

### Post by claracc on 2011-05-18
> Not in my version of brasero, but there is a "File checksum" and "Image checksum" option in the Edit ->Plugins menu item, and a "Check integrity" in the Tools menu.

Presumably the same thing?

It is the same that I have , as my system is in spanish I have made a tranlation into english of the menus, for this reason you can note the difference in the words.

---

### Post by HermanAB on 2011-05-18
$ md5sum file.iso
$ cat /dev/cdrom | md5sum

---

### Post by nrundy on 2011-05-20
Anybody mind giving me a quick run down on how to go about verifying a CD burned with Data after it's complete? The ubuntu brasero wiki didn't go into any detail how to do this. I see that I have three options, md5, sha1, sha256. How exactly do I verify?

I'm assuming I somehow get an md5 of the data I copy into the Brasero burn window? and then use Tools > Check Integrity after the burn and compare what's on the disk to the md5 I created before the burn? How do I get the initial md5? I'd be most appreciative if someone could run this down step by step or direct me to where it's laid out. thanks. GUI directions please :-)

---

### Post by ajgreeny on 2011-05-22
You can find the md5sum of any file by running ```
md5sum *filename*
``` in terminal, so for a data CD you would have to do it for the original and the burned file, I presume.

Perhaps there is a utility that can do it in one go, or a script available from somebody already, but I don't know of one.

---

### Post by lmn. on 2011-05-22
if it's an OS, run it in virtualbox. If everything runs smoothly, chances are it'l work from boot..

---

### Post by coldraven on 2011-05-22
I just use K3B and have never had a problem with it.
With Brasero I have never managed to burn a good disc! I don't understand why it is the default burner in Ubuntu.

---

### Post by nrundy on 2011-05-24
> **ajgreeny said:**
> You can find the md5sum of any file by running ```
md5sum *filename*
``` in terminal, so for a data CD you would have to do it for the original and the burned file, I presume.

Perhaps there is a utility that can do it in one go, or a script available from somebody already, but I don't know of one.

can I md5sum a folder (hence all the data in the folder)? I'm trying to ensure the integrity of data for backup purposes. obviously, this isn't feasible one file at a time.

---

### Post by ajgreeny on 2011-05-25
I don't see why it would not work for folders.  Try it with a CD-RW if you have one;  you'll soon be able to check.

---

### Post by nrundy on 2011-05-25
> **ajgreeny said:**
> I don't see why it would not work for folders.  Try it with a CD-RW if you have one;  you'll soon be able to check.

Doesn't work. Apparently "directories" can't be md5summed.

This really pisses me off because I made a brainstorm for a verification method and the moderator marked it as an idea already implemented. But there is NO WAY to verify the integrity of a CD burned of backup data using Ubuntu.

---

### Post by ajgreeny on 2011-05-25
In that case make an archive of the folder(s) you want and then you can check that tar or zip or whatever file-type you turn it into.

---

### Post by nrundy on 2011-05-26
> **ajgreeny said:**
> In that case make an archive of the folder(s) you want and then you can check that tar or zip or whatever file-type you turn it into.

Not following you. It won't let me make md5sum of a zipped folder either.

---

### Post by ajgreeny on 2011-05-26
That's odd, because I can md5sum a zip file I have just made to test out the theory.

Are you using archive manager and then trying to md5sum the folder from there?   You must use the command ```
md5sum filename.zip
``` in order for it to work.

---

### Post by nrundy on 2011-05-27
I got it working. 

Not sure cause I was doing the same thing I did last time. Thanks for your help.

Although this doesn't totally solve my problem because I'd like to be able to verify a data folder that is not compressed, it is a workaround that isn't useless. so thanks a lot.

---


---
title: "Bash input/output error"
date: 2010-07-21
forum: General Help
---

### Post by tmetzcc325 on 2010-07-21
Hi all.  I am having a strange problem I've never encountered before.  I have an Asus Eee S101 10.1" netbook with the 32GB SSD.  I installed Ubuntu 10.04 Netbook Edition.

The other day, I was browsing with Firefox, when suddenly the entire computer came screeching to a halt.  Had to power it down with the power button.  After this happened, I have been unable to use the same Firefox profile I had been using.  I had to start Firefox from the command line with the -ProfileManager switch, then create a new profile to keep browsing.

I wanted to completely get rid of the old profile, so from the Profile Manager I tried to delete the old one.  Computer hung, had to reboot with the power switch.  I then tried to browse to the .mozilla/firefox directory and delete the profile's directory there, from both Nautilus and the command line.  Both times, the computer froze.

I tried a few more times, and the couple of times the computer didn't freeze, I got an error from the command line saying a Bash input/output error.  After this error appeared, it would appear no matter what command I ran - I couldn't even run a sudo reboot now.

Can anyone help me with this?  I can create/delete other files and directories, just not that Firefox profile.  I have no idea what else to try.

Thanks,
Tom

---

### Post by rubylaser on 2010-07-21
If you have an external drive or Ubuntu installed on a thumb drive, you could try to boot from the livecd, mount the drive, and delete the profile that way.  It sounds like that part of the SSD may not be working as designed anymore.

Hope that helps.

---

### Post by tmetzcc325 on 2010-07-21
Thanks for the quick reply.  That is actually exactly what I tried to do.  I booted off my thumb drive (which also has UNE Lucid), and the SSD was automatically mounted.  However, whenever I try to access my /home, I get an access denied message.  Is there something special I need to do to access that directory?  I assume this has to do with the fact that I selected to encrypt /home during installation.

I sure hope the SSD isn't failing, because this computer is only about 2 weeks old.  I don't want that hassle yet.

---

### Post by rubylaser on 2010-07-21
Here's a quick link to mount an encrypted home directory.
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html]("http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html")
Hope that helps.

---

### Post by prodigy_ on 2010-07-21
Assuming that you **didn't** install via Wubi, you need to run **fsck** on every Linux partition to ensure file system integrity. Don't forget to unmount partitions first. To check the partition that is normally mounted as root (/) file system, you can use a LiveCD.

---

### Post by tmetzcc325 on 2010-07-21
Thanks for the advice guys.

Using the link provided by rubylaser, I was able to mount the encrypted directory from the thumb drive.  Unfortunately, when I tried to rm -R the ~/.mozilla/firefox directory, I received a bunch of errors that were in the vein of 

"can't remove .mozilla/firefox/phab0908.default/Cache/Trash/0980988796: This is a read-only filesystem"

I don't remember the exact text, and when I tried to copy it into a file, I received the "Bash: Input/output error" When trying to run nano and gedit.

I also just tried to fsck the sda1 partition from the live environment, and this is all I got:

```
ubuntu@ubuntu:~$ sudo !!
sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda1: clean, 170363/1888656 files, 5610955/7548416 blocks
```

I don't know what that means, though.  If there is a problem with the SSD, would it have been reported here?

Thanks,
Tom

---

### Post by prodigy_ on 2010-07-21
"Clean" means that the file system is ok.

What happens when you try to remove your FF profile now? Do you still get the same error?

---

### Post by tmetzcc325 on 2010-07-22
I haven't tried removing the profile folder since running the fsck.  I'll give it a shot tonight when I get home.

I thought the fsck was okay, just wasn't sure if the fact that it said "170363/1888656 files, 5610955/7548416 blocks" meant that it couldn't verify all files/blocks.

---

### Post by tmetzcc325 on 2010-07-26
Well, I finally had some time to try this.  After fsck'ing the SSD, I am still not able to remove the ~/.mozilla directory.  The errors that I am receiving say:

rm: cannot remove `.mozilla/firefox/phab7011.default/Cache.Trash/Trash/Cache/70BADB0Ad01': Read-only file system

It will also say:

rm: cannot remove `.mozilla/firefox/phab7011.default/Cache.Trash/Trash-1': Read-only file system

with a couple Input/Output errors sprinkled in.

I was able to remove other files/directories, just not here.  But now, after trying to run this command, I can no longer read/write/delete any files.

---


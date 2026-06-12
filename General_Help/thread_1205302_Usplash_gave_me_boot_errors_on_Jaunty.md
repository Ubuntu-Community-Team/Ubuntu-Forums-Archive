---
title: "Usplash gave me boot errors on Jaunty"
date: 2009-07-05
forum: General Help
---

### Post by OobNosferatu on 2009-07-05
Everything was going well except that after upgrading from Intrepid 64bit to Jaunty 64bit, splashy wasn't working. It wasn't giving me any splash screen.

So I decided to re-install it. Nothing changed.

I decided to install usplash... and then everything went to heck.

Now I can't boot into my desktop. I am dropped into a login prompt at the console. It gives a few errors but they fly by too fast for me to be able to read them and since I'm a fantastic newbie (that is, excelling at being clueless) I don't know how to look up that particular log.

But the basic problems I'm getting right now are:

1- my filesystem is read only... 
2- my home directory doesn't mount (it's on my second hard drive)

here's my menu.lst from grub:

```

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		6b893350-1222-4a74-8918-634e489e7487
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=6b893350-1222-4a74-8918-634e489e7487 ro vga=792 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		6b893350-1222-4a74-8918-634e489e7487
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=6b893350-1222-4a74-8918-634e489e7487 ro single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		6b893350-1222-4a74-8918-634e489e7487
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6b893350-1222-4a74-8918-634e489e7487 ro vga=792 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		6b893350-1222-4a74-8918-634e489e7487
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=6b893350-1222-4a74-8918-634e489e7487 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
uuid		6b893350-1222-4a74-8918-634e489e7487
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=6b893350-1222-4a74-8918-634e489e7487 ro vga=792 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
uuid		6b893350-1222-4a74-8918-634e489e7487
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=6b893350-1222-4a74-8918-634e489e7487 ro single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, memtest86+
uuid		6b893350-1222-4a74-8918-634e489e7487
kernel		/boot/memtest86+.bin
quiet

```

And here's my /etc/fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6b893350-1222-4a74-8918-634e489e7487 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=43c8540c-78e7-4495-bc88-54c650a45875 /home           ext3    relatime        0       2
# /dev/sda5
UUID=76115ff8-4209-4ab4-bfbe-babdfb3e1919 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I also have a second Jaunty installed on a small partition (that I did to try out a few alsa modifications that required reboots to run my soundcard, hence the liveCD wasn't helpful).

I logged in with it and chrooted to my main ubuntu and tried to uninstall and re-install splashy. It gave me a few errors. I read somewhere to force the install and i did, but it didn't help.

From what I can tell a few others have had a similar problem but none of them resolved the issue (or at least didn't post it here). I really don't want to re-install ubuntu. A possible solution may be to copy the relevant startup files from my working ubuntu to my dysfunctional one, but:

1- I don't know which files would be the relevant ones here
2- I'd like to keep that as a last resort because that may create more problems...

Please help. I've searched this forum and google as well to no avail

---

### Post by OobNosferatu on 2009-07-05
Aha! In an effort to fend off frustration, I have decided on a destructive course: remove splashy and usplash so that I can at least boot up! Therefore I have googled how linux starts up, discovered and deleted splashy and usplash scripts from the init.d folder in etc.

This should have an effect. Not sure if positive or what... but I shall learn. Bring on the pain!

Also, update-initramfs -c -k all would be a good idea now... i think

---

### Post by OobNosferatu on 2009-07-05
Okay that had no effect. 

Any ideas, anyone? How can I undo the damage usplash did to my system?

---

### Post by OobNosferatu on 2009-07-06
Alright, considering the fact that others with the same problem re-installed everything, I'll follow suit.

Here's what I'll do to back up my system:

[http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/linuxhowto/howto-fresh-ubuntu-install-without-losing-your-current-settings/)

I'm lucky I had a separate /home directory and a handy fresh installation of jaunty on the side, in different partitions.

This error blows. I'd like to report this to the people who can fix it... any clues?

---


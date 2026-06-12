---
title: "Unknown filesystem at boot"
date: 2006-03-03
forum: General Help
---

### Post by HakanS on 2006-03-03
Yesterday morning when i started the computer everything was OK. I didn´t do anything with the system, just copied a file to another computer.

In the evening when I booted the computer I got this messages in the boot process:
"Unknown filesystem typ ’ext2’
Unknown filesystem typ ’ntfs’
Unknown filesystem typ ’xfs’"

I have set up fstab like this:
/dev/hda5   reiserfs     /
/dev/hda1   ext2         /boot
/dev/hda6   reiserfs     /home
/dev/hda7   reiserfs     /usr
/dev/hdb1   ntfs         /media/windows
/dev/sda1   xfs           /media/videoedit

I tried to mount hda1, hdb1 and sda1 manualy, but I get the same error message.

What have happened to my system?
How can I fix it?

---

### Post by akiro.yamamoto on 2006-03-03
Post your fstab file.

---

### Post by incubus on 2006-03-03
Seems to me that GRUB is loading your kernel but not the modules. I would take a look at the "menu.lst" in the grub directory. Did you upgrade the kernel recently?

The problem, of course, is that you can't mount that, right? If you have a live distro, that would be very helpful. Or also GRUB allows you to manually edit the boot lines on the fly, if you know what you're doing.

incubus

---

### Post by HakanS on 2006-03-05
This is what's in menu.lst:
```

title		Ubuntu, kernel 2.6.12-10-k7 
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-k7 root=/dev/hda5 ro quiet splash
initrd		/initrd.img-2.6.12-10-k7
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-k7 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-k7 root=/dev/hda5 ro single
initrd		/initrd.img-2.6.12-10-k7
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro quiet splash
initrd		/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hda5 ro single
initrd		/initrd.img-2.6.12-10-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin  
boot

```
Is something wrong there?
I haven't upgraded the kernel in the last weeks.

Here is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda5 / reiserfs notail,noatime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda1 /boot ext2 defaults,noatime,auto,rw,dev,exec,suid,nouser 0 2
/dev/hda6 /usr reiserfs defaults,noatime,auto,rw,dev,exec,suid,nouser 0 3
/dev/hda8 /var reiserfs defaults,noatime,auto,rw,dev,exec,suid,nouser 0 4
/dev/hda9 /home reiserfs defaults,noatime,auto,rw,dev,exec,suid,nouser 0 5
/dev/hdb1 /media/win1 ntfs nls=utf8,umask=022,uid=0,gid=0,auto,ro,nouser 0 0
/dev/hdb2 /media/win2 ntfs nls=utf8,umask=022,uid=0,gid=0,auto,ro,nouser 0 0
/dev/hde1 /media/videoedit xfs defaults,noatime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda7 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0 /media/floppy0 auto ,atime,noauto,rw,dev,exec,suid,user 0 0
```

I realy need help.

---

### Post by incubus on 2006-03-05
HakanS,
Everything seems to be fine in your files. I still think there is something wrong with the modules. You didn't switch cables either, right?

If I read correctly your system has "vmlinuz" and "initrd.img" saved in /dev/hda1. Is it possible to do:
$ sudo apt-get install --reinstall linux-386 linux-k7

This should save the kernel in your /boot directory (which is not mounted). Then probably using a live distro, move these files to your /dev/hda1 (mounting it first, of course).

Also make sure everything is the same version (the files and the entries in the menu.lst).

incubus

PS: Additionally, compare the versions in:
$ dpkg -l |grep linux-image
and
$ uname -a

---

### Post by HakanS on 2006-03-06
The system works again. But I don´t know why!

I booted with the 386 kernel. I then got the /boot (ext2) partition mounted by fstab. But the same error messages for the ntfs and xfs partitions.

I didn´t mention it before, but I also get an error message about dns nameserver (I think it´s the message) and I can´t access the internet.
The same error show up when I booted with the 386 kernel.

On the kubuntu boot screen I saw no OK after "loading modules".

Now to my home made solution:
I edited the menu.lst. Took away the text "quiet splash" and rebooted.
Then everything worked!
Can anyone tell me why?

---

### Post by HakanS on 2006-03-08
Sometime the system works, sometime it don´t.
Today I booted the computer 4 times before it worked.
Any idea what it can be?

I have done:
$ sudo apt-get install --reinstall linux-386 linux-k7

---

### Post by missmoondog on 2006-03-08
hmm? sounds just like a problem i had with a windows xp computer i have. never have figured it out, but that computer now runs ubuntu breezy absolutely perfectly! 

good luck

---

### Post by incubus on 2006-03-09
HakanS,

"Sometimes" is a terrifying word when it comes to computers. It could be a hardware problem, then. Especially because you said you haven't changed anything, right?

Are you sure your hard drive is in good shape? First thing I recommend you to do is backup all your important data.

Then if you don't patience for debugging, you could just reinstall Linux. If you do have patience, we could try:
1. Get a boot working without any "quiet" or "splash" and follow it carefully to see anything strange (like some process taking too long). You can also run "dmesg" to read it again.

2. "fsck" the first partition, which contains the kernel images. When you reinstalled the images (apt-get), make sure they were saved to that partition. You're still trying 386, correct?

Sorry, can't think of anything else right now. But if you can, make sure your hard drive is not failing. That could be the problem.

incubus

---

### Post by HakanS on 2006-03-09
Thanks for all the help i get.
The hard drive is new. But of course it can still be something wrong with it. Is it possible to test it for hardware errors?
I will test "fsck" and "dmesg" tonight when I have finished work.
I am booting with the k7 kernel. Yesterday it worked at the 3:rd reboot.

If I reinstall Kubuntu; Do I have to reinstall the nVidia driver, Canon printer driver and all apt-get:ed programs?

---

### Post by jerrykenny on 2006-03-09
what size is the /boot partition maybe theres no free space in the boot partition  ? next time you can boot try "df"

If your stuck again you can use your kubunt install disk, boot off it, and type    rescue    at the boot prompt . . . .

then try  grub-install hd0

(at least I think thats the reinstall command . . . . . )

---

### Post by HakanS on 2006-03-12
The problem is solved (permanently I hope).
I checked the free space for the /boot partition and it was OK (53% free). But I noticed that the root (/) partition was filled to 100%. I deleted some files so the partition had 88% free space and rebooted. No more errors after that!
Thanks again for all help.

---


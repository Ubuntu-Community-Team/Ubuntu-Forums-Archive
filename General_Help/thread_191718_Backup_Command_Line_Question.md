---
title: "Backup Command Line Question"
date: 2006-06-07
forum: General Help
---

### Post by LsrLine on 2006-06-07
I have a 500GB external USB hard drive. X server won't boot so I want to plug it in and copy all my data onto the ext drive which is FAT32. So:

1) Will Linux recognize the drive even though it won't boot x server, and

2) What command do i need to use to access and copy to the external drive? I'm curious to know even the cd rom drives too

Thanks guys!

---

### Post by Nikusan on 2006-06-07
[QUOTE=LsrLine]I have a 500GB external USB hard drive. X server won't boot so I want to plug it in and copy all my data onto the ext drive which is FAT32. So:

1) Will Linux recognize the drive even though it won't boot x server, and

2) What command do i need to use to access and copy to the external drive? I'm curious to know even the cd rom drives too

Thanks guys![/QUOTE]

Please don't [double post]("http://www.ubuntuforums.org/showthread.php?t=191695").

Have you tried ```
dpkg-reconfigure xserver-xorg
``` To fix the X problem?

---

### Post by scxtt on 2006-06-07
if you're doing a normal boot, but X just fails, it should load the right modules for hotplugging USB devices ...

then they should be accessible via /dev/sda* or they might be mounted to either /mnt or /media ...

after that you should be able to just cp & mv whatever you want to them ...

---

### Post by LsrLine on 2006-06-08
[QUOTE=scxtt]if you're doing a normal boot, but X just fails, it should load the right modules for hotplugging USB devices ...

then they should be accessible via /dev/sda* or they might be mounted to either /mnt or /media ...

after that you should be able to just cp & mv whatever you want to them ...[/QUOTE]

I can't seem to find it.  I've looksed in /media /mnt /dev/sda and i haven't found anything.  Although when i turn the usb hd off and then back on I get: [4296250.736000] sda: assuming drive cache: write through
is there a way that maybe I could search for a file that is on my drive and the path would show up?  how would i do that?

---

### Post by medio on 2006-06-08
You could use the command

mount

to show which drives have been mounted into your filesystem. What is the output of this command?

---

### Post by LsrLine on 2006-06-08
[QUOTE=medio]You could use the command

mount

to show which drives have been mounted into your filesystem. What is the output of this command?[/QUOTE]

/dev/hda1 on / type ext3
proc on / proc
/sys on / sys
varrun on var/run
varlock on var/lock
procbususb on /proc/bus/usb
udev on /dev
devpts on /dev/pts
devshm on /devshm
binfmt_misc on /proc/sys/fs/binfmt_misc

---

### Post by medio on 2006-06-08
1. check that your USB drive is connected and switched on
2. use 

    sudo mount -t vfat /dev/sda1 /mnt

    to mount the first partitition of drive sda (=sda1) to /mnt

---

### Post by scxtt on 2006-06-08
i just checked this out, here's what i did and my results:

1. rebooted into recovery mode and was greeted w/ NO X and a root prompt
2. plugged in a USB flash drive i have, on the command line i saw that my computer recognized it and was initializing it (even told me it was assigned /dev/sdc [my 2 hard drives are sda and sdb])
3. changed to /media and created a tmp directory
[INDENT]cd /media
mkdir tmp[/INDENT]
4. edited my /etc/fstab to mount the device to my new directory:
[INDENT]vi /etc/fstab
added the following line:
/dev/sdc /media/tmp usbfs defaults 0 0
(w/ tabs where the spaces are, like the file was already set up)[/INDENT]
then mounted the filesystem:
[INDENT]mount /media/tmp[/INDENT]
i was then able to use my USB drive like it was a hard drive (i.e. copy and move things to it) ... you should be able to do the same, so i'd boot into recovery mode then plug in your USB device and see if it's detected ...

this is similar to what medio suggested, but i didn't feel like remembering the flags when i looked @ the manpage :p ... i tried to use vfat as the partition type, and it didn't work, i had to use usbfs ...

NOTE: in X, when i plug the LEXAR JUMPDRIVE in, it shows up as /media/LEXAR automagically, w/ no entry in /etc/fstab - pretty cool!

---


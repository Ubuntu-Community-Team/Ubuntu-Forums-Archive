---
title: "Setting up a ramdisk"
date: 2006-05-26
forum: General Help
---

### Post by starkes on 2006-05-26
I'm not sure if this will be helpful but I've been having problems with video playing slow and i have 1.5gb of ram in my cheap thinkpad r51, so i decided to check if i could set up a ramdisk under Breezy, and it worked.

I havent seen anything, anywhere on the forums, wiki, or otherwise showing how to set up a useful ramdisk in ubuntu. The only tutorials i've seen are on old redhat systems using lilo, or grub with a grub.conf file.

My ubuntu doesnt have a grub.conf file, but the menu.lst file that it DOES have is exactly what i needed anyway

basically, if you want to use a ramdisk you need to:

1. Set up your /boot/grub/menu.lst to change the size of ramdisks
2. Make a filesystem on the ramdisk
3. Mount the ramdisk somewhere

_STEP 1. _

Open a terminal and type: 
```
**sudo gedit /boot/grub/menu.lst**
```
Enter your password to be able to edit the file

Find a section that looks something like this:
```

title		Ubuntu Linux
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

```

Add ramdisk_size=500000 to the end of the kernel line, replacing 500000 with whatever size you want your ramdisk to be in KB (this example makes a 500mb drive)

After modification, the line should look like this:

```

kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda5 ro quiet splash **ramdisk_size=500000**

```

You need to reboot in order for the change to the ramdisk size to take place, otherwise you'll end up with a smaller (around 50mb for me initially) ramdisk.
The ramdisk size seems to be passed to the kernel at boot time, and all of /dev/ram* end up being that size.

_STEP 2._

You need to make a filesystem on /dev/ram0 in order to be able to put files on it.

In a terminal, type:
```
**sudo mke2fs /dev/ram0**
```

_STEP 3._

Now, you need to mount the filesystem somewhere.
Again, in a terminal, type:
```
 
[B]cd /media/
sudo mkdir ramdisk
sudo mount /dev/ram0 /media/ramdisk/
sudo chmod -R 777 ramdisk/[/B]

```




Thats it. now you have a ramdisk formatted with ext2!

btw, i used the following 2 sources:
[http://www.linuxfocus.org/English/November1999/article124.html](http://www.linuxfocus.org/English/November1999/article124.html)
[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

---

### Post by stinger30au on 2007-07-19
Ubuntu and Debian auto-mount a ramdisk using tmpfs. This gets mounted to /dev/shm and is usable by anyone (just cd to /dev/shm and start plonking files in there).

the ram disk is dynamic, not static (resizes automatically and will use up to half your available ram)

---


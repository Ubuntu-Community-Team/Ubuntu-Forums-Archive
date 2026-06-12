---
title: "Grub Problems"
date: 2006-03-23
forum: General Help
---

### Post by Bluztrvler on 2006-03-23
This looks to be an age old question because I have found numerous posts about it, but none of the solutions I have found work for me. I am using 5.10.

I had two versions of Windows loaded on my computer when I loaded Ubuntu and grub worked properly until I removed one of them. Then I couldn't boot to anything. I was able to get XP working again by using FixMbr on the windows disk but so far I cannot get Ubuntu to work.

The problem is that I do not seem to be able to edit the menu.lst file. I have tried using rescue on the live cd disk. Gedit doesn't work, get a gedit 19490 GTK-warning Cannot open display error. Sudo nano doesn't work, get error opening terminal :bterm error. If I then type "exit" it takes me to another shell and from there I can open the file using nano or sudo nano, but it says that this is a read only file and I do not have permission to change it.

I have also tried going in by using Knoppix, and I can open the file but cannot find a way to give myself permission to edit it. I used the terminal program as well and accessing it in a word processor program.

If I boot into Ubuntu live cd, I don't seem to be able to acces the drive at all. Is there a way that I can mount my drive and edit it from there.

For what it is worth. I also tried using the Super Grub Disk, and a program called Explore2fs through which I could access my Linux partition inside windows. I tried both the older version and the newer. I could open the file in word pad, but even though the older version said that I might be able to change files, I could not.

What I need to know is, is there another way that I might be able to edit this file? Can I mount the Linux partition using Live cd, and if so, How? Any other suggestions. Is there another way of editing this file using the rescue disk.

---

### Post by Irony on 2006-03-23
Just boot up from the ubuntu live cd, then right click on the desktop and choose Create Folder, then do from terminal;

[PHP]sudo mount /dev/hda? /home/username/Desktop/ubuntu[/PHP]

where ? is the partition number that the installed ubuntu is on.

Then do;

[PHP]sudo gedit /home/username/Desktop/ubuntu/boot/grub/menu.lst[/PHP]

It seems to me that you don't know what your ubuntu partition number is, so first do;

[PHP]sudo fdisk -l[/PHP]

to find out. You will then have to reinstall grub via the install cd by choosing;

[PHP]rescue[/PHP]

at the boot prompt. The pointing grub to the appropriate partition, i.e.;

[PHP]dev/disc/disc0/part?[/PHP]

then at the prompt type;

[PHP]grub-install /dev/hda?[/PHP]

then;
[PHP]
umount /dev/hda?[/PHP]

then type;

[PHP]reboot[/PHP]

I think with unmounting you should type the number of the last partition you booted into rather than the one you are installing to. For example if you last booted into windows on hda1 then type;

[PHP]umount /dev/hda1[/PHP]

If it doesn't work just repeat the process (it only takes a few minutes) but umount a different number.

---

### Post by steve.horsley on 2006-03-23
In knoppix, the disk icons are all read-only. You can rithg-click them and get a menu where you can change the access mode to read-write.

In knoppix, you just use the command **su** in a console. The root password is blank, so just hit enter at the prompt. Now you should be able to use nano.

---

### Post by Bluztrvler on 2006-03-23
Thanks to both of you. 

Your info was very helpful. I was able to edit the menu.lst file using the method described.  f.y. i,  in place of username I had to use ubuntu. 

Everything was great until I got to the grub-install part. I typed:

grub-install /dev/hdb3 (because my Linux installation is on the 3rd partition of my second drive)   and I received the error;

 error reading grub/Stage 1 file or Stage1 file read incorrectly.
I should have written it down, but that is the general idea. 

There is a stage 1 file in my grub directory.

Any ideas?

Thanks a lot for the help

---

### Post by Irony on 2006-03-23
You should point grub to;

[PHP]dev/disc/disc1/part3[/PHP]

I made a mistake in the first part you should do;
[PHP]
grub-install /dev/hda[/PHP]

This installs grub to the MBR, or else if you install it elsewhere you will have to mess with boot flags.

---

### Post by Bluztrvler on 2006-03-23
thanks, I'll give it a try.

---


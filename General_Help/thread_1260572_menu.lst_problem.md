---
title: "menu.lst problem"
date: 2009-09-07
forum: General Help
---

### Post by cartesian on 2009-09-07
I've renamed my menu.lst file by mistake and now I can't boot into any of the items in it.  I am stuck at a grub> prompt.

Can anyone help me boot into recovery mode for instance (its not actually a usable linux partition at the moment) so that I can rename the menu.lst file back to the correct filename.

I really need to stop tinkering with the family PC!!!!

Thanks

---

### Post by drs305 on 2009-09-07
SuperGrub Disk is a very handy CD to have on hand it will help with lots of boot problems.
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

I'm not clear about the "its not actually a usable linux partition at the moment" but if you have Ubuntu installed:

The LiveCD has an option to boot from the first hard disk.

If you can't do that, you can boot from the LiveCD to the Desktop, mount your system partition, find the file and rename it.
From the Desktop: Applications, Accessories, Terminal.
```

sudo mkdir /mnt/temp
sudo mount /dev/sd[COLOR="Red"]XX[/COLOR] /mnt/temp
gksudo nautilus /mnt/temp

```
Find your file and rename it, then reboot.

---

### Post by jobst on 2009-09-07
> **cartesian said:**
> I've renamed my menu.lst file by mistake and now I can't boot into any of the items in it.  I am stuck at a grub> prompt.

Can anyone help me boot into recovery mode for instance (its not actually a usable linux partition at the moment) so that I can rename the menu.lst file back to the correct filename.

I really need to stop tinkering with the family PC!!!!

Thanks

Read:

  [http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=5025](http://forums.scotsnewsletter.com/index.php?act=ST&f=14&t=5025)

jobst

---

### Post by cartesian on 2009-09-09
drs305 - sorry for the delay in replying, I've been trying to sort out a live cd on another pc.

I've booted into the live cd, opeved a Terminal window.  How do I get the XX for the mount /dev/sdXX?

Thanks in anticipation of your help

---

### Post by nothingspecial on 2009-09-09
```
sudo fdisk -l
```

---

### Post by Zoot7 on 2009-09-09
> **cartesian said:**
> I've renamed my menu.lst file by mistake and now I can't boot into any of the items in it.  I am stuck at a grub> prompt.

Can anyone help me boot into recovery mode for instance (its not actually a usable linux partition at the moment) so that I can rename the menu.lst file back to the correct filename.

I really need to stop tinkering with the family PC!!!!

Thanks 
Boot off a LiveCD and manually rename menu.lst ;)

---

### Post by cartesian on 2009-09-09
Yes I can boot off a livecd into root.
I've done the following commands:
mkdir /mnt/temp
mount /dev/sda3 /mnt/temp

When I try and run this command:

gksudo nautilus /mnt/temp

I get the message "command not found"

Supposing I do mount the correct partition can I just then cd to /boot/grub to change the filename back to menu.lst?

Thanks

---

### Post by drs305 on 2009-09-09
> **cartesian said:**
> Supposing I do mount the correct partition can I just then cd to /boot/grub to change the filename back to menu.lst?
Thanks

Yes. All you have to do is get into /boot/grub *of the mounted partition* (if that is where you mis-named the file). The command was just a shortcut. You can find and change the name via command line or open nautilus via "sudo -i" and then nautilus (so you have admin privileges if needed).

---

### Post by cartesian on 2009-09-10
> **drs305 said:**
> Yes. All you have to do is get into /boot/grub (if that is where you mis-named the file).

So, once I've mounted the tmp partition I'm effectively executing commands on the Linux partition on my hard drive?

Can I do a 'find' command from UNIX e.g.

find -name menu.lst **or** find -name menu*

(I'm pretty sure I renamed it to menu.lst.bkp)

to search for the file? I looked quickly last night and could not see it.

Thanks for your help again.

---

### Post by cartesian on 2009-09-10
Excellent. I've managed to rename the file to the correct name.

Thanks to all who've posted and helped me out of a hole!!:)

---

### Post by drs305 on 2009-09-10
Background: Since the questions in post 9 were answered in a PM, I'll summarize it here for anyone who reads the post:

Once you have the system partition mounted (example /mnt/temp), then you should be able to use the find command to locate the file.

Look with nautilus and make sure you are in the /mnt/temp folder. So the menu.lst file should be in /mnt/temp/boot/grub/...

You can use the Places search feature also from the main menu: Places, Search, Look in folder: Other > /mnt/temp

Normal command line entries work but using Nautilus or Places may be more familiar. 

One thing about command line entries - even when you are in /mnt/temp, the environment is still your LiveCD. That means if you tried to install grub, it wouldn't be installing into your real system partition. For that, we would use "chroot". We can explore that if you can't find your old menu.lst file.

---


---
title: "Completely Borked - GDM Can't Write Entry"
date: 2009-11-02
forum: General Help
---

### Post by Dan Again on 2009-11-02
When I attempt to log into Ubuntu (Jaunty) I see the logo with the load bar underneath it, but after that my computer goes to a text-based command line type error message rather than going to the login prompt. The error message says that GDM cannot write an authorization entry because there is not enough disk space.

I am given the option to log in at the command line, but I'm having problems doing anything useful because my keyboard seems to be missing keystrokes when it is in this mode. I can type commands, but I frequently have to type a key twice. When it asks me for my password though I am unable to see what I am typing, so thus far have been unable to successfully enter it.

Furthermore my Windows partition is borked as well due to (I believe) an unrelated issue - I destroyed the boot sector when trying to fix my GRUB. So trying to fix the problem through Windows is not really an option either.

My brother has suggested reinstalling Ubuntu, but before I did anything so drastic I wanted to see if anyone had any suggestions.

Anyone?

---

### Post by SlugSlug on 2009-11-02
boot a live disk and checkout your partition sizes / available space using gparted.

---

### Post by Dan Again on 2009-11-02
I did that...I don't see anything that looks overloaded.

---

### Post by Dan Again on 2009-11-02
Okay...I'm an idiot. Booted to LiveCD again and am looking at GParted now...my boot partition is completely full. Looking [here]("http://ubuntuforums.org/showthread.php?t=1122670") for a fix. When I mount the partition through the LiveCD, though, I don't have permission to do anything, how do I change this? How do I figure out what I need to delete?

---

### Post by SlugSlug on 2009-11-02
gksudo nautilus


will open the browser as root for you to look at stuff, but you'll need to resize the root partition I find 10gig is more than enough, am currently using 4, but I have /home on a diff partition....

---

### Post by P4man on 2009-11-02
> **Dan Again said:**
>  When I mount the partition through the LiveCD, though, I don't have permission to do anything, how do I change this? How do I figure out what I need to delete?

Rather than deleting files, perhaps you want to resize your partition. This guide may help you:
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by Dan Again on 2009-11-02
When I do gksudo nautilus it opens up nautilus for me, but I do not see any of my other partitions.

---

### Post by Dan Again on 2009-11-02
This is a case of a backup gone wrong. Immediately prior to encountering this problem I was messing around with Simple Backup Suite and also moved about 110G of data to an external HDD...I found through my searches that these kinds of operations can often cause problems such as the one that I am having. I guess data is sent to the wrong place. At this point I am certain that I inadvertently filled up my boot partition with files of some sort and just need to delete them. At the moment, though, I cannot figure out how to do this through the LiveCD.

---

### Post by P4man on 2009-11-02
> **Dan Again said:**
> This is a case of a backup gone wrong. Immediately prior to encountering this problem I was messing around with Simple Backup Suite and also moved about 110G of data to an external HDD...I found through my searches that these kinds of operations can often cause problems such as the one that I am having. I guess data is sent to the wrong place. At this point I am certain that I inadvertently filled up my boot partition with files of some sort and just need to delete them. At the moment, though, I cannot figure out how to do this through the LiveCD.

most partitions will mount automatically if you access them from Places > nameofdrive.

If you're using nautilus as root, those mounts may not be visible in the left menu, but you should be able to browse there via /mnt/nameofmount (or /media/nameofmount if its external drive I think)

If that doesnt work, mount them manually
create a mountpoint:

```
sudo mkdir /mnt/namofmountpoint
sudo mount /dev/sda3 /mnt/nameofmountpoint
```

obviously replace sda3 with the correct partition name/number. you can get a list with

```
sudo fdisk -l
```

---

### Post by Dan Again on 2009-11-02
I created a folder on my desktop called mount then through the command line ran sudo mount /dev/sda5 /home/ubuntu/Desktop/mount

This mounted the partition, but I still do not have access to the folder I want (Lost and Found).

When I run sudo nautilus I do not see the mount folder I created on the desktop.

Furthermore, I cannot figure out how to unmount the partition now. How do I do that?

---

### Post by ghostborg on 2009-11-02
Remember to backup your browser book marks. I sometimes overlook this.
Don't forget about the hidden folders in your home directoy-cntrl+h.
I keep my  /home directory on a separate drive so if I need to reinstall-
all my data and settings are intact.Just use the custom option to tell the Ubuntu installer where to put everything and make sure /home does not get formated in the process. If all your data is backed up sometimes its faster to re-install the OS.:(

---

### Post by Dan Again on 2009-11-02
I am in! Figured out how to get complete access to the partition.

Now I just need to figure out what to delete...

Does anyone have any experience with this?

---

### Post by P4man on 2009-11-02
> **Dan Again said:**
> I created a folder on my desktop called mount then through the command line ran sudo mount /dev/sda5 /home/ubuntu/Desktop/mount

This mounted the partition, but I still do not have access to the folder I want (Lost and Found).

When I run sudo nautilus I do not see the mount folder I created on the desktop.

Because you made it on the desktop of the ubuntu user, not the root user? Using a root nautilus you'd have to browse the full path /home/ubuntu/Desktop/mount. 
> 
Furthermore, I cannot figure out how to unmount the partition now. How do I do that?

sudo umount /mnt/nameofmountpoint/

---

### Post by P4man on 2009-11-02
> **Dan Again said:**
> I am in! Figured out how to get complete access to the partition.

Now I just need to figure out what to delete...

Does anyone have any experience with this?

Thats kind of hard for us to guess lol. But go to applications > accessories > disk usage analyser

Have it scan that mount point, it will give you a nice graph whats using all the space.

---

### Post by Dan Again on 2009-11-02
The problem was the messing around I did with Simple Backup Suite.

Once I figured out how to access my boot partition with permissions I navigated to /usr/backup and deleted the two backup folders that were there.

Problem solved! It feel sooooooo good to be back!

---


---
title: "random icons in gnome"
date: 2010-02-04
forum: General Help
---

### Post by coldfusion1313 on 2010-02-04
I have these random cdrom drives in my computer and I cant get rid of them. they dont do anything either is there a way to hide them or something. [IMG]http://farm3.static.flickr.com/2695/4331066951_04ed666da6_o.png[/IMG]

---

### Post by kyphi on 2010-02-04
You cannot get rid of "Filesystem" because that is the filesystem of your Ubuntu installation and you cannot get rid of "CD/DVD Drive" because that is your CD/DVD drive.

The other two, both called "cdrom2" were probably left behind when you removed a CD you had been using without unmounting it first.

Try a reboot.

---

### Post by coldfusion1313 on 2010-02-04
I have rebooted and the 'cdrom2' drives are a read only file system.

---

### Post by kyphi on 2010-02-04
First try placing a CD into your CD/DVD drive and after it spins up, unmount it.

If that does not remove the item, open a terminal (Application, Accessories, Terminal) and type "gksu nautilus" (without the quotation marks).

In the left hand column right click on the cdrom2 icons and choose "mount".

Close nautilus and then the terminal (Ctrl+d).

You should now have a cdrom2 icon on your Desktop.  Right click it and select "unmount" from the drop-down menu.

---

### Post by coldfusion1313 on 2010-02-04
The cdrom2 drives never change, and when you try to mount the one with the icon that looks like a cd going into a drive it says:
```
mount: special device /dev/scd1 does not exist
```And when you try and unmount the one with the plain cd icon,which is already mounted, it says:
```
umount: /media/cdrom2 mount disagrees with the fstab
```

---

### Post by kyphi on 2010-02-04
What happens when you place a CD into the CD/DVD drive?  Does it want to play?  Does it create another icon?

To tackle the message about your fstab, could you copy and paste it please.  Use the command cat /etc/fstab

---

### Post by coldfusion1313 on 2010-02-04
> **kyphi said:**
> What happens when you place a CD into the CD/DVD drive?  Does it want to play?  Does it create another icon?

The 'cdrom2' drives are always there and are never affected by what ever I put in the physical CD/DVD drive, the icons are just there.

When I type in cat /etc/fstab I get:
```
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by kyphi on 2010-02-04
If you only have one CD/DVD Drive, it should register in fstab as /dev/scd0 and not as scd1.

As you can see from my fstab with two CD/DVD Drives the lines should be like this:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

Please check that there is no other scd listed.  If there is none, copy my first line /dev/scd0   /media/cdrom0  ... and replace yours that says /dev/scd1       /media/cdrom2  ...

To do that you will have to use sudo gedit /etc/fstab
Save it before exit.

---

### Post by coldfusion1313 on 2010-02-04
I deleted the line in /etc/fstab:
```
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
```And it made one of the icons go away. Then I tried to ejected the other one, but it said I had to be root, so I did. When I tried to unmount it said:
```
eject: tried to use `/dev/sr1' as device name but it is no block device
eject: unable to find or open device for: `/media/cdrom2'
```

---

### Post by coldfusion1313 on 2010-02-04
I got it both icons are gone, I had to login as root, eject and unmount it. One last questions how do I add things to the 'Places' drop down menu?

---

### Post by kyphi on 2010-02-05
Sorry for the delay - I have been looking through Launchpad where it appears as a listed bug that was supposed to be fixed prior to the final release of Karmic Koala.
see: [https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/441338](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/441338)

At this stage I suggest a complete reboot.

You might also try the Disk Utility under System, Administration.

Although I have Karmic loaded in VirtualBox, several of the utilities that I have come to rely in Hardy Heron have been removed and I am therefore at a disadvantage.

---

### Post by kyphi on 2010-02-05
I was pleased to read of your success.

What did you want to add to the places menu?

---

### Post by kyphi on 2010-02-05
Suppose you want to add a folder called "Sundries" to your Places Menu.

Open your Home folder, create a new folder and name it Sundries.  Open the new Sundries folder and use Ctrl+d or go to the Bookmarks heading and select "Add Bookmark" to add it to your Places Menu.

---

### Post by coldfusion1313 on 2010-02-05
Thanks.
Can you change the ubuntu logo in the menu bar to something esle?

---

### Post by kyphi on 2010-02-06
> Can you change the ubuntu logo in the menu bar to something esle?

Not that I know of.

---


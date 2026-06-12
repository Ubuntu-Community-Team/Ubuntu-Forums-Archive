---
title: "Do windows directories change position?"
date: 2011-01-30
forum: General Help
---

### Post by magodiafano on 2011-01-30
Hi I have a question:
since I have my mp3s on a windows directory (C:\Users\magodiafano\Music) I used to create a link in order to have a direct access to this directory from the ubuntu's desktop.
The problem is that everytime I log into the pc, the link does not work anymore as if the position of the directory was changed.
So I have a lot of problems with the library of rhythmbox too.
What is my error?

---

### Post by hawthornso23 on 2011-01-30
Is this a wubi install or a proper install? 

Sounds to me like your windows partition may not be being mounted automatically. A link to an unmounted partition won't work. If this is the problem then you may want to add your windows partition to /etc/.fstab to get it to mount automatically at boot. Search for "how to fstab ubuntu" in google.

---

### Post by drewsus on 2011-01-30
hawthornso23 is mostly correct, but he pointed to the incorrect file and the command to edit it is:
```
gksu gedit /etc/fstab
```
[SIZE="1"]*(not /etc/.fstab)*[/SIZE]

I will make your life easier by just telling you what to do. You need the UUID of the partition that you have windows on so run this command:
```
sudo blkid
```

Identify that which is your windows partition. For me it was:
```
/dev/sda2: LABEL="WIN7" UUID="01D5FA3C08854FA3" TYPE="ntfs"
```

So my UUID is "01D5FA3C08854FA3".

Open the fstab file by using the first command I provided you with (which is):
```
gksu gedit /etc/fstab
```

Add a line, similar to this, but edited to have your UUID and the mount point target you want (and assuming that your partition is actually formatted to NTFS):
```
UUID=01D5FA3C08854FA3 /media/WIN7 ntfs users,defaults,locale=en_CA.utf8,uid=1000,gid=46,umask=000 0 0
```
[SIZE="1"]*the target I am refuring to is the second field ("/media/WIN7" for my example)*[/SIZE]

Then save fstab, and restart your computer.

---

### Post by hawthornso23 on 2011-01-30
Yeah well . is right next to / on the keyboard - looks like my finger mashed an extra key. The top result on the google search I recommended goes to a page giving extremely detailed comprehensive instructions for how to edit /etc/fstab. The title of that page is "How to fstab". I could have copied the link across, but it was faster just to type the search term.

Yes the title of the page verbs the noun fstab. It isn't my title. Nowhere did I assert that fstab was a command. In fact I didn't give any  instructions. Not being in the habit of reinventing the wheel, I merely pointed at some really detailed existing ones.

I'm annoyed that you construed my post in a way which made it seem like I didn't know what I was talking about. And that is enough of that.

---

### Post by drewsus on 2011-01-30
Sir, I think you took much offense, where there was none. You read the tone on my post very incorrectly, but if I worded it aggressively, I apologise. 

I merely pointed out that there was no period in front of "fstab". Thats it. In fact, if I erased my first sentence, my post would have been *exactly* the same. 

I had *just* done all of this on a new system that is tri-boot (OS X 10.6.6, Windows 7, Ubuntu 10.10) with 2x500 GB, 1x1TB, 1x2TB hard disk drives, with all 3 OSes on one of the 500GBs, the rest being storage and such. I figured I would just help directly, and it was not intended as a slag on you, so forget that.

Furthermore, I completely encourage **magodiafano** to read further on the subject and google is the best place to start. After all, I didn't set mine up by not reading various websites!

Just for fun, here is my fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=053d181a-f905-4a4b-9c54-6a608ae64ed1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=e1257782-f801-4be1-80eb-8ba56d768f0a /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=8b0a9987-5653-4e42-a9c7-fba3ad0174bd none            swap    sw              0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#Added by dRewsus
UUID=7198893753E6D637 				/media/DREW500	ntfs		users,defaults,locale=en_CA.utf8,uid=1000,gid=46,umask=000	0	0
UUID=113155DB0A64530D 				/media/DREW1000	ntfs		users,defaults,locale=en_CA.utf8,uid=1000,gid=46,umask=000	0	0
UUID=2E31CC297EDEA813 				/media/DREW2000	ntfs		users,defaults,locale=en_CA.utf8,uid=1000,gid=46,umask=000	0	0
UUID=01D5FA3C08854FA3 				/media/WIN7	ntfs		users,defaults,locale=en_CA.utf8,uid=1000,gid=46,umask=000	0	0
UUID=f124bf3f-c2dd-3c50-9932-4bfcb2d89f9d 	/media/OSX 	hfsplus		users,defaults,uid=1000,gid=1000,umask=000
```

---

### Post by magodiafano on 2011-02-02
it is not so clear! unlucky I am a newbie in ubuntu... so I installed ubuntu using the complete installation... in fact it has a its own partition.. could you help me now?

---

### Post by drewsus on 2011-02-02
Well, did you read my first post? Do that...

But if you need me to walk you through it, open terminal and run this command:
```
sudo blkid
```

And post the output here please. 

For *example* here is my output of said command:
```
drewsus@drewtopia-home:~$ sudo blkid
[sudo] password for drewsus: 
/dev/sda1: UUID="f124bf3f-c2dd-3c50-9932-4bfcb2d89f9d" LABEL="OSX" TYPE="hfsplus" 
/dev/sda2: LABEL="WIN7" UUID="01D5FA3C08854FA3" TYPE="ntfs" 
/dev/sda5: UUID="053d181a-f905-4a4b-9c54-6a608ae64ed1" TYPE="ext4" 
/dev/sda6: UUID="8b0a9987-5653-4e42-a9c7-fba3ad0174bd" TYPE="swap" 
/dev/sda7: UUID="e1257782-f801-4be1-80eb-8ba56d768f0a" TYPE="ext4" 
/dev/sdb1: LABEL="DREW1000" UUID="113155DB0A64530D" TYPE="ntfs" 
/dev/sdc1: LABEL="DREW500" UUID="7198893753E6D637" TYPE="ntfs" 
/dev/sdd1: LABEL="DREW2000" UUID="2E31CC297EDEA813" TYPE="ntfs" 
/dev/ramzswap0: TYPE="swap" 
drewsus@drewtopia-home:~$
```

---

### Post by magodiafano on 2011-02-03
This is my output

> diego@Administrator:~$ sudo blkid
[sudo] password for diego: 
/dev/sda1: LABEL="RECOVERY" UUID="FEFC38B1FC3865D5" TYPE="ntfs" 
/dev/sda2: UUID="32103AD1103A9C33" TYPE="ntfs" 
/dev/sda3: UUID="FC9C3AAE9C3A62F6" TYPE="ntfs" 
/dev/sda5: UUID="21678ee0-9782-44a2-9a15-86647812896d" TYPE="ext4" 
/dev/sda6: UUID="d22421d7-4a1f-4456-99b3-60a0bf72d09c" TYPE="swap" 
diego@Administrator:~$ 



---

### Post by mendhak on 2011-02-03
It's one of these two:

/dev/sda2: UUID="32103AD1103A9C33" TYPE="ntfs" 
/dev/sda3: UUID="FC9C3AAE9C3A62F6" TYPE="ntfs" 

Presumably, you have a C: and D: in your Windows installation, so the first one *should* be C:

Edit fstab as shown above.  (gksu gedit /etc/fstab)

At the bottom of the fstab file, add this:

UUID=32103AD1103A9C33 /media/WIN7 ntfs users,defaults,locale=en_CA.utf8,uid=1000,gid=46,umask=000 0 0

I've simply copied drewsus' line and replaced the UUID with yours.

Once you do this, in terminal, run

sudo mount -a

And in RhythmBox, point it to /media/WIN7/Users/magodiafano/Music, it should start scanning.

---

### Post by drewsus on 2011-02-03
thanks for finishing it off mendhak :)

---


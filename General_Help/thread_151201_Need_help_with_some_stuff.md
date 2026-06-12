---
title: "Need help with some stuff"
date: 2006-03-27
forum: General Help
---

### Post by Bishop Hill on 2006-03-27
Here's some of the problems I currently have with Kubuntu (if you have an answer to any of them, I would be extremly grateful):

My network. I dunno why, but sometimes the network just shuts down. It's 
compleatlyy random when, but it just shuts down and I have to inactivate and activate it again. Since it's not wireless I'm getting pretty annoyed with this.

Why, and how do I solve this?

The keyboard. The keys are extremly sensitive, and very often I get a long row of letters (eeeeeeeee etc).

Why, and how do I solve this?

Windows. How do I access the windows partition so I can transfer files from Linux to windows and the other way?

My external 250 gb usb FAT 32 harddrive. When I plug it in and run df -h, the terminal says my external is full (when windows says that it has 9 gb's free). I understand that you have to tell Ubuntu which filesystem, but since it automounts I did'nt think that it was needed.

Why, and how do I solve this?

Thank you/Daniel

---

### Post by lupine_nickt on 2006-03-27
The keyboard repeat delay & speed can be set in System Settings->Keyboard. You set delay & rate/sec. My defaults are 660msec and 25.0/s .  YMMV, though. 

For the windows partition, you need to add a line to your /etc/fstab file. It should look "something like":-

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda2            /media/win32       fat32       rw,user              0             0

"fat32" can probably be replaced with auto. 

Not sure about the network & the external; sorry.

xF,

...Nick

---

### Post by incubus on 2006-03-27
Daniel,

What do you mean by having the network shutting down? Does that mean that you can't access anything (like other computers in the network) or just the internet stops working? As you can imagine, the possibilities are endless, we have to narrow down what it could be.

Check the output of:
$ ifconfig
$ route
$ ping [www.google.com](www.google.com)
$ ping 66.102.7.99
(if you will, don't post everything -- especially the first two contain private information such as your IP)

Probably eth0 or eth1 is your network card. Do you see it associated to an IP address? Do you have a router for your connection or is it just a modem?

If you get something from the second ping but not from the first, there's probably something wrong with the DNS server. This is easy to solve.

incubus

---

### Post by incubus on 2006-03-27
Is your entire external HDD formated as FAT32? If so, this can be a problem. Microsoft officially limits a FAT32 partition to 32Gb I think. The "linux" implementation (vfat) probably follows it seriously as opposed to windows xp.

I may be wrong about that, but you may need  to reformat that using a different file system. An elegant solution would be to format the partition using ext2/ext3 and install a driver for windows to access it. I do this and never had a single problem (although I rarely use windows).

[http://www.fs-driver.org/]("http://www.fs-driver.org/")

In other words, I can't offer a practical advice here. I suggest you to search the forums for similar problem.

incubus

PS: To see which file system automount used run:
$ mount

If everything is correct, having an fstab entry won't make much difference.

---

### Post by Barrakketh on 2006-03-27
[QUOTE=incubus]I may be wrong about that[/QUOTE]
You are...sorta.  The maximum size of a FAT32 partition is 8 TB.  Obviously, we don't have those because that's a lot of disk space, and no one that needs to store that much data would use such a crappy filesystem.  However, Windows 2000/XP can't create FAT32 filesystems larger than 32GB, even though they can can read/write to it.  Why, I dunno...but here's what Microsoft says:
> You cannot format a volume larger than 32 GB in size using the FAT32 file system in Windows 2000. The Windows 2000 FastFAT driver can mount and support volumes larger than 32 GB that use the FAT32 file system (subject to the other limits), but you cannot create one using the Format tool. This behavior is by design. If you need to create a volume larger than 32 GB, use the NTFS file system instead.

You can read the knowledge base article [here](http://support.microsoft.com/kb/184006/en-us).

[quote=lupine _nickt]/ dev/hda2 /media/win32 **fat32** rw,user 0 0[/quote]
Whoah...that's wrong.  The filesystem type for FAT32 is vfat.  IIRC, the filesystem type for FAT16 is msdos.

---

### Post by lupine_nickt on 2006-03-27
..oops... lol. My memory must be dying on me. I will officially go and hide my head in shame ;)

Well. Actually I'm off to bed, but you know what I mean... 

xF,

...Nick

---

### Post by Bishop Hill on 2006-03-28
God, I love you guys. I hafta go to school now, but I will try everything when I get home:)

---

### Post by Bishop Hill on 2006-03-28
Ok, this is what I get out of lupine_nickt's help:

There is'nt even an keyboard-setting in systems, but when I type "Keyboard" in "run commando" (or whatever the english words for it are) a window namned keyboard. An empty window.

Why?

When I plug in the external HD, a windows with it's contents come up. Then type "sudo nano /etc/fstab" in the terminal, and it says under options: 

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Why?

---

### Post by incubus on 2006-04-12
Did you figure out these things, Bishop?

Tell me if you still need help there.

incubus

---


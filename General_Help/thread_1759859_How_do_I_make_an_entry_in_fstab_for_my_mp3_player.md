---
title: "How do I make an entry in fstab for my mp3 player?"
date: 2011-05-16
forum: General Help
---

### Post by stinkeye on 2011-05-16
How do I make an entry in fstab for my mp3 player if connected but 
won't cause errors if not connected.
If I plug the player in after boot it mounts on **/dev/sdd**, but if
it's plugged in before boot it mounts on **/dev/sda**.
I would like it to always mount on **/dev/sdd**.

Plus if I reboot into my Natty install,from maverick, with the player
 plugged in it won't even boot.

When mp3 player connected **after** boot.
```
glen@MavMusic:~$ sudo blkid
/dev/sda1: LABEL="XP" UUID="F0D4A588D4A55220" TYPE="ntfs" 
/dev/sda2: LABEL="Storage" UUID="E0D8480AD847DE02" TYPE="ntfs" 
/dev/sda5: LABEL="UBUP" UUID="9c04ea8b-889a-4b40-989a-dcb51cba0db7" TYPE="ext3" 
/dev/sdb1: UUID="610db18d-a68f-4d23-aa48-117044d6492d" TYPE="ext4" 
/dev/sdb3: LABEL="GAMES" UUID="40D0591AD059178C" TYPE="ntfs" 
/dev/sdb4: UUID="09092549-56a6-44c6-bdad-4bf4ea4a5e54" TYPE="swap" 
/dev/sdc1: LABEL="Mav-System" UUID="c587d8ad-4f02-4545-aac7-40873bc4f392" TYPE="ext4" 
/dev/sdc3: LABEL="Mav-Home" UUID="7bb1242c-9af5-4a48-ae0d-8f653dc36418" TYPE="ext4" 
/dev/sdc5: UUID="95ccf46f-0825-4466-9632-3d46cfd0b2c5" TYPE="swap" 
[COLOR="Magenta"]/dev/sdd: LABEL="SANSACLIPPM-^B" UUID="5064-06E0" TYPE="vfat"[/COLOR]
```


When mp3 player connected **before** boot.
```
glen@MavMusic:~$ sudo blkid
[COLOR="#ff00ff"]/dev/sda: LABEL="SANSACLIPPM-^B" UUID="5064-06E0" TYPE="vfat"[/COLOR] 
/dev/sdc1: LABEL="XP" UUID="F0D4A588D4A55220" TYPE="ntfs" 
/dev/sdc2: LABEL="Storage" UUID="E0D8480AD847DE02" TYPE="ntfs" 
/dev/sdc5: LABEL="UBUP" UUID="9c04ea8b-889a-4b40-989a-dcb51cba0db7" TYPE="ext3" 
/dev/sdd1: UUID="610db18d-a68f-4d23-aa48-117044d6492d" TYPE="ext4" 
/dev/sdd3: LABEL="GAMES" UUID="40D0591AD059178C" TYPE="ntfs" 
/dev/sdd4: UUID="09092549-56a6-44c6-bdad-4bf4ea4a5e54" TYPE="swap" 
/dev/sde1: LABEL="Mav-System" UUID="c587d8ad-4f02-4545-aac7-40873bc4f392" TYPE="ext4" 
/dev/sde3: LABEL="Mav-Home" UUID="7bb1242c-9af5-4a48-ae0d-8f653dc36418" TYPE="ext4" 
/dev/sde5: UUID="95ccf46f-0825-4466-9632-3d46cfd0b2c5" TYPE="swap"
```


Current fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=c587d8ad-4f02-4545-aac7-40873bc4f392 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc3 during installation
UUID=7bb1242c-9af5-4a48-ae0d-8f653dc36418 /home           ext4    defaults        0       2
# swap was on /dev/sdc5 during installation
UUID=95ccf46f-0825-4466-9632-3d46cfd0b2c5 none            swap    sw              0       0
#UUID=9c04ea8b-889a-4b40-989a-dcb51cba0db7 /media/UBUP  ext3  errors=remount-ro,users,user  0  0
#UUID=9c04ea8b-889a-4b40-989a-dcb51cba0db7 /media/UBUP ext3 defaults 0 0
/dev/disk/by-uuid/9c04ea8b-889a-4b40-989a-dcb51cba0db7 /media/UBUP ext3 defaults 0 0
```

---

### Post by aeiah on 2011-05-16
you should be able to add it like any other device in your fstab. as you can see, nowadays fstab mounts from a uuid rather than a /dev/ name, and the uuid for your mp3 player will always be the same (5064-06E0)

this won't solve your natty issue though. is this just that you have your bios set to boot from usb first?


by the way, your last entry in your fstab looks a little odd. it probably still works, but it instead of: ```

/dev/disk/by-uuid/9c04ea8b-889a-4b40-989a-dcb51cba0db7 /media/UBUP ext3 defaults 0 0
```
it should probably be:
```
UUID=9c04ea8b-889a-4b40-989a-dcb51cba0db7 /media/UBUP ext3 defaults 0 0
```

your entry for your mp3 player will be something similar but of course, remember to follow an fstab example for a FAT filesystem.

---

### Post by stinkeye on 2011-05-16
I'm unsure as what code to use though.
Do I use 
**UUID=5064-06E0 /media/SansaClipp blah blah blah**
or
**UUID=5064-06E0 /dev/sdd blah blah blah**

and what do I use for *blah blah blah* so that if it's not connected
it won't give boot errors?

---

### Post by aeiah on 2011-05-16
you'd use:```

UUID=5064-06E0 /media/SansaClipp blah blah blah
```

the syntax is: <device> <mountpoint> <option flags>

where <device> is either a uuid or a /dev/ location (like /dev/sda). its recommended to use uuid because the uuid will never change. and really, its the only way for you to go anyway.

your 2nd line, **UUID=5064-06E0 /dev/sdd blah blah blah** would try to do <device> <device> <optionflags> which wouldnt work for obvious reasons!

im not sure what'll happen if it isnt plugged in at boot. you shouldnt have any problems with your computer, but when you do go to plug in the mp3 player it may not mount to your mountpoint, it may just mount to wherever the default is.

---

### Post by stinkeye on 2011-05-16
OK, thanks.
I'll give it a whirl and see what happens.

---

### Post by stinkeye on 2011-05-16
Fstab is making my brain bleed. #-o
Is there not a line I can copy and paste in fstab or is it more complicated than that.
Think I'll just leave it as it is and try and remember to unplug the player before rebooting.

---

### Post by Lateralis on 2011-05-16
What are you struggling with?  What is your specific problem? 

Lines in fstab always look like this:
```

<file system> <mount point>   <type>  <options>       <dump>  <pass>

```

If you're unsure what all of these are, then have a read through the good documentation on [this Tuxfiles page]("http://www.tuxfiles.org/linuxhelp/fstab.html").  If you're still confused or perplexed then feel free to ask.

---

### Post by stinkeye on 2011-05-16
> **Lateralis said:**
> What are you struggling with?  What is your specific problem? 

Lines in fstab always look like this:
```

<file system> <mount point>   <type>  <options>       <dump>  <pass>

```

If you're unsure what all of these are, then have a read through the good documentation on [this Tuxfiles page]("http://www.tuxfiles.org/linuxhelp/fstab.html").  If you're still confused or perplexed then feel free to ask.

What I'm struggling with is reading through all the fstab options.
I was hoping someone with a good knowledge of fstab would be able
to supply a copy and paste with the info I have given.
Lazy, maybe, but if that's not possible I'll leave it as it is.
No biggie.

---


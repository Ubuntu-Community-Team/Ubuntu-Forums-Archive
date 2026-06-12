---
title: "Grub Help Wanted"
date: 2006-05-09
forum: General Help
---

### Post by WelterPelter on 2006-05-09
I've been searching this forum for answers, but didn't find exactly what I was looking for. Sorry if this question is repetitive. 

I'm running ubuntu as my main OS on one drive, and I have Win98 on a separate drive. I can use this second drive find from ubuntu, but I want to be able to boot into the Windows drive, since I have some special software on there that I would like to use. I've been doing this for years, but somehow grub got messed up and it's not working.

My ubuntu drive is hda. My windows drive is hdb. So the relevant lines of menu.lst look like this:

title        Microsoft Windows
root        (hd1,0)
savedefault
makeactive
chainloader    +1

When I try to boot into Windows, it shunts me to the grub edit window. 

Anyone know why this isn't working? Have a suggestion about how to fix it?

---

### Post by gotvols on 2006-05-09
I use a program called gag. [http://gag.sourceforge.net/](http://gag.sourceforge.net/) It is a nice way to dual boot with any os.

---

### Post by Jose Catre-Vandis on 2006-05-09
W98 doesn't like booting from a second hard disk if I remember rightly? can you get it to boot up using a boot disk etc?

Worth checking that W98 really is on (hd1,0) in grub speak, hdb,1 in ubuntu speak, I find that ubuntu/linux installs seem to pick up old partition numberings and some numbers get missed out? Other than that it looks OK.

You could always try reinstalling grub, so that it refinds the OS's on board?

Finally, there is Super Grub Disk (search forum/wiki)

---

### Post by WelterPelter on 2006-05-09
[quote=Jose Catre-Vandis]W98 doesn't like booting from a second hard disk if I remember rightly? can you get it to boot up using a boot disk etc?

Worth checking that W98 really is on (hd1,0) in grub speak, hdb,1 in ubuntu speak, I find that ubuntu/linux installs seem to pick up old partition numberings and some numbers get missed out? Other than that it looks OK.

You could always try reinstalling grub, so that it refinds the OS's on board?

Finally, there is Super Grub Disk (search forum/wiki)[/quote] 
Well, it worked in the past. No prob. I just need to get the settings right this time. Your question about the proper partition numbers is intriguing. How do I check this?

Here's my fstab:

```
wp@wp:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,exec 0 2
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /data           ext3    defaults 0 0
/dev/hdb1       /windows        vfat    umask=000 0 0
```

---

### Post by jazzgossen on 2006-05-10
Also, Windows often needs to be on the first drive in order to boot. You can make grub trick Windows into thinking that it's on the first drive by adding the lines

map (hd0) (hd1)
map (hd1) (hd0)

to the WIndows section of menu.lst.

My own Windows section looks like this:

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
savedefault
chainloader (hd1,0)+1

---

### Post by lha on 2006-05-10
[QUOTE=jazzgossen]
My own Windows section looks like this:

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
savedefault
chainloader (hd1,0)+1[/QUOTE]

This should work for you, WelterPelter. Just replace 'chainloader (hd1,0)+1' with 'chainloader +1'. There shouldn't be a (hd1,0) in it. (Maybe XP->98, too. :))

---


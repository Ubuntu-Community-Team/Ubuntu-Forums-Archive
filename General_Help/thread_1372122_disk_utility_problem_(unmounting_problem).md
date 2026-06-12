---
title: "disk utility problem (unmounting problem)"
date: 2010-01-04
forum: General Help
---

### Post by Amgad elsaiegh on 2010-01-04
i am facing a problem with ubuntu 9.10's Disk utility when i try to unmount ntfs partations , a pop-up message appears as the following pic
[IMG]http://i48.tinypic.com/28jxp4y.jpg[/IMG]
one more thing i noticed here is that this partation is called games while if you looked up in the info you will find that it is mounted as /media/music ,all the ntfs partations are like that !!! , i can't unmount any of them :(

---

### Post by amsterdamharu on 2010-01-04
How did you mount them? 
To unmount I usually use Nautilus (right click and unmount).

For automatic mounts or root only mounts you need to put something in /etc/fstab:
UUID=yourid    /media/something    ntfs    nouser,noauto,noexec,rw    0    0

To get the UUID you can run the command:
ls -l /dev/disk/by-uuid

Change nouser to user, noauto to auto (will mount automatically) rw is read write.

---

### Post by Amgad elsaiegh on 2010-01-04
i mounted them by ntfs configuration tool (ntfs- config)
Unmounting form Nautilus failed too :(
i didn't understand the rest of your post but when i tried ls -l /dev/disk/by-uuid it gave me the following results:
[IMG]http://i45.tinypic.com/2sbve3n.jpg[/IMG]
more help please

---

### Post by amsterdamharu on 2010-01-04
Whats in your /etc/fstab ?

You need to be root to change it but normal user can read it:

gedit /etc/fstab

You can change nouser to user to allow the user to mount and unmount the partitions in the fstab file.

---

### Post by rnerwein on 2010-01-04
hi
just a little hint: if you can't find nouser in your fstab - inser user to the options - nouser is the default.
see "man mount"
ciao

---

### Post by Amgad elsaiegh on 2010-01-05
this is a screenshot of the content of fstab , what should i do next ??(i,m still new to ubuntu so i can't solve all stuff by myself)
[IMG]http://i46.tinypic.com/2chxmv4.jpg[/IMG]

---

### Post by amsterdamharu on 2010-01-05
Open a console and run the following commands

```

sudo
cp /etc/fstab /etc/fstab.org
gedit /etc/fstab

```

Either change the line starting with /dev/sda10 to this:
/dev/sda10 /media/Music ntfs-3g user,noauto,noexec,rw 0 0


Or put a # in front of the line and save the file. the # means the line is commented and will not be used so you can mount and unmount it yourself.

---

### Post by Amgad elsaiegh on 2010-01-06
thanks alot amsterdamharu for replying , i applied your instructions & the result was the unmounting of the GAMES drive & now i'm unable to remount it again at all & when i try to mount it the following message appear :

[IMG]http://i49.tinypic.com/n38ynk.jpg[/IMG]

does anybody got more clues ?

---

### Post by Morbius1 on 2010-01-06
Hokey Smokes !!!

Could you please post the output of the following commands please:

Open **Terminal**
Type **sudo blkid -c /dev/null**
Type **cat /etc/fstab**

[COLOR=Blue]And when I say post the output I mean from the Terminal: Select Edit > Select all > Right click > Copy then Paste into the foum.[/COLOR]

From what I'm reading so far you have two linux partitions: sda5 and sda6 ( swap ). Yet your fstab has sda5 mounted twice - as an ntfs partition at /media/Vista and at /. If this is the result of 9.10's Disk utility or ntfs-config I'd stop using it.

---

### Post by amsterdamharu on 2010-01-06
My advice is edit the fstab
```

sudo
gedit /etc/fstab

```

Comment out all the lines that have ntfs in it (put a # sign in front of the line)

Then mount the partitions in nautilus (double click on it). Stay away from the tools that change your fstab. So if the lines are uncommented again you've used a tool that you better not use.

---

### Post by Morbius1 on 2010-01-07
> **amsterdamharu said:**
> My advice is edit the fstab
```

sudo
gedit /etc/fstab

```Comment out all the lines that have ntfs in it (put a # sign in front of the line)

Then mount the partitions in nautilus (double click on it). Stay away from the tools that change your fstab. So if the lines are uncommented again you've used a tool that you better not use.

For what it's worth, I think this is the best solution.

Using utilities to configure things like fstab or smb.conf always seem to result in unintended consequences.

---

### Post by Amgad elsaiegh on 2010-01-07
hey Morbius1
this the result for the 1st command:

[COLOR="Red"]/dev/sda1: UUID="1C5054FC5054DDD8" TYPE="ntfs" 
/dev/sda5: LABEL="Lilo" UUID="289e334a-0867-46bc-b51a-f3749aace9ce" TYPE="ext4" 
/dev/sda6: UUID="bbfbeeca-735a-4834-b278-9626329b854e" TYPE="swap" 
/dev/sda7: UUID="14D84663D846436A" LABEL="Software" TYPE="ntfs" 
/dev/sda8: UUID="00E485FDE485F4E6" LABEL="Learn" TYPE="ntfs" 
/dev/sda9: UUID="BE749EDC749E972D" LABEL="Music" TYPE="ntfs" 
/dev/sda10: UUID="92BCDE0DBCDDEBAB" LABEL="Games" TYPE="ntfs" 
/dev/sda11: UUID="C84C08884C08740A" LABEL="Movies" TYPE="ntfs" 
/dev/sda12: UUID="CCF41864F41852D6" LABEL="Islamics" TYPE="ntfs" 
/dev/sda13: UUID="AC4C27D24C27965C" LABEL="Unknown" TYPE="ntfs" 
/dev/sda14: UUID="4D2F137F00DE7085" TYPE="ntfs" [/COLOR]


and this is the result for the 2nd command:
[COLOR="Red"]# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=289e334a-0867-46bc-b51a-f3749aace9ce / ext4 errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=bbfbeeca-735a-4834-b278-9626329b854e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda11 /media/Games ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda9 /media/Learn ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda8 /media/Software ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Vista ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda14 /media/Unknown ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda13 /media/Islamics ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda10 /media/Music ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda12 /media/Movies ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Xp ntfs-3g defaults,locale=en_US.UTF-8 0 0[/COLOR]

hey amsterdamharu
i tried this before but i was unable to automount any of the partations anymore using ntfs-config :(

---

### Post by Morbius1 on 2010-01-07
Sorry for the interruption but you may have misinterpreted amsterdamharu's suggestion:

(1) Don't use any utility to mount or unmount your ntfs partitions.

Place a # in front of the following lines in /etc/fstab:
> [COLOR=Red]/dev/sda11 /media/Games ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda9 /media/Learn ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda8 /media/Software ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda5 /media/Vista ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda14 /media/Unknown ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda13 /media/Islamics ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda10 /media/Music ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda12 /media/Movies ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/Xp ntfs-3g defaults,locale=en_US.UTF-8 0 0[/COLOR](2) Reboot
> amsterdamharu,
Then mount the partitions in nautilus (double click on it).All of your unmounted partitions should show up under "Places" in nautilus. You should be able to select one and it will mount. Select the triangle icon next to the name Nautilus and it will unmount.

---

### Post by Amgad elsaiegh on 2010-01-07
thanks alot Morbius1 ,so far this is fine ,i put the # mark & they were successfuly unmounted but the problem now is that i want them to automount at ubuntu startup ,i tried ntfs-config but it gives me the following error on all the ntfs partations :
[IMG]http://i48.tinypic.com/27zddtx.jpg[/IMG]

---

### Post by Morbius1 on 2010-01-07
I don't know anything about ntfs-config. I don't know anything about psydm. I don't know anything about "9.10's Disk utility". I don't use them. If you want to contunue to use them I'd wait for someone with experience in these utilites.

If you want to mount sda8 at boot I would do the following:

> [COLOR=Red]/dev/sda8: UUID="00E485FDE485F4E6" LABEL="Learn" TYPE="ntfs" [/COLOR](1) Create a mount point.

[B]sudo mkdir /media/Learn

[/B]You may already have that mount point created and the output of that command will tell you that.

(2)Add the following line in /etc/fstab

** /dev/sda8 /media/Learn ntfs defaults,nls=utf8,umask=007,gid=46    0    0**

(3) If you have any other references to /dev/sda8 in fstab put yet another # in front of them.

(4) Just because I don't know what you've done with what partition at the moment I'd reboot

(5) Stop using these other utilities ;)

---

### Post by Amgad elsaiegh on 2010-01-07
Yes man :D , so far so good ,the command "**/dev/sda8 /media/Learn ntfs defaults,nls=utf8,umask=007,gid=46 0 0**" worked flawlessly ,what if i wanna do all the rest of ntfs partations ? i think i will change the /dev/.......... to the partation i want, but what about these codes **nls=utf8,umask=007,gid=46 0 0** ,will they be changed ,what are they doing , how did knew them ???

i know i am very annoying , but i think UBUNTU should be much more user-friendly than that & should have a stronger graphocal os tweaking software (not terminal commands which are hard/forgetable) ,don't you agree with me?!

---

### Post by Morbius1 on 2010-01-07
**umask=007** User Mask

Each digit represent a type of user. The first digit is owner, the second is group, and the third is everyone else. A 0 allows read / write. A 7 allows nothing. So 007 allows owner and group to read and write to that partition and no one else.

**gid=46** Group Identifier

All users on your box are members of group=46 (plugdev). So together with umask=007 it means that all local users will be able to read and write to that partition.

**0 0 **

The first "0" has to do with "dump" and quite frankly I've never understood it except that's it's best to keep it at "0" ;)

The second "0" tells linux not to perform a filesystem check at boot.

**utf8** has to do with character encoding. I add it out of habit. It works without it so it's probably in the default. I should have left it out so I wouldn't be forced to explain what it means and end up looking like an idiot :)

> but i think UBUNTU should be much more user-friendly than that & should have a stronger graphocal os tweaking software (not terminal commands which are hard/forgetable) ,don't you agree with me?!Well you used 2 or possibly three utilities to do this and it made a mess of things. Actually, had you chosen to do a "manuual partitoning" at install time instead of using the default, the installer would have automatically produced a line in fstab that looks a lot like mine except instead of using /dev/sda8 it would have used [COLOR=black]UUID=00E485FDE485F4E6

*NOTE: All these parameters are for Windows filesystems. They mean nothing to Linux filesystems ( ext3, ext4 ). There's a different set of rules for those.*
[/COLOR]

---

### Post by Amgad elsaiegh on 2010-01-07
thanks alot Morbius1 ,you helped me alot :D
> Well you used 2 or possibly three utilities to do this and it made a mess of things. Actually, had you chosen to do a "manuual partitoning" at install time instead of using the default, the installer would have automatically produced a line in fstab that looks a lot like mine except instead of using /dev/sda8 it would have used UUID=00E485FDE485F4E6
i have never knew about this "manual partioning" thing (and i don't think i saw it before !!!(where is that)) , but i'll try it next time i install ubuntu

---


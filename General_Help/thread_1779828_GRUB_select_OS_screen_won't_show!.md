---
title: "GRUB select OS screen won't show!"
date: 2011-06-11
forum: General Help
---

### Post by Locobox on 2011-06-11
Hi!

I used **StartUp Manager** in Linux to change to "0" the time GRUB shows the "Select OS screen" now I'cant choose which OS I want to boot. 

Since WinXP is selected as the default OS, I can only log into Windows.

I've already tried to press the **UP ARROW** several times when the machine starts up but has no effect and the GRUB selection screen won't show up (This used to work on a desktop PC with GRUB and dual OS's).

I'm on a laptop, is there any way to get to the GRUB select OS screen again?

Thaks for any help in advance.

---

### Post by axatrikx on 2011-06-11
try using the EasyBCD software to change the bootloader menus..

---

### Post by wildmanne39 on 2011-06-11
> **Locobox said:**
> Hi!

I used **StartUp Manager** in Linux to change to "0" the time GRUB shows the "Select OS screen" now I'cant choose which OS I want to boot. 

Since WinXP is selected as the default OS, I can only log into Windows.

I've already tried to press the **UP ARROW** several times when the machine starts up but has no effect and the GRUB selection screen won't show up (This used to work on a desktop PC with GRUB and dual OS's).

I'm on a laptop, is there any way to get to the GRUB select OS screen again?

Thaks for any help in advance.
Hi, you can boot the livecd and follow this guide to reinstall grub, but I know that there is a command to let you change the the 0 back to a new number but I do not know it.
[http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/](http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/)

---

### Post by Locobox on 2011-06-11
@wildmanne39
GRUB is installed on my system but the time to show the OS selection Screen is "0", I dont think I need to reinstall it.
Anyway going to give it a try thanks for the link.

@axatrikx
Thanks for the advice.

---

### Post by drs305 on 2011-06-11
Holding down the SHIFT key during boot should display the Grub 2 menu. If it doesn't, you can try intermittently pressing the ESC key.

---

### Post by Locobox on 2011-06-11
Hi **drs305**, thanks for the tips but...

Holding down the SHIFT key during boot or intermittently press the ESC key did nothing.

Also tried it with a USB Keyboard, just in case, but no success! 

Thanks for the help

---

### Post by drs305 on 2011-06-11
I'm working with the assumption your boot is controlled by GRUB2...

The SHIFT option was the easiest solution - if it would work.

You can edit the Grub2 settings by booting any linux LiveCD. Mount your Ubuntu partition and then edit the grub.cfg file. Find the "set timeout=0" lines and change them to "set timeout=-1" (there should be two). The -1 value will make the menu wait for your input. You don't need (or want) to run update-grub. Just save the file and boot. The menu should display, at which time you can change the settings in /etc/default/grub and change the GRUB_TIMEOUT setting.

Change the **XY** values to your Ubuntu partition (example: sd**a5**
```

sudo mount /dev/sd**XY** /mnt
gksu gedit /mnt/boot/grub/grub.cfg
```

---

### Post by Locobox on 2011-06-11
mmm... well if ESC or SHIFT keys didnt work, I think I'm not using GRUB2.

I'm trying what wildmanne39, axatrikx suggested booting Ubuntu from the CD/pendrive to access Linux and change the setting to 1 second on Startup Manager.

(Dowloading...)

@drs305
Is there any way to do that from winXP?

Many thanks for your quick response.

---

### Post by drs305 on 2011-06-11
There are some configurations where the keystatus check (which is what the SHIFT key invokes) isn't included in the Grub 2 configuration file.

You could download and run the 'boot info script' while running the LiveCD to give us a good view of your boot status. If you can run it, please post the contents of RESULTS.txt. Get the script from the "BIS" link in my signature line. It's really the best way for us to avoid guessing.

If you can't boot a LiveCD, you should be able to access linux files from within Windows. One app is Ext2Read. The grub files are simple text files (/boot/grub/grub.cfg) so you should be able to access and alter it from within Windows once you install a linux format reader.

If it isn't Grub 2, the file you would edit would be /boot/grub/menu.lst, but I would be surprised if you weren't using Grub 2.

---

### Post by Locobox on 2011-06-14
Hi again, drs305

I think I'm using GRUB2
This is the path for it /boot/grub/grub.cfg

I used Ext2Read, I can see the drive where Ubuntu is, but has no access to it (Windows keep saying if I want to format the drive). So I could not access Ubuntu from Windows that way.

I tried other programas and on most I could access the whole Ubuntu partition from Win but could not write, just read. 

I used UNetbooting to load an Ubuntu ISO to a pendrive, and succesfully accesed ubuntu (not my session) and again I can see the grub.cfg but cannot write it.

Any ideas on what to do I'm thinking in backing up and reformat the whole drive but have no time.

Thanks for the help!

---

### Post by drs305 on 2011-06-14
> **Locobox said:**
> I used UNetbooting to load an Ubuntu ISO to a pendrive, and succesfully accesed ubuntu (not my session) and again I can see the grub.cfg but cannot write it.


First, are you mounting the real Ubuntu system partition and then editing the real grub.cfg file?

Second, try opening the file as root. I'll use **sda5** - use the actual Ubuntu partition for your setup:
```
sudo mount /dev/**sda5** /mnt
gksu gedit /mnt/boot/grub/grub.cfg

```
Since those are the same commands given earlier and you might have already tried them, run this command to manually change the file to allow writing:
```

sudo chmod +w /mnt/boot/grub/grub.cfg
```
If you still can't edit it:
```

sudo chmod 777 /mnt/boot/grub/grub.cfg
```

---

### Post by Locobox on 2011-06-14
Thanks for the help drs305.

I tried the commands you suggested but no luck, Terminal keeps telling me -no such file or directory-

This is what I did:

Used UNetbooting to load Ubuntu to a flash drive, and started Ubuntu from there (Selected the DEFAULT option and waited linux to load) from that session I can see my linux partition but cant edit the grub file.

Most people told me that this can be achieved just by booting linux from a Flash drive or LiveCD and thats it... 
I must be doing something wrong

how do I mount the real Ubuntu system partition (Question)

---

### Post by wildmanne39 on 2011-06-14
> **Locobox said:**
> Thanks for the help drs305.

I tried the commands you suggested but no luck, Terminal keeps telling me -no such file or directory-

This is what I did:

Used UNetbooting to load Ubuntu to a flash drive, and started Ubuntu from there (Selected the DEFAULT option and waited linux to load) from that session I can see my linux partition but cant edit the grub file.

Most people told me that this can be achieved just by booting linux from a Flash drive or LiveCD and thats it... 
I must be doing something wrong

how do I mount the real Ubuntu system partition (Question)
Hi, in post #11 drs305 is telling you how to mount your partitons, if you need more help post back, you just need to enter your actual partition number in the place of his partition number which is sda5 as an example. Look also at his second and third commands that he posted.

---

### Post by Locobox on 2011-06-15
Thanks for your reply wildmanne39, I tried the commands suggested by drs305 on #11 (All of them) from Terminal but nothing happened (No such file or directory or no message at all)

---

### Post by drs305 on 2011-06-15
If you are able to boot the LiveCD/USB please run the boot info script from [http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net") and post the contents of RESULTS.txt

I don't know why you can't edit the Grub files, if they exist. With the limited information we have it's hard to try to recommend much else until we can get some more details on your boot status. The RESULTS.txt will provide us with that info.

---

### Post by Locobox on 2011-06-15
Sure, I understand.

Thanks for the link, I'll post the TXT for further analisys...

---

### Post by Locobox on 2011-06-16
Hi

Loaded Ubuntu from a Pendrive, selected default, in Ubuntu did all the suggested instructions, here is the TXT that terminal generated.

Thaks for the help.

---

### Post by drs305 on 2011-06-16
RESULTS.txt shows existing partitions but no Linux files within them. The boot info script isn't finding an Ubuntu installation. Grub 2 is installed in the MBR and *looking* for the Ubuntu installation, which it can't find. The results also don't show the Windows boot files, so I'm not sure how it's even booting Windows.

The partition structure appears correct to me but I'm not extremely well-versed in partitions. If you didn't have data on the partitions, reinstalling would probably be the easiest solution. If you had data on them or want to spend more time searching for possible contents, you can use *Test Disk* to poke around a bit.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

---

### Post by Locobox on 2011-06-16
> **drs305 said:**
> RESULTS.txt shows existing partitions but no Linux files within them. The boot info script isn't finding an Ubuntu installation. Grub 2 is installed in the MBR and *looking* for the Ubuntu installation, which it can't find. The results also don't show the Windows boot files, so I'm not sure how it's even booting Windows.

The partition structure appears correct to me but I'm not extremely well-versed in partitions. If you didn't have data on the partitions, reinstalling would probably be the easiest solution. If you had data on them or want to spend more time searching for possible contents, you can use *Test Disk* to poke around a bit.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")


Thanks for your help, I tried to understand the TXT generated but seems a bit confusing to me, just in case I'm on an HP Laptop CQ60 with Windows XP and Ubuntu 9 installed on the same 500GBs HDD, everything was fine before I changed the value from 1 to 0 on StartUP Manager in Ubuntu 9.

As I said before, Windows XP was set as default selected OS. I can see the GRUB file both from windows and from Ubuntu but cannot edit it, **someone pointed me out that I needed an Ubuntu 9 rescue disc to enter my Ubuntu 9 original installation/partiton..., booting any IMG from a pendride wont access the origibal ubuntu partition but a new one and thats why I cant edit the GRUB file I see from that session! is that true?**

Ubuntu 9 worked great for me, but given this problem I considered reinstalling it but on that partition where ubuntu is installed there is more than a year of data, so reinstalling is not  an option, thanks for the link, I think I need to read more on this (and how permissions are asigned in linux systems).

Again thanks for your help, learned a lot from this, hope it gets fixed soon!

---

### Post by drs305 on 2011-06-16
You might try burning Rescatux - the linux version of Super Grub Disk. It attempts to repair Grub but can also fix some disk errors that might be preventing the files from being see or altered.
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by Locobox on 2011-06-17
Thanks drs305![[COLOR=#d40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")

---


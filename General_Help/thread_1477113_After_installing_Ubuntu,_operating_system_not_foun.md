---
title: "After installing Ubuntu, operating system not found"
date: 2010-05-08
forum: General Help
---

### Post by jesseduarte on 2010-05-08
I just installed Ubuntu on my IBM thinkpad 43, but after restarting the computer after a supposed "Successful installation", it tells me "Operating System Not Found". This is strange, because when i open the "install Ubuntu" thumbnail, it tells me Ubuntu is installed. Can anyone help me get Ubuntu running?

---

### Post by dino99 on 2010-05-08
open a console: ctrl+alt+F2

then: sudo grub-mkconfig && update-grub

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by jesseduarte on 2010-05-08
thanks for the reply.
Running the first command gives me
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

---

### Post by dino99 on 2010-05-08
> **jesseduarte said:**
> thanks for the reply.
Running the first command gives me
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

i suppose you have not marked / to be bootable when you have formated the partition

[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

run again gparted or any formatting prog and "only" make / bootable (dont reformat)

---

### Post by jesseduarte on 2010-05-08
Thanks, I'm installing partedmagic right now, it'll take a while so I'll come back here after I try those steps.

---

### Post by RJARRRPCGP on 2010-05-08
Probably an error from the BIOS, probably because the BIOS can't find a boot loader! 

Please make sure that the BIOS is configured to boot from the HDD!

---

### Post by jesseduarte on 2010-05-08
okay, now i'm really confused. I booted PartedMagic from a USB drive, and when i open "partition editor" there is no "/" partition. The partition which I'm pretty sure i put Ubuntu on (because it's 53 GB with 3.05 used) is "/dev/sda1", and it DOES have the "boot" flag. So it should be bootable, right?

---

### Post by jesseduarte on 2010-05-08
I don't know if this is allowed, but i need help so I'm bumping this thread.

---

### Post by louieb on 2010-05-08
Boot flag? Linux and GRUB don't need the boot flag - don't care if its set or not. 

What kind of install - WUBI (inside widows)? normal in it own partition?  Are you trying to dual boot? 

Also which install CD - The Live - try before you install CD or the alternate CD? 
and which version of Ubuntu are you trying to install?

Did you tell it not to install the GRUB boot loader? 

Might have other questions too , but 1st please follow the   [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")
and put the results.txt file in your next post.

---

### Post by jesseduarte on 2010-05-08
> **louieb said:**
> Boot flag? Linux and GRUB don't need the boot flag - don't care if its set or not. 

What kind of install - WUBI (inside widows)? normal in it own partition?  Are you trying to dual boot? 

Also which install CD - The Live - try before you install CD or the alternate CD? 
and which version of Ubuntu are you trying to install?

Did you tell it not to install the GRUB boot loader? 

Might have other questions too , but 1st please follow the   [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")
and put the results.txt file in your next post.
I burned an iso onto a cd from another computer, and booted from the cd. Then when linux started, i double clicked the "install ubunto 10.4" LTS icon, and it said it worked, but there's no operating system found when i go back to booting from my HDD. It never asked me whether or not to install the GRUB boot loader. I'm trying to install 10.4
RESULTS.txt is attached.

---

### Post by Serpher on 2010-05-08
In gparted, delete your '/' partition, and make a new one and make sure it's bootable. Also do you have any other partitions for any other mountpoints like /boot or /home?

---

### Post by jesseduarte on 2010-05-08
When i use the partition manager in Partedmagic, there IS no "/" partition. I can make one, but how big should it be? And how exactly to i make it bootable in partedmagic? Add the "boot" flag?

---

### Post by jesseduarte on 2010-05-08
bump =/

---

### Post by jesseduarte on 2010-05-08
bump :/

---

### Post by jesseduarte on 2010-05-08
bump >.>

---

### Post by jesseduarte on 2010-05-09
bump. come on, help please.

---

### Post by louieb on 2010-05-09
Good news bad new - both the same -  the results.txt  shows you should have a boot-able Ubuntu installation.  Looks like a normal - guided use the whole disk installation. 

GRUB IPL code is in the MBR of drive sda. 

sda1 is the / (root) partition and uses most of the drive.   Important files such as /etc/fstab and /boot/grub/grub.conf are present and look good too. 

sda5 is your swap partition  (virtual memory/paging file  in windows user terms). 

> "Operating System Not Found".So your not even getting a grub loading message.  

1st thing I would try is boot the install CD and use the[COLOR=Sienna]** boot 1st hard disk **[/COLOR]option.  

May be some odd BIOS setting preventing it from booting straight to  the hdd - might want to check your BIOS setting boot order.

---

### Post by jesseduarte on 2010-05-09
> **louieb said:**
> Good news bad new - both the same -  the results.txt  shows you should have a boot-able Ubuntu installation.  Looks like a normal - guided use the whole disk installation. 

GRUB IPL code is in the MBR of drive sda. 

sda1 is the / (root) partition and uses most of the drive.   Important files such as /etc/fstab and /boot/grub/grub.conf are present and look good too. 

sda5 is your swap partition  (virtual memory/paging file  in windows user terms). 

So your not even getting a grub loading message.  

1st thing I would try is boot the install CD and use the[COLOR=Sienna]** boot 1st hard disk **[/COLOR]option.  

May be some odd BIOS setting preventing it from booting straight to  the hdd - might want to check your BIOS setting boot order.

I've tried putting these three things first on my BIOS:
IDE HDD0(random sequence of letters)
IDE HDD1
IDE HDD2

with all three of them, I  no longer get "OS not found", but a blinking cursor that blinks infinitely and doesn't do anything.
Where is the boot 1st hard disk option?
And will i have to boot it from the cd every single time? Because it takes forever to get to Ubuntu from the cd...

---

### Post by jesseduarte on 2010-05-09
bump

---

### Post by louieb on 2010-05-09
> Where is the boot 1st hard disk option?.
When you boot to the CD its on the 1st menu.  near the bottom.
> 
And will i have to boot it from the cd every single time? Because it takes forever to get to Ubuntu from the cd...

Should not have to. Linux should run just fine on the T series IBM laptop - have a T30 running Ubuntu - use it everyday -works just fine.

---

### Post by jesseduarte on 2010-05-10
> **louieb said:**
> When you boot to the CD its on the 1st menu. near the bottom.
 
 

When i boot the CD, i get an error that immediately takes me to a desktop session. Is there any way i can access the command from the desktop session?

---

### Post by RJARRRPCGP on 2010-05-10
> **jesseduarte said:**
> 

with all three of them, I  no longer get "OS not found", but a blinking cursor that blinks infinitely and doesn't do anything.

That means the BIOS loaded corrupted data! You must wipe the HDD and try again. Sorry. :(

---

### Post by louieb on 2010-05-11
> **jesseduarte said:**
> When i boot the CD, i get an error that immediately takes me to a desktop session. ...

Not good. The CD should not work that way. Sounds like a bad burn or a bad download.  Probably why the hard drive install is not booting. 

1st check the [HowToMD5SUM - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowToMD5SUM")  
make sure you have a good iso download. 

2nd - after burning another CD - on the 1st menu - run the check media for defects option. 

All it takes is few twisted bits in the wrong place to get weird results.

---

### Post by jesseduarte on 2010-05-11
> **louieb said:**
> Not good. The CD should not work that way. Sounds like a bad burn or a bad download.  Probably why the hard drive install is not booting. 

1st check the [HowToMD5SUM - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowToMD5SUM")  
make sure you have a good iso download. 

2nd - after burning another CD - on the 1st menu - run the check media for defects option. 

All it takes is few twisted bits in the wrong place to get weird results.

According to winmd5sum, the hashes are exactly the same :/
But I'll try another CD and get back to you.

---

### Post by louieb on 2010-05-13
Just found out something try this. Seems the 1st menu does not show up by default in Lucid.

> 
As soon as you boot the livecd hit any key when the graphic appears.  Then check cd for defects.

From the release notes.
Boot options hidden by default on Desktop and Netbook LIVECDs
The Ubuntu 10.04 LTS Desktop and Netbook CDs feature a new boot  interface that is non interactive by default.
To configure advanced boot options, press any key at the first boot  screen.
from [http://ubuntuforums.org/showpost.php?p=9281212&postcount=13](http://ubuntuforums.org/showpost.php?p=9281212&postcount=13)

---


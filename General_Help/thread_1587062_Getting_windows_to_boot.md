---
title: "Getting windows to boot"
date: 2010-10-02
forum: General Help
---

### Post by Earl-Grey on 2010-10-02
Hello,

I have been trying to install Ubuntu Netbook remix on my nextbook via a USB drive but haven't had much luck, and decided for the time being that I would like to delete it and go back to using windows. Later I will get a Ubuntu CD and try installing it from that.

I deleted the partition with the currupt instalation of Ubuntu on and rebooted my system. Now instead of getting a choice between booting Ubuntu or Windows, I just get the following error;

error: no such partition
grub rescue>


I would like to boot back into XP, but I don't know if I need a command to type in, or if I need to boot windows with my USB stick :confused:

Any information would be much appreciated.

---

### Post by garvinrick4 on 2010-10-02
Need to put in LIVE USB (your install USB) boot off of it and choose try ubuntu.
Open a terminal:
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR
Reboot into Hard disk. Windows will boot.

---

### Post by Dustin2128 on 2010-10-02
hm, sounds like the partition contained your grub data; e.g. grub doesn't know what OSes you can boot into. I don't have much experience in standalone grub installs, so my recommendation would to either a. install ubuntu from the CD as you planned, thus reinstalling grub or b. wait for someone who *does *know about grub standalone installs to post. Anyway, the data plus your XP install should still be there if the ubuntu partition is all you deleted.

EDIT: since you've got the option to boot into live USB, you might see if 
```
sudo update-grub
``` fixes the problem.

---

### Post by Earl-Grey on 2010-10-02
:KS Thank you very much for the really fast replies.

I managed to get around the problem for now, by reinstalling Ubuntu from my USB stick. Now it gives me 6 options to boot from.

Ubuntu standard
Ubuntu recovery mode
Memory test
Memory test serial console
Windows XP dev/sda1
Windows XP dev/sda3

For now I think I will keep it like this, but as I am not the only one using the computer, I think it is a bit of hassle selecting option 1 for Linux and option 5 for Windows all the time. On my desktop I only have a choice for 2 options and their is a countdown timer so it will always boot in Windows unless I select Linux before the countdown times runs out.

I wanted a similar system for the netbook, but maybe as I am using a different version of Ubuntu I can't have 2 simple options.



Anyway, thank you again for getting back to my message so quickly, one bag of popcorn each for you.

:popcorn::popcorn:

---

### Post by Dustin2128 on 2010-10-02
> **Earl-Grey said:**
> :KS Thank you very much for the really fast replies.

I managed to get around the problem for now, by reinstalling Ubuntu from my USB stick. Now it gives me 6 options to boot from.

Ubuntu standard
Ubuntu recovery mode
Memory test
Memory test serial console
Windows XP dev/sda1
Windows XP dev/sda3

For now I think I will keep it like this, but as I am not the only one using the computer, I think it is a bit of hassle selecting option 1 for Linux and option 5 for Windows all the time. On my desktop I only have a choice for 2 options and their is a countdown timer so it will always boot in Windows unless I select Linux before the countdown times runs out.

I wanted a similar system for the netbook, but maybe as I am using a different version of Ubuntu I can't have 2 simple options.



Anyway, thank you again for getting back to my message so quickly, one bag of popcorn each for you.

:popcorn::popcorn:
you can change the boot default by the way:[http://maohao.wordpress.com/2010/01/18/setting-windows-as-default-boot-entry-ubuntu/](http://maohao.wordpress.com/2010/01/18/setting-windows-as-default-boot-entry-ubuntu/)

---

### Post by wilee-nilee on 2010-10-03
> **Dustin2128 said:**
> you can change the boot default by the way:[http://maohao.wordpress.com/2010/01/18/setting-windows-as-default-boot-entry-ubuntu/](http://maohao.wordpress.com/2010/01/18/setting-windows-as-default-boot-entry-ubuntu/)

I think the OP has grub2.

OP you can modify grub to show what you want. I would make sure I knew which MS boot is the recovery for sure. With my acer netbook when I had XP the recovery was in grub and worked.

Ask for help on editing the grub menu though, if you decided to try this.

The suggestion of installing lilo though would get you just XP back if that's what you wanted or a fixmbr from a XP install disc @ the command line in the repair section.

---

### Post by garvinrick4 on 2010-10-03
> **Earl-Grey said:**
> :KS Thank you very much for the really fast replies.

I managed to get around the problem for now, by reinstalling Ubuntu from my USB stick. Now it gives me 6 options to boot from.

Ubuntu standard
Ubuntu recovery mode
Memory test
Memory test serial console
Windows XP dev/sda1
Windows XP dev/sda3

For now I think I will keep it like this, but as I am not the only one using the computer, I think it is a bit of hassle selecting option 1 for Linux and option 5 for Windows all the time. On my desktop I only have a choice for 2 options and their is a countdown timer so it will always boot in Windows unless I select Linux before the countdown times runs out.

I wanted a similar system for the netbook, but maybe as I am using a different version of Ubuntu I can't have 2 simple options.



Anyway, thank you again for getting back to my message so quickly, one bag of popcorn each for you.

:popcorn::popcorn:Sounds like your desktop is a Wubi install which is not the same. If you want to choose Windows to boot first in partition install, Open a terminal and;
```
sudo apt-get install startupmanager
```It will be in system/admin to startup manager
You can change boot option there.

This link will tell you how to get rid of recovery and mem entries in boot menu.
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by Earl-Grey on 2010-10-03
Well I managed to get Windows to Work but I am still having problems with Ubuntu. 

When I first switch on my computer I get the boot select screen screen;

Ubuntu, with Linux 2.6.32-25-Generic
Ubuntu, with Linux 2.6.32-25-Generic (Recovery mode)
Ubuntu, with Linux 2.6.32-21-Generic
Ubuntu, with Linux 2.6.32-21-Generic (Recovery mode)
Memory test (memtest86+)
Memory test (memtest86+ serial console 115200)
Mocrosoft Windows XP Home Edition (on /dev/sda1)
Windows NT/2000/XP (on /dev/sda3)

If I try to load the second from last option I can load windows XP. The 1st and 3rd options for Ubuntu don't work, I get the following message;

BusyBox v1.13.3 (Ubuntu 1:1/13.3-1ubunty11) built-in shell (ash)
Enter `help` for a list of built-in commands.

(initramfs)_

I am not sure what I am meant to type in here. I think I might have tried to install Ubuntu twice.


If put the USB drive in, I can load the installer screen and through this I can load a temporary version of Ubuntu, but not my main version where I changed the wallpaper e.t.c


Sorry if my explanation isn't very good. Is there a way of deleting everything to do with Ubuntu and starting again from afresh?

---

### Post by wilee-nilee on 2010-10-03
Post 2 tells you how to install lilo, lilo will boot your XP like it is the only OS. 

I am unsure really whether you have installed from a live running XP or booted the thumb and installed this is very important as far as details go. The grub lines are not 2 installs but 2 kernels.

You might consider posting the bootscript in my signature, in code tags as described as well, or for your information.

---

### Post by webtechquery on 2010-10-03
I think its better you install Grub from Ubuntu Live CD. After installation, you would probably be able to get your Windows back, which will be showing in the Grub menu.. hopefully

Check out:
[http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/](http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/)

---

### Post by Earl-Grey on 2010-10-06
I'm still having a few problems with installing Ubuntu and getting it to boot.

Here is a list of some of the things I have tried;

1) Installing Ubuntu from a USB drive. 

2) Installing Ubuntu in Windows XP.

3) Installing Ubuntu from a live CD.


When I try to load Ubuntu once I have installed it, I get this message;

[COLOR=SeaGreen]BusyBox v1.13.3 (Ubuntu 1:1/13.3-1ubunty11) built-in shell (ash)
Enter `help` for a list of built-in commands.

(initramfs)_[/COLOR] 


I can get the live CD and USB drive method to open up Ubuntu (live version) but after installing it and rebooting I get the same boot screen, with the [COLOR=SeaGreen]initramfs[/COLOR] text.

I thought that I was installing it wrong, so I tried installing it a few different ways. I have the option to install it alongside my windows partition or to a separate one. I tried both several times but I still get the same [COLOR=SeaGreen]initramfs[/COLOR] message.

The final thing is, if I delete the Ubuntu partition I can't get into windows and I get a message like `Can't find grub`. I think I will have a go installing it in windows again just in case.

---

### Post by oldfred on 2010-10-06
If you just want windows install the lilo boot loader or run the fixMBR suggested above. 

If you want to see what is wrong with Ubuntu post the boot info script as that will usually tell what is wrong. With grub2 in the MBR and deleting the Ubuntu partition with the rest of grub you cannot boot. You have to either have Ubuntu with grub or a windows style (windows or lilo) boot loader in the MBR.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Earl-Grey on 2010-10-09
I am sorry but I couldn't get it to work with lilo.

Would you know if there is an easy way in Windows to just delete the Ubuntu installation so it just boots to Windows and I have no other OS installed?

---

### Post by Quackers on 2010-10-09
If you have a Windows repair disc or recovery disc boot from that and at the select language screen just click on next. Then from the advanced options (if it has them) select Command Prompt. In Command prompt enter "bootrec.exe /fixmbr" without the quotes, and hit enter. Then enter "bootrec.exe /fixboot" without quotes and hit enter. Then reboot and Windows should boot up.

NOTE the space between bootrec.exe and /fix****

---

### Post by Earl-Grey on 2010-10-09
> **Quackers said:**
> If you have a Windows repair disc or recovery disc boot from that and at the select language screen just click on next. Then from the advanced options (if it has them) select Command Prompt. In Command prompt enter "bootrec.exe /fixmbr" without the quotes, and hit enter. Then enter "bootrec.exe /fixboot" without quotes and hit enter. Then reboot and Windows should boot up.

NOTE the space between bootrec.exe and /fix****

Thank you for the really fast reply :P

Sadly I don't have a Windows repair disc. It is a netbook and it has no CD drive. I think that there might be a recovery partition or something on my main drive, but I don't know how to access it.

Is there some software that would do the same job as putting in a Windows repair disc?

---

### Post by oldfred on 2010-10-09
You can just about do all the repairs from Ubuntu or most of the Linux based repair CDs.

Lilo should give you a windows boot. If not, just a fixMBR will not fix your windows as the boot problem is after the MBR.

Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

You can use nano to edit boot.ini if it is not correct. And you can use testdisk to recover or rebuild the boot sector.

This has instructions on using testdisk to repair the boot sector for windows from Ubuntu or Linux LiveCD. (was for those who had installed grub to the boot sector in error but proceduce is same)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Often chkdsk is required to repair XP. There is no Ubuntu way as the tools will do minor repairs and set the chkdsk flag.

Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Some advanced repair if chkdsk does not work:
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) or it is in the repositories
As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---


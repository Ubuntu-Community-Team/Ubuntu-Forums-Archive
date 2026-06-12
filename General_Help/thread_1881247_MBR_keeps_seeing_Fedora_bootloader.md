---
title: "MBR keeps seeing Fedora bootloader"
date: 2011-11-15
forum: General Help
---

### Post by Bigs11 on 2011-11-15
My machine consists of Windows 7 on one hard drive.
On a second hard drive, I partitioned and installed Ubuntu 11.10, with Grub booting from root on that drive.
I then setup boot menu with Grub Customizer, and then installed Burg to manage the boot menu.
All worked well untill I installed Fedora16 on another partition on that hard drive. I think I set root as bootloader for Fedora.
When I boot the computer, I keep getting Fedora's boot menu, even after re-installing Grub through Ubuntu.
I'm guessing I need to completely clear the MBR, and then re-install Grub through Ubuuntu Live CD.

Can someone tell me exactly how I should do this please?

Thanks in advance.

---

### Post by BillyBoa on 2011-11-15
Here is a good guide on how to do it, but as I know it's better to install first Fedora and then Ubuntu, otherwise you have problems.

[http://www.linuxbsdos.com/2011/05/31/how-to-triple-boot-fedora-15-ubuntu-11-04-and-windows-7/](http://www.linuxbsdos.com/2011/05/31/how-to-triple-boot-fedora-15-ubuntu-11-04-and-windows-7/)

---

### Post by jjex22 on 2011-11-15
multi booting with windows 7, I always find it easiest to install each bootloader to the /root or /boot partition of that os, and install easy bcd in windows 7. you do get daisy chaining, but I like the set up and when you install a new distro, and it flags itself as most important, you just pop back into windows and reset the mbr. When you want to remove the distro, remove the entry, simples.

---

### Post by coffeecat on 2011-11-15
@Bigs11, you said you installed burg for booting Ubuntu but that after installing Fedora you re-installed grub for Ubuntu but you are still getting the Fedora grub menu. Are you wanting to use burg or grub in Ubuntu? Whichever, if you had re-installed Ubuntu's grub correctly, you would not be seeing the Fedora grub menu. so what method did you use to re-install Ubuntu's grub?

Prior to Fedora 16, Fedora used legacy grub and this did not recognise other Linux distros, which meant that if you were running a Windows/Ubuntu/Fedora triple-boot you needed to edit Fedora's menu.lst or re-install Ubuntu's grub2. That was why it was often advised to install Fedora first. But things have changed with Fedora 16. Fedora 16 now uses grub 2 which recognises your Ubuntu and should have set up a triple-booting menu. Which means that it really doesn't matter whether you use Ubuntu's or Fedora's grub to boot with. 

So the question is: do you want to use grub or burg? And to answer your question, you do not need to "completely clear" the mbr. All you have to do is re-install Ubuntu's grub correctly, re-install burg or configure Fedora's grub if need be. Which would you like to do? :)

---

### Post by rng on 2011-11-15
You can download boot_info_script from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and run it as root. The output will be stored in RESULTS.txt in that folder which you can post here. It will clarify all the partitions as well as grub and booting info.

---

### Post by raja.genupula on 2011-11-15
boot into ubuntu and then open the terminal type this

```
sudo dpkg-reconfigure grub-pc
```

then install the grub to ubuntu sda

---

### Post by oldfred on 2011-11-15
I would do raja.genupula's recommendation, but install to the same drive as Ubuntu - sdb so boot loader & system are on same drive. Then reinstall Windows boot loader to sda, again so system & boot loader are on same drive. 
Then in BIOS set to boot sdb, but if you ever have major issues with sdb you could directly boot sda. 

The boot info script will show where everything is installed. With two drives & three systems it is worth running just to know what is where. I run it before & after every install just to be sure I did what I thought I wanted to do. Plus it provides some internal partition layout documentation that would be useful in a major crash.

---

### Post by Bigs11 on 2011-11-15
> **coffeecat said:**
> @Bigs11, you said you installed burg for booting Ubuntu but that after installing Fedora you re-installed grub for Ubuntu but you are still getting the Fedora grub menu. Are you wanting to use burg or grub in Ubuntu? Whichever, if you had re-installed Ubuntu's grub correctly, you would not be seeing the Fedora grub menu. so what method did you use to re-install Ubuntu's grub?

Prior to Fedora 16, Fedora used legacy grub and this did not recognise other Linux distros, which meant that if you were running a Windows/Ubuntu/Fedora triple-boot you needed to edit Fedora's menu.lst or re-install Ubuntu's grub2. That was why it was often advised to install Fedora first. But things have changed with Fedora 16. Fedora 16 now uses grub 2 which recognises your Ubuntu and should have set up a triple-booting menu. Which means that it really doesn't matter whether you use Ubuntu's or Fedora's grub to boot with. 

So the question is: do you want to use grub or burg? And to answer your question, you do not need to "completely clear" the mbr. All you have to do is re-install Ubuntu's grub correctly, re-install burg or configure Fedora's grub if need be. Which would you like to do? :)

Thanks for all the replies.
I definately want to be able to boot with "BURG".
What is the correct way to reinstall Grub from Ubuntu?
 


It looks like Grub is where I want it, and when I just rebooted, I got (I assume) the boot menu from Ubuntu.
What I didn't get, is the Burg menu. Even after I configured Burg, then did a "sudo update-burg" from terminal.
This worked fine before I installed Fedora.
I notice the pasted info above shows Grub2 (v1.99) is installed in the boot sector of sdb2.
Maybe if I boot into Fedora, then reinstall Grub to "sdb", then reboot into Ubuntu and reinstall Grub to"sdb", that might work?

Thanks in advance.

---

### Post by oldfred on 2011-11-15
If you just reinstall grub to the MBR of sdb it will work, but it probably saved the initial install location and on an update will reinstall to sda. You can check with the command below.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by Bigs11 on 2011-11-16
Finally got the Burg boot-menu back.
I used, which I normally do, Grub Customizer.
When it starts, it prompts you to use Burg, which of course you do.
After settings are configured, in the file menu, there's an option to save to MBR. Just pick which MBR you want, and done.

The only problem I have now, which is new, is it doesn't retain the default boot-up partition which I set.
Even setting Windows7 as default boot in Grub Customize, as well as Burg Customize, it keeps defaulting to Ubuntu 11.10 as boot partition.

Any ideas, anyone?
Thanks again in advance.

---

### Post by Bigs11 on 2011-11-20
Just in case anyone is having similar problem with Burg:
The issue I recently had while using Burg (Grub Customize)
was, I couldn't get Windows 7 bootloader to be the default.
The position I selected in Grub (Burg) Customizer for Windows 7 was "2" in "Preferences/Advanced". This defaulted to Ubuntu every time.
The only way to boot this selection as default was to edit "File System/etc/default/burg" in Gedit, and modify  the line:
GRUB_DEFAULT="2"

---


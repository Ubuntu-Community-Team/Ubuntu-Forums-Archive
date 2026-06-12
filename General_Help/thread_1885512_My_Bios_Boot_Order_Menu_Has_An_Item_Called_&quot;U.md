---
title: "My Bios Boot Order Menu Has An Item Called &quot;Ubuntu&quot;"
date: 2011-11-23
forum: General Help
---

### Post by ExpDisease on 2011-11-23
My Bios Boot Order Menu Has An Item Called "Ubuntu" and it seems that whatever I do I can't erase it. Although it isn't causing any problems, how the heck it appeared there ?

---

### Post by mikejonesey on 2011-11-23
cat /boot/grub/grub.cfg

then locate the menu entry with
/buntu

then you can see which script is including it... (is it encapsulated by ### BEGIN /etc/grub.d/30_os-prober ###)

then edit the appropriate script (int /etc/grub.d/) to exclude that entry

then run update-grub2 to generate a new grub.cfg

---

### Post by Mark Phelps on 2011-11-23
> **ExpDisease said:**
> My Bios Boot Order Menu Has An Item Called "Ubuntu" and it seems that whatever I do I can't erase it. Although it isn't causing any problems, how the heck it appeared there ?

Since Ubuntu installs do NOT mess with the BIOS settings in any way, that is a mystery!

How do you know it is the BIOS boot order?

---

### Post by Quackers on 2011-11-23
Doesn't an EFI/bios machine do that when it's set to bios, when Ubuntu is installed? I think so.
There was a thread around here this morning with a screenshot. I'll try to find it.

---

### Post by Quackers on 2011-11-23
I was wrong :-)
It happens when an EFI/bios machine is set to EFI boot, not bios boot.
Here is the thread I was thinking of

[http://ubuntuforums.org/showthread.php?t=1885123](http://ubuntuforums.org/showthread.php?t=1885123)

EDIT ExpDisease - it's your other thread!

---

### Post by mikejonesey on 2011-11-23
i was guessing the op ment grub... not bios, i'm verry interested it it is bios...

---

### Post by ExpDisease on 2011-11-23
Oh my god I'm sorry. I was tyring to install ubuntu for 2 days. I think i was very tired i didin't recognise that is related and I have an screenshot about it.

So I'm posting here the screenshot

[IMG]http://img703.imageshack.us/img703/8454/p2211110000.jpg[/IMG]

I still don't get it. What is that menu ?  Which bootloader is that ? 

Since I couldn't figure out the problem with my computer I returned back to windows 7 but that thing is still out there :)

I tried the windows repair command "bootsect /nt60 ALL" but it didin't delete it. I changed "use uefi support" to disable so I probably won't see that if I see that list again but in bios boot order section it's still there

---

### Post by oldtimer7777 on 2011-11-23
Troll.  Stick with windows.

> **ExpDisease said:**
> Oh my god I'm sorry. I was tyring to install ubuntu for 2 days. I think i was very tired i didin't recognise that is related and I have an screenshot about it.

So I'm posting here the screenshot

[IMG]http://img703.imageshack.us/img703/8454/p2211110000.jpg[/IMG]

I still don't get it. What is that menu ?  Which bootloader is that ? 

Since I couldn't figure out the problem with my computer I returned back to windows 7 but that thing is still out there :)

I tried the windows repair command "bootsect /nt60 ALL" but it didin't delete it. I changed "use uefi support" to disable so I probably won't see that if I see that list again but in bios boot order section it's still there

---

### Post by oldfred on 2011-11-23
post this, I think you are in UEFI mode not BIOS.

If UEFI include this also:
dmesg | grep EFI
find /boot/efi -name "*efi"


Does you system manual discuss UEFI at all? Some do not make it clear and mix up BIOS & UEFI as it should not matter to users who just have Windows installed.

---

### Post by oldtimer7777 on 2011-11-23
Maybe they can afford taking it back to where they purchased this "state of the art" system, and have them explain what they did wrong because they now need Windows support since they are using a Windows system. 

> **oldfred said:**
> post this, I think you are in UEFI mode not BIOS.

If UEFI include this also:
dmesg | grep EFI
find /boot/efi -name "*efi"


Does you system manual discuss UEFI at all? Some do not make it clear and mix up BIOS & UEFI as it should not matter to users who just have Windows installed.

---

### Post by ExpDisease on 2011-11-23
For the record I'm not a troll or something. You don't know how many times I reinstalled and reinstalled ubuntu. I really meaned that for 2 days i tried to install it. I'm writing this problem here because it happened when I tried to install ubuntu. 

That was an old picture before I installed windows and set uefi support to disable. Even though I set uefi support to enable it doesn't matter because windows boot manager boots first. Now I have no problems about booting computer but the ubuntu item in the list still there so I was curious about removing it.

---

### Post by oldtimer7777 on 2011-11-23
You need to completely repartition and wipe your system before installing Windows.

You need the factory installation dvds or cds.

Contact your tech support for that make/model of computer...

I beg your pardon, if you are truly not a troll.  When someone just posts a picture and says something like that, with no background on the Specs, or anything.. it sounds fishy..   I've never seen anything like that before, but then again I don't know what system you are trying to install Ubuntu onto either.

> **ExpDisease said:**
> For the record I'm not a troll or something. You don't know how many times I reinstalled and reinstalled ubuntu. I really meaned that for 2 days i tried to install it. I'm writing this problem here because it happened when I tried to install ubuntu. 

That was an old picture before I installed windows and set uefi support to disable. Even though I set uefi support to enable it doesn't matter because windows boot manager boots first. Now I have no problems about booting computer but the ubuntu item in the list still there so I was curious about removing it.

---

### Post by ExpDisease on 2011-11-23
I'm sorry about that. Like I said my brain is really gone because of that 2 days. The first installation was just fine I switched to gnome3 prepeared everyting shell-extensions, programs etc. 

I have a samsung rv520 notebook. i5 processor, nvidia gt520m graphics, 4gb ram
 
But when I restarted the computer I saw that menu and I was suprised. In my previous topic I tried to do everything to have ubuntu and solve that problem. I did a auto partition install so I think it made it like this. Because ubuntu has created a fat or efi (I can't remember it exactly) for the boot partition.

The weird thing is I tried to install arch linux couple of times and it went well. But arch is like an ocean to me so I tried ubuntu again. There is something wrong with the grub installation but I don't know why. Tried to reinstall and configure grub but it didin't help.

I wanted to go with ubuntu but this notebook is built for windows i think. That sucks..

---

### Post by oldtimer7777 on 2011-11-23
I know, try an older verison of Ubuntu, like Ubuntu 10.10:

[https://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](https://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Make sure to wipe the entire hard drive with the Thumb Drive/Flash Drive stick of Ubuntu you are installing from.  Wipe the whole hard drive before installing it with gparted. Don't do side-by-side or anything like that until you can get Ubuntu to run.  If you know that you -need- windows, then stick with Windows.. and do a Wubi installation of Ubuntu instead for casual use of Ubuntu.

> **ExpDisease said:**
> I'm sorry about that. Like I said my brain is really gone because of that 2 days. The first installation was just fine I switched to gnome3 prepeared everyting shell-extensions, programs etc. 

I have a samsung rv520 notebook. i5 processor, nvidia gt520m graphics, 4gb ram
 
But when I restarted the computer I saw that menu and I was suprised. In my previous topic I tried to do everything to have ubuntu and solve that problem. I did a auto partition install so I think it made it like this. Because ubuntu has created a fat or efi (I can't remember it exactly) for the boot partition.

The weird thing is I tried to install arch linux couple of times and it went well. But arch is like an ocean to me so I tried ubuntu again. There is something wrong with the grub installation but I don't know why. Tried to reinstall and configure grub but it didin't help.

I wanted to go with ubuntu but this notebook is built for windows i think. That sucks..

---

### Post by oldfred on 2011-11-23
If you are in UEFI mode, older versions may not work at all. Grub is still updating its boot loader to work correctly with UEFI. Some systems work better than others.

Do you have an Ubuntu/grub file in the efi partition. That would explain the ubuntu entry in the UEFI menu.

---

### Post by ExpDisease on 2011-11-24
At this point I have only 2 partitions which are ntfs. I installed ubuntu with wubi

---


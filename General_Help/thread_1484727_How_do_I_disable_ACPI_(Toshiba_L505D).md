---
title: "How do I disable ACPI (Toshiba L505D)?"
date: 2010-05-16
forum: General Help
---

### Post by kananesgi on 2010-05-16
I'm a bit confused here. I'm trying to get Ubuntu working on my Toshiba L505D-S5983. I've read the threads reagarding the issues installing linux on this computer, but I'm stuck at stage one. The first step is to temporarily disable ACPI, but I can't seem to figure out how to do this. I've tried searching the threads for help on this, but it seems that everyone automatically knows how to disable it. The only real help I found was in the Community Ubuntu Documentation on BootOptions ([link]("https://help.ubuntu.com/community/BootOptions")). It shows some screenshots of the Ubuntu LiveCD Loader Menu with menus for F1-F6 at the bottom, with F6 being where ACPI is at. Unfortuately, my loader menu does not have these options. It's a very basic text based loader interface and hitting any of the F keys simply causes the menu to flicker. The documentation shows a nice color menu for the loader.
 
I am currently working with Xubuntu 10.04, but I believe it was the same loader as the regular Ubuntu version. I'm working this from a LiveUSB, too. Would that make a difference?

---

### Post by Ozymandias_117 on 2010-05-16
Press esc while it's booting (At the purplish screen when you boot from cd) select your language, press f6 and select acpi=off.

---

### Post by kananesgi on 2010-05-16
> **Ozymandias_117 said:**
> Press esc while it's booting (At the purplish screen when you boot from cd) select your language, press f6 and select acpi=off.
 
There is no purplish screen during boot, and if I press ESC at the loader menu, it exits to a grub command prompt that won't let me do anything. During boot, all I have is a brief BIOS splash screen (pressing ESC does nothing here), a quick blank screen followed by the GRUB boot loader.
 
I'll try just rapidly tapping ESC until something happens.

---

### Post by colinwhipple on 2010-05-16
> **kananesgi said:**
> There is no purplish screen during boot, and if I press ESC at the loader menu, it exits to a grub command prompt that won't let me do anything. During boot, all I have is a brief BIOS splash screen (pressing ESC does nothing here), a quick blank screen followed by the GRUB boot loader.
 
I'll try just rapidly tapping ESC until something happens.

[https://help.ubuntu.com/community/Grub2#Boot%20Display%20Behavior](https://help.ubuntu.com/community/Grub2#Boot%20Display%20Behavior)

The user can interrupt the boot process and display the menu by holding down the SHIFT key until the menu displays.

    * GRUB 2 searches for a depressed SHIFT key signal during boot. If the key is pressed or GRUB 2 cannot determine the status of the key, the menu is displayed.

---

### Post by kananesgi on 2010-05-16
> **Ozymandias_117 said:**
> Press esc while it's booting (At the purplish screen when you boot from cd) select your language, press f6 and select acpi=off.
 
Ok, I guess I was wrong. This did work after a bit of trial and error. Now I've got a new problem with ACPI on the HD installation. I can't seem to figure out how to tell the HD installation to turn off ACPI during boot.
 
Right now, when I boot the computer I get GNU GRUB version 1.98-1ubuntu6 (at the top of the screen) with a menu beneath with all the various OS installs. The OSs are Linux, Linux Recovery, two Memory Tests, and then two Windows 7 (on separate HDs - I'm guessing my recovery partition and main partition). ESC does nothing here. Info at the bottom says to "hit 'e' to edit the commands" or "c' for the command-line."
 
If I hit 'e' I get a box with a bunch of stuff that I have no idea what to do with, and if I hit 'c' I get a grub command prompt. I tried something simple like 'boot acpi=off' but that returns 'error: no loaded kernel.'
 
Any help? How do I boot from the HD installation with ACPI off? Keep in mind I am a total newb with linux. Right now, I've got maybe an hour with linux actually working. I haven't even fully discovered how to navigate the hard drive yet. I would keep working it in Live mode, but I don't like having to disable the ACPI.
 
> [[COLOR=#444444]https://help.ubuntu.com/community/Gr...lay%20Behavior[/COLOR]]("https://help.ubuntu.com/community/Grub2#Boot%20Display%20Behavior")

The user can interrupt the boot process and display the menu by holding down the SHIFT key until the menu displays.

* GRUB 2 searches for a depressed SHIFT key signal during boot. If the key is pressed or GRUB 2 cannot determine the status of the key, the menu is displayed.
 
For some reason, this post didn't show up when I replied above, but I think I got that part figured out.

---

### Post by colinwhipple on 2010-05-16
Hit "e" on the Linux line, and look for "ro" in one of the lines that show up.  Put the "acpi=off" after the "ro".

Colin

---

### Post by kananesgi on 2010-05-16
> **colinwhipple said:**
> Hit "e" on the Linux line, and look for "ro" in one of the lines that show up.  Put the "acpi=off" after the "ro".

Colin

Thanks man. That worked perfectly. Now I've got tofigure out how to fix the kernel. My first attempt didn't work too well. Now I guess I've got to figure out how to compile my own kernel, but that's going to take some doing that I don't have time for right now. Will try again later.

---

### Post by Comodín on 2010-06-09
Hi,

I got a similar laptop (L505D S5592) with the same problem and was wondering if you could indicate me how to compile my own kernel for my laptop.

Thanks in advance.

---

### Post by colinwhipple on 2010-06-09
> **Comodín said:**
> Hi,

I got a similar laptop (L505D S5592) with the same problem and was wondering if you could indicate me how to compile my own kernel for my laptop.

Thanks in advance.

Look here, particularly on Page 8:

[http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d](http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d)

---


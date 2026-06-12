---
title: "GRUB won't load"
date: 2010-11-14
forum: General Help
---

### Post by leviathan8 on 2010-11-14
Hello there.

A friend of mine just installed today Ubuntu 10.04. After a while, he also installed some NVidia graphic display drives, and rebooted his laptop. After restarting his laptop, the Acer splash screen appears, everything seeming to be fine, but the screen just kept showing for 3-4 minutes. Right after that, a black screen appears with a hovering " _ " at the top left corner of monitor. He can't do anything from here. GRUB doesn't show up nor he can input something with the keyboard. I told him to boot up his LiveCD, but nothing happened. He can't even change the options from boot menu (CD or Stick).

Any help is appreciated.
Have a nice day, leviathan8.

---

### Post by coffee412 on 2010-11-14
> **leviathan8 said:**
> Hello there.

A friend of mine just installed today Ubuntu 10.04. After a while, he also installed some NVidia graphic display drives, and rebooted his laptop. After restarting his laptop, the Acer splash screen appears, everything seeming to be fine, but the screen just kept showing for 3-4 minutes. Right after that, a black screen appears with a hovering " _ " at the top left corner of monitor. He can't do anything from here. GRUB doesn't show up nor he can input something with the keyboard. I told him to boot up his LiveCD, but nothing happened. He can't even change the options from boot menu (CD or Stick).

Any help is appreciated.
Have a nice day, leviathan8.

Boot up the system and when you come to the flashing curser hit <alt> <f2> and this should bring you to a login screen. Login as root or user uninstall everything nvidia. 

This will tell you what else you have to remove besides kmod-nvidia
yum whatprovides /etc/init.d/nvidia 

It will list the nvidia driver package - remove it.

Now install the 256 version of nvidia driver. Google for it if you cannot find it. 

That fixed my problem on my fedora setup that had the same problem. The 260 version seems to have a problem as far as Im concerned. 

Would be nice to know what video card you have.

---

### Post by leviathan8 on 2010-11-15
Unfortunately nothing happened after pressing ALT + F2...

---

### Post by Hippytaff on 2010-11-15
Try booting from liveCD and do nomodset
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
Then fix the driver issues as suggested above ^^ :-)

---

### Post by matt_symes on 2010-11-15
Hi

> I told him to boot up his LiveCD, but nothing happened

Is the CDRom set as the first boot device in his BIOS. It will need to be as is sounds like grub is broken and he will need the live CD to fix it. 

In the first instance, get him to check this and try to boot to the live CD again

Kind regards

---

### Post by leviathan8 on 2010-11-15
> **matt_symes said:**
> Hi



Is the CDRom set as the first boot device in his BIOS. It will need to be as is sounds like grub is broken and he will need the live CD to fix it. 

In the first instance, get him to check this and try to boot to the live CD again

Kind regards

Yeah, I told him to change the boot device in BIOS, but apparently nothing happened. Maybe something went wrong, i'll tell him to try harder. ^^

---

### Post by matt_symes on 2010-11-15
Hi

Talk him through how do change the boot order in the BIOS. It sounds like its still trying to boot from the hard drive.

Kind regards

---

### Post by leviathan8 on 2010-11-15
> **matt_symes said:**
> Hi

Talk him through how do change the boot order in the BIOS. It sounds like its still trying to boot from the hard drive.

Kind regards

I also think that's what happened. He is trying right now, and if I know right, the button to access boot device menu is F12. no?

---

### Post by matt_symes on 2010-11-15
Hi 

It depends on the make of his machine. What is the make ?

Read this

EDIT: Changed site. put the wrong one up.

[http://pcsupport.about.com/od/fixtheproblem/a/biosaccess_pc.htm]("http://michaelstevenstech.com/bios_manufacturer.htm")

Kind regards

---

### Post by sunewbie on 2010-11-15
Does the bios screen load. Do you have 2 hard disks? There was a strange problem with one of my friends laptop (HP compaq). Even if he had only one hard disk. The bios showed another option similar to the hard disk (may be due to virus). Just select proper hard disk and check again. If he has two hard disk, which is not common in laptop), just unplug one and reboot. 

nvidia can cause some problems. Search the forums. Remove nvidia driver and check again. 

If somehow you manage to load ubuntu, just reinstall grub2.

Sometimes the shortcut button for bios screen is F2, delete or F8. Generally it depends upon the motherboard. Sometimes the flash screen for bios loading is not visible as it vanishes fast. Try to hit pause key to see if it works.

Install Grub through Live CD [http://ubuntuforums.org/showthread.php?t=1326991](http://ubuntuforums.org/showthread.php?t=1326991)

Is it a dual boot or just Ubuntu 10.04?

---

### Post by coffee412 on 2010-11-15
> **leviathan8 said:**
> Unfortunately nothing happened after pressing ALT + F2...

Oops!

How about <control> <alt> <f2>

This should give you a login and then login and do what I suggested above: Uninstall all the nvidia driver packages, Then install the older one. The current one is probably ver. 260 and the one Im using is 256.

I would bet that is probably your problem. Especially if you can login the alternate way. That would mean the system is up and running but its just a graphics problem.

---

### Post by sunewbie on 2010-11-16
> **coffee412 said:**
> Oops!

How about <control> <alt> <f2>

This should give you a login and then login and do what I suggested above: Uninstall all the nvidia driver packages, Then install the older one. The current one is probably ver. 260 and the one Im using is 256.

I would bet that is probably your problem. Especially if you can login the alternate way. That would mean the system is up and running but its just a graphics problem.

I agree with him.

---

### Post by leviathan8 on 2010-11-18
> **sunewbie said:**
> Does the bios screen load. Do you have 2 hard disks? There was a strange problem with one of my friends laptop (HP compaq). Even if he had only one hard disk. The bios showed another option similar to the hard disk (may be due to virus). Just select proper hard disk and check again. If he has two hard disk, which is not common in laptop), just unplug one and reboot. 

nvidia can cause some problems. Search the forums. Remove nvidia driver and check again. 

If somehow you manage to load ubuntu, just reinstall grub2.

Sometimes the shortcut button for bios screen is F2, delete or F8. Generally it depends upon the motherboard. Sometimes the flash screen for bios loading is not visible as it vanishes fast. Try to hit pause key to see if it works.

Install Grub through Live CD [http://ubuntuforums.org/showthread.php?t=1326991](http://ubuntuforums.org/showthread.php?t=1326991)

Is it a dual boot or just Ubuntu 10.04?

He has dual boot: Windows 7 and Ubuntu, and yes the bios screen does load.

> **coffee412 said:**
> Oops!

How about <control> <alt> <f2>

This should give you a login and then login and do what I suggested above: Uninstall all the nvidia driver packages, Then install the older one. The current one is probably ver. 260 and the one Im using is 256.

I would bet that is probably your problem. Especially if you can login the alternate way. That would mean the system is up and running but its just a graphics problem.

He tried, still nothing.

---

### Post by matt_symes on 2010-11-18
Hi

 > bios screen does load

....and in the BIOS, the CDRom is set as the first bootable device?

....and the LiveCD is inserted into the CDRom when the machine is restarted and it still will not boot into the LiveCD?

When running from the harddrive as the first boot device, does he get the grub dual boot loader screen?

If he can boot into the Live CD but not the hard drive, i would be investigating GRUB. 

Kind regards

---

### Post by leviathan8 on 2010-11-18
> **matt_symes said:**
> Hi

 

....and in the BIOS, the CDRom is set as the first bootable device?

....and the LiveCD is inserted into the CDRom when the machine is restarted and it still will not boot into the LiveCD?

When running from the harddrive as the first boot device, does he get the grub dual boot loader screen?

If he can boot into the Live CD but not the hard drive, i would be investigating GRUB. 

Kind regards

Yes, the CDRom in BIOS is set as first... the liveCD is inserted... the machine is restarted and the GRUB doesn't load from harddrive. I already mentioned he can't do anything even with LiveCD, maybe he's laptop is crappy. :p

---

### Post by matt_symes on 2010-11-18
Hi

Well assuming the LiveCD is valid and it is not booting into the LiveCD even though it's set as the first boot device, then it sounds like a hardware problem.

You could try making a bootable USB pendrive on a different PC and try booting from that on the laptop, but personally i doubt that would work with the symptoms you are describing. However, you never know. That would eliminate a damaged LiveCD and CDRom though and you would be booting over USB and not CDRom. I would try this anyway as it's good to have a bootable USB pendrive drive handy.

I think it might be a trip to the PC repair shop, if you don't know how to eliminate hardware issues.

Kind regards

---


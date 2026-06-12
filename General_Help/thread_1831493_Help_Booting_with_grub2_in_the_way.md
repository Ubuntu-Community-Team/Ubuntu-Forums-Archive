---
title: "Help Booting with grub2 in the way"
date: 2011-08-23
forum: General Help
---

### Post by Cameron64 on 2011-08-23
Tinkered with partitions.
Grub is now messed up.

Unable to boot from live CD in the normal manner of just hitting f9.

Want to boot from live CD.



Dual booting Win7 and Ubuntu 11.04 64bit.

---

### Post by seawolf167 on 2011-08-23
Booting from a LiveCD and booting from GRUB off your hard drive are independent of eachother. If you cannot boot off a cd, ensure that your cd/dvd booting is enabled and has a higher priority than your hard drive in BIOS.

Does F9 normally give you your boot menu during POST?

---

### Post by Cameron64 on 2011-08-23
Yes, normally occurs during post. However it seems that no matter what I press, nothing stops grub rescue from coming up.

Is there any way to get to the boot menu?

---

### Post by seawolf167 on 2011-08-23
Can you set a different boot order in BIOS placing the cd/dvd drive as the first priority device? Is the keyboard working ok? Even if you spam your boot menu key during startup you don't get any menu? Can you enter BIOS at all?

---

### Post by Cameron64 on 2011-08-23
I DID IT!!! Just spammed the hell out of it like my computer depended on it and it brought me to the boot menu.

Am I going to be able to repair grub2 from this live desktop?

---

### Post by seawolf167 on 2011-08-23
If you cannot enter BIOS no matter what you do, you'll want to clear the CMOS to reset the BIOS back to its original configuration. A quick google search gave [this ]("http://pcsupport.about.com/od/fixtheproblem/tp/clearcmos.htm")so you can see pictures of what to do. You should, however, be able to look up your specific motherboard model number from the manufacturer's website and in the manual follow their instructions on how to reset the BIOS on that particular model.

---

### Post by oldfred on 2011-08-23
Just to reinstall grub2's boot loader to the MBR. Any of these should give you general directions:

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Otherwise post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by seawolf167 on 2011-08-23
> **Cameron64 said:**
> I DID IT!!! Just spammed the hell out of it like my computer depended on it and it brought me to the boot menu.

Am I going to be able to repair grub2 from this live desktop?

Glad you got it working :) Next time you edit your post though, please leave your original post so anyone replying to it makes sense (like mine lol). Oldfred has posted all the good links on how to reinstall Grub2.

---


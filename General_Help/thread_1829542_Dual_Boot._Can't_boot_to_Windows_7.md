---
title: "Dual Boot. Can't boot to Windows 7?"
date: 2011-08-20
forum: General Help
---

### Post by kensclark15 on 2011-08-20
I partitioned off a 50GB section of my HD for Ubuntu 11.04. When booting up my screen says "resolution Mismatched" and I can not choose to boot with Windows or Ubuntu. How do I fix this? How do I take Ubuntu off of the boot list so I can uninstall it and make my computer automatically boot from Windows?

---

### Post by Basher101 on 2011-08-20
I guess that something is interfering with your grub. The splashscreen probably has the wrong resolution..so can you boot into ubuntu now or not?

---

### Post by kensclark15 on 2011-08-20
After 1 minute of the problem it goes straight to Ubuntu. If I want to delete Ubuntu AND make it automatically boot with Windows 7, do I just delete the partition?

---

### Post by Basher101 on 2011-08-20
no this wont do. if you just delete the ubuntu partition, the bootloader still remains. then you wont be able to boot anything...you can change the default operating system thats to be booted. By default its ubuntu, you can change it to windows, but then you wont be able to boot into ubuntu again since your grub will keep booting windows and you cant change back to ubuntu.
Do you have windows installation disks and/or recovery disks? If you have, then deleting the ubuntu partition and restoring your MBR with a windwos disk should be enough

---

### Post by kensclark15 on 2011-08-20
I don't have a disk or anything for Windows because I bought it pre installed. Could I change the bootloader to boot windows by editing something through Ubuntu? If not do you think I should format my drive and just use Ubuntu? All I do is watch videos, surf the web, play Minecraft, and program in Java.

---

### Post by oldfred on 2011-08-20
Lets see where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply, Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
New Version 060 has improved formating and requires code tags to make it legible. It is also a .zip file that you have to extract to get the script.

---

### Post by critin on 2011-08-20
[I]<<do you think I should format my drive and just use Ubuntu?>>
You're asking this on an ubuntu forum?  lol  Thats a question only you can answer.
Why don't you try reinstalling ubuntu to the same partition?  If you modified the splash screen to be pretty, I suggest not doing that until after you get it working satisfactorily.

Of course if you truly don't care about windows, install it on the entire disk.  Ubuntu is vastly more interesting to use--imo

critin
[/I]

---

### Post by kensclark15 on 2011-08-20
I fixed it by downloading a boot fixing program. Now I can only go on windows, so I deleted ubuntu. Is there a way when I reinstall it so that at boot I can choose which one to boot with? I heard I need something called grub?

---

### Post by Basher101 on 2011-08-20
Grub gets automatically installed with Ubuntu, unless you make a custom install and change the bootloader device.

---

### Post by kensclark15 on 2011-08-20
Well before, I downloaded the 32bit version. Now I am going to install the 64bit and hopefully it works. If so I'm going to start messing around with Ubuntu and if I like it I might replace Windows with it.

---

### Post by Basher101 on 2011-08-20
you should not replace it with windows right away, as there are still many programs and especially games that only run on windows. You can replace it when you can check this list:

1.I can run all my important programs or similar ones on Ubuntu
2.My game runs fine in wine (or the linux version if there is one)
3.There is nothing i cant do in Ubuntu that i can in windows.

---

### Post by Mark Phelps on 2011-08-21
If it's not too late ... BEFORE you do anything else, do the following:
1) Boot into Win7
2) Use the Backup feature to create and burn a Win7 Repair CD.

NOW, if you have Win7 booting problems in the future (sometimes happens after dual-boot setups), you have a disk to use to do the repairs...

---


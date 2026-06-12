---
title: "Dual boot problem. Windows safe mode"
date: 2010-02-07
forum: General Help
---

### Post by mark.diamond on 2010-02-07
I have a dual boot system, Karmic Koala 9.10/Windows XP SP3. I am trying to boot into Windows safe mode but I cannot find a working solution in what I have read.

I have tried ...
(1) Using the Windows utility called msconfig to choose Safe mode (with various options)
(2) Booted into Windows from the Grub loader and then caught the boot by hitting the F8 key 
(3) Adding a line to menus.lst, after the standard Windows boot, for windows safe mode 
With each of the choices I end up at the standard Windows screen which offers me a choice of modes into which to boot Windows, namely, starting normally, and starting in safe mode with various options. When I choose safe mode (either alone, or with networking, drivers, etc.) the machine restarts and I get back to the Grub loader. The whole process then goes around in circles.

Any suggestions would help a great deal.

By way of background ... The reason for wanting to get to Safe Mode is that Trojan Vundo.KA appears to be hijacking my browser as well as preventing me from finding or removing the infection. AVG 9.0 finds the process infections but cannot remove them. Malwarebytes does not find the infection, Spyware Doctor does not find it. I'm hoping that Safe Mode will enable me to bypass the loading of the Trojan and then use one of the tools I've mentioned to remove it.

---

### Post by thecliff on 2010-02-07
If you can find the location of the trojan, you should be able to browse and remove inside of Ubuntu.  

If you are using grub, try pressing F8 as soon as you select Windows and press Enter/Return to select Safe Mode.

Cheers

---

### Post by mark.diamond on 2010-02-07
Hello Cliff,

As I mentioned, the problem with the F8 idea is that it doesn't work. If I choose Windows from the Grub loader, and then hit F8 I get to the screen where I can choose Windows Safe Mode ... but I'm the system then reboots and I'm returned to the Grub loader for another round of the circle.

And without being able to find the Trojan (requiring Safe Mode) I can't remove it from Ubuntu!

mark.diamond

---

### Post by mrag on 2012-03-10
Has this ever been resolved? I posted a very similar (?) problem at 
[http://ubuntuforums.org/showthread.php?p=11748523#post11748523](http://ubuntuforums.org/showthread.php?p=11748523#post11748523)
but have not gotten any substantive reply. I do not know for sure that I have any malware. Avast Pro, MalwareBytes, MS Security Scan and HouseCall all say NO, but I cannot boot into Safe Mode. Someday I am sure I will want to. 

So far I cannot find anyone that has a CURRENT dual boot XP and 11.10 system that can get into Safe Mode.

---

### Post by Elfy on 2012-03-11
Old thread closed.

---


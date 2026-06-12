---
title: "help startup"
date: 2009-06-29
forum: General Help
---

### Post by netsitter on 2009-06-29
HI Have installed ubuntu  when I boot up the computer I get the choice of starting Windows XP or ubuntu if I choose ubuntu I get this (WINDOWS COULD NOT START BECAUSE THE FOLLOWING FILE IS MISSING OR CORRUPT <WINDOWS ROOT> SYSTEM32.HAL.DLL PLEASE RE-INSTALL A COPY OF THE ABOVE FILE ) this happens when I choose to run ubuntu NOT windows. HELP please

---

### Post by lindsay7 on 2009-06-29
I never had this problem but I found this, see if it helps

[http://www.pchelpforum.com/windows-xp-2000/23020-windows-root-system32-hal-dll-help.html](http://www.pchelpforum.com/windows-xp-2000/23020-windows-root-system32-hal-dll-help.html)

---

### Post by netsitter on 2009-06-29
hi windows XP is not the problem it works as good as it did it is the ubuntu files that are screwed upI downloaded the iso right to cd and burned works good I can run the demo works fine I can install it fine , but when I go to reboot it gives me a choice windows XP or ubuntu if I go for ubuntu and hit enter it gives me the message in the post.

---

### Post by merlinus on 2009-06-29
Did you install ubuntu in its own partition, or run install from windows?

---

### Post by colau on 2009-06-29
> **lindsay7 said:**
> I never had this problem but I found this, see if it helps

[http://www.pchelpforum.com/windows-xp-2000/23020-windows-root-system32-hal-dll-help.html](http://www.pchelpforum.com/windows-xp-2000/23020-windows-root-system32-hal-dll-help.html)
Is the link broken?

---

### Post by netsitter on 2009-06-30
the link is the same error message but is not the answer. ubuntu is on a 250 gig extention by seagate with usb drive works bran new worked when installed. ubuntu is by it self on this drive

---

### Post by lindsay7 on 2009-06-30
The site opens for me, I just tried it from my post. Here is the info on the fix for the windows dll problem.


> Hi the morningview, and welcome to the PCHF!

There are 2 options for this problem...
You will need to insert your Windows CD, and let it start the Windows setup process, and eventually give you an option.
Repair install of windows, new install, or recovery console. Pick Recovery Console.
Once in there, it will ask you which windows install you want to use, it should only give you one option. 1. C:Windows
Push 1, and enter.
It will now ask you for the Administrator password...if you don't have one, just push enter.

Option 1:
type the following (each new line is where you push "enter")
Attrib -H -R -S C:\Boot.ini
DEL C:\Boot.ini
BootCfg /Rebuild
Fixboot

If this doesn't work...Option 2:

Type the following in Recovery Console...(bold is what you type, italicis key press (such as enter)

expand d:\i386\hal.dl_ c:\windows\system32\hal.dll
reboot and retry.

---

### Post by netsitter on 2009-07-01
Windows IT works. I installed ubuntu on to a external portable drive 250gb. When I start computer it gives me a choice of starting Windows XP or starting ubuntu if I choose UBUNTU I get this message, it is in cap so that stands out (WINDOWS COULD NOT START BECAUSE THE FOLLOWING FILE IS MISSING OR CORRUPT <WINDOWS ROOT>SYSTEM32.HAL.DLL  PLEASE RE-INSTALL A COPY OF THE ABOVE FILE ) Now as I said windows works same as ever BUT Ubuntu does not work I get the above message. Please help. Thank you

---


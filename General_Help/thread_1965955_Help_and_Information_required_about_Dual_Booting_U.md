---
title: "Help and Information required about Dual Booting Ubuntu 11.10 and Win 7"
date: 2012-04-26
forum: General Help
---

### Post by ak700 on 2012-04-26
Hello Fellow Users.

First of all I am new to Ubuntu as well as Ubuntu forums. I am very sorry if I have posted this QUESTION in the wrong section.
Also please use "easy" language so I can follow on.

I would like to dual boot Ubuntu 11.10 on my Desktop which already runs Windows 7 32 bit. I know their is an program called Wubi. Perhaps I have already easy used about some years ago when I dual booted Ubuntu 9.10 on the same machine as said above. The  difference was at that time it ran Windows XP. 

After I did so,(ie dual boot - Win XP and Ubuntu 9) I got green lines on somethings. I don't remember on what but on it came while broswing via chrome (In windows; ubuntu ran perfectly). Also during the boot. The technician formatted and installed Windows 7. 

Now I want to try dual booting Windows 7 along Ubuntu 11.10.
I want to know the minimum requirement for the same. Also probably the reason why that "green lines" appeared.

My Config -

-> Intel Core2Duo 2 (2.9 Ghz)
-> 500Gb Sata HDD
-> Nvidia geforce 9900 card
-> realteck audio card

Thanks in advance :D

---

### Post by ak700 on 2012-04-26
Some More Information about the "Green Lines" 

The green lines appeared mostly when there was a HIGH ram usage taking place like using the chrome browser + flash websites. Also came up while alot multitasking was done. Thus I thought it was due to the low memory. But then they also started coming in the bios menu too and also when the intel logo flashed before the Windows logo came. On the other side Ubuntu was perfect and untouched and no sign of "green lines".

I panicked and uninstalled Wubi via the windows add/remove programs option from the control panel. But the green lines showed up.

I showed this thing to the computer technician and he too was puzzled. He suggested me to re installed the OS.

**I really want to try out Ubuntu 11.10 but I fear this taking place again so want to know whether my computer is below the minimum requirements of dual booting OR what ?**

---

### Post by techsupport on 2012-04-26
> **ak700 said:**
> Some More Information about the "Green Lines" 

The green lines appeared mostly when there was a HIGH ram usage taking place like using the chrome browser + flash websites. Also came up while alot multitasking was done. Thus I thought it was due to the low memory. But then they also started coming in the bios menu too and also when the intel logo flashed before the Windows logo came. On the other side Ubuntu was perfect and untouched and no sign of "green lines".

I panicked and uninstalled Wubi via the windows add/remove programs option from the control panel. But the green lines showed up.

I showed this thing to the computer technician and he too was puzzled. He suggested me to re installed the OS.

**I really want to try out Ubuntu 11.10 but I fear this taking place again so want to know whether my computer is below the minimum requirements of dual booting OR what ?**

Did you try dropping to Ubuntu 2D session to see if it could be your video driver?

---

### Post by gordintoronto on 2012-04-26
Your system should run Ubuntu just fine.

WUBI is really intended to let you fool around with Ubuntu, not as a long-term solution. If you can free up some space on your hard drive, then install Ubuntu into it, I think you will have a happier experience.

On my C: drive, I right-clicked and selected Properties.  One of the "Properties" is Tools, and one of the Tools is defragmentation. I ran that, and it only took a few minutes on a brand-new hard drive. Maybe an hour or more on a drive which has been used for a while.

In Windows Control Panel, search for "disk," and one of the items is "Create and format hard disk partitions." I clicked on it, highlighted the C: drive and selected "Action," "All Tasks," "Shrink Volume."

I suggest you try 12.04, which has just been released. If you can do bittorrent downloads in your Windows system, that is the best way to get it.

---

### Post by ak700 on 2012-04-26
Thank You So Much for the Help!

---


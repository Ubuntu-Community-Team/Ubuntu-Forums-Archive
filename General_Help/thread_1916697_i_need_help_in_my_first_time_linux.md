---
title: "i need help in my first time linux"
date: 2012-01-28
forum: General Help
---

### Post by ran0123456789 on 2012-01-28
hi
this is my first time i use linux and i need your help
i installed linux in 2 coputer.
in first copmputer it work properly
but in the other one i have problam
in the first time i was see an empty purple screen and this stick.
in the second time it exit to dos whitout operating system
 
in addition i want to know how i delete linux
and i want to know how i not delete but back widows 7 to default option (about after 3 second)
 
thanks alot!! :)

---

### Post by BC59 on 2012-01-28
First of all go [here]("http://ubuntuforums.org/showthread.php?t=1613132") and follow the instructions. About the second question I'm not sure what you like to do.

---

### Post by Indie Media on 2012-01-28
> **ran0123456789 said:**
> in addition i want to know how i delete linux

Restore MBR ( remove GRUB ) and get rid of the partition it has been installed on.

> **ran0123456789 said:**
> and i want to know how i not delete but back widows 7 to default option (about after 3 second)

Edit GRUB ( see the link above ).

---

### Post by ran0123456789 on 2012-01-28
thank you all. i will try it... i am little confused because it new for me, i will try to write the command
thank!!

---

### Post by BC59 on 2012-01-28
In the link I [posted]("http://ubuntuforums.org/showthread.php?t=1613132"), go to "How to enable kernel options on the livecd (before install)" and try to follow the instructions, it's simple.
If you see it's working, then go to "How to permanently set kernel boot options on an installed OS (not wubi)" to make it permanent.

---

### Post by grahammechanical on 2012-01-28
Please explain the meaning of the word "delete." I want to find out if you have the same understanding as we do for the word "delete."

Do you want the computer to boot into Windows 7 if you do not choose to boot into Ubuntu? At the moment does the computer boot into Ubuntu if you do not choose Windows 7?

If so, then you want to change the boot order in the boot menu.

Regards.

---

### Post by sanscents on 2012-01-28
Maybe your installation disk corrupted on the second one.  You could try another one.

---

### Post by ran0123456789 on 2012-01-29
i am not succed to remove linux
so this is the problam:
in my laptop, ubnuto work perfectly i very satisfied and i will recomed to every one to install linux
 
but...
in my regular computer - Stationary computer - the linux not work. :(
i try 3 times. and this not work!!
after the instalation in the firs time i get purple empty screen , and i restart my computer. Every time later i have the purple screen with all the option, windows7/memory test/ubuntu, if i choose ubuntu it get me out to linuk dos - command.
 
if i choose windows 7 this ok.
 
but this annoying me in this computer so i want to remove everything that connect to linux.. to format, to delete, to remove everything, i sorry that i install it in my regular computer.
i dont know commend in linux, i dont know how to write them and where.
i want only my old windows 7.
 
when i will be clever i will try again to install linux
 
thankk alot!!! i am very appriciate your help!!!:)

---

### Post by dragonfly41 on 2012-01-31
Your laptop is working o.k.?

In your "regular computer" .. boot up the ubuntu Live CD.

Then when ubuntu starts .. open terminal.

Run terminal command:**   sudo fdisk -l **

and copy terminal output from this command to this forum to help diagnose your problem on your "regular computer".

...

You are trying to uninstall ubuntu on your "regular computer"?

---

### Post by ran0123456789 on 2012-02-01
thank you.
 
in my laptop ubuntu run perfectly. I like it,  nevertheless , i prefer  that win 7 will run automaticlly If there will be no choice over 3 seconds.
because still i not get used to linux. i want, but it will take  time.
 
 
in "regular computer" linux doesnt work!! i want to remove it. i want only windows 7 without purple screen
:)

---

### Post by dragonfly41 on 2012-02-01
(a) In laptop .. install **grub customizer** .. and select windows to launch first in menu as default.

(b) In regular computer .. boot up Live CD .. run **sudo fdisk -l** from command terminal  as advised earlier.

---

### Post by dragonfly41 on 2012-02-01
[http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)


[COLOR=DarkRed][EDIT] the above link was posted in reply to a question by another user who entered the thread .. now moved out by moderator.

[http://ubuntuforums.org/showthread.php?t=1918674](http://ubuntuforums.org/showthread.php?t=1918674)[/COLOR]

---

### Post by ran0123456789 on 2012-02-01
this is my screenshot of my regular computer.
 
is it possible to format linux partition, without harm to windows 7 partition??

---

### Post by Gremlinzzz on 2012-02-01
How to Remove Ubuntu From a Dual Boot in Windows 7
[http://www.ehow.com/how_8511577_remove-dual-boot-windows-7.html](http://www.ehow.com/how_8511577_remove-dual-boot-windows-7.html)
You will not be able to access this operating system again without installing a new boot loader.

How to Repair the MBR on Windows 7
Things You'll Need

    Windows 7 installation disc
[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

---

### Post by ran0123456789 on 2012-02-02
From the above link you gave me "If you wish to remove an operating system, such as Ubuntu Linux, from this list, you may do so from within Windows."

The problem is that windows do not even know there is Linux, and as I start my Linux Linux there is no mention of the boot or the Linux partitions




in addition I tried the windows recovery and did not help :( linux contunue to appear in the boot startup with the purple screen/
 
 
thank you so much i really apriciate your help :)

---

### Post by mastablasta on 2012-02-02
> **ran0123456789 said:**
> From the above link you gave me "If you wish to remove an operating system, such as Ubuntu Linux, from this list, you may do so from within Windows."
 
The problem is that windows do not even know there is Linux, and as I start my Linux Linux there is no mention of the boot or the Linux partitions
 

if you go to disk manager in windows you will see there is unfortmatted disk space. you can then delete &  reformat that space (that space are actually ubuntu partitions)
 
> 
in addition I tried the windows recovery and did not help :( linux contunue to appear in the boot startup with the purple screen/
 
thank you so much i really apriciate your help :)
 
after deleting the partitions.... one more thing needs to be done -
 
 
not windows recovery, but windows boot repair. : [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
 
good luck.

---

### Post by ran0123456789 on 2012-02-02
thank you so much!!!!!! i succeed in my regular computer.

for the next time that someone ask for this, I make guide - how to delete ubuntu and repair windows 7:


**step 1 **_(repair your boot)_
1. insert  your widows  7 installation disk
2. repair your computer
3. choose windows 7
4. choose command prompt
5. write this command:    bootrec /fixmbr

in the next time will be only boot from win7

**step 2** _(delete ubuntu - and format ubunu partitions_)
1. start
2. control panel
3. choose computer manager
4 choose disk manager.
5. delete all the empty  partitions
6 format them to NTFS type

you finish.
dont worry... you'll back to ubuntu soon :) !!!! :)

---

### Post by ran0123456789 on 2012-02-03
now I have Success also with my laptop.:)

I want to ask some more quetion
1. is it possible to install microsoft office on linux???
2. I have low id on aMule
3. I found driver to my printer (xerox 3140) but i dont know how to install the driver?

---

### Post by mastablasta on 2012-02-03
> **ran0123456789 said:**
> now I have Success also with my laptop.:)
 
I want to ask some more quetion
1. is it possible to install microsoft office on linux???

2007 and older work via WINE
 
> 
3. I found driver to my printer (xerox 3140) but i dont know how to install the driver?
 
if the printer doesn't work with CUPS (out of the box) then drivers are indeeed needed. they have to be linux drivers. if they come in the form of tar.gz. file you need to extract it and find a readme file which will give you some commands to copy&paste in terminal to install the driver along with other information.

---

### Post by rudihawk on 2012-02-03
> **mastablasta said:**
> 2007 and older work via WINE
 


If this is true I might just :D

---


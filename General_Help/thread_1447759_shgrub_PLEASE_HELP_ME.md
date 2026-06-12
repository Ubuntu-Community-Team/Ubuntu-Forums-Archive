---
title: "sh:grub PLEASE HELP ME"
date: 2010-04-05
forum: General Help
---

### Post by Elliot.exe on 2010-04-05
I am running xubuntu on a Dell vostro 1500 laptop and it has gone into a black screen that says sh:grub how do I get out of that and back into the normal ubuntu.
 
 
 
Please help me I am deperate.
 
 
 
Thank You
 
 
 
Elliot Davies

---

### Post by drs305 on 2010-04-05
Elliot.exe,

Welcome to Ubuntu and the Ubuntu forums. If you are using Grub2, you are at a Grub 2 command line which may allow you to boot into your system using the commands listed in the following section of the Ubuntu community documentation on Grub 2. 

It may seem complicated, but just take it one step of the way. You will need to know where your Xubuntu installation is. Grub 2 counts the first drive as 0, the first partition as 1. So sda1 would be hd0,1. sda5 would be hd0,5 and sdb5 would be hd1,5, etc. 

If you don't know where your install is located, the "ls" command may help you find it.

Here is the link:
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot")

If you can't get it to boot, use the LiveCD and run meierfra's boot info script according to the instructions in this post:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

If you have questions or once you get it booted, come back and we'll try to fix it up.

---


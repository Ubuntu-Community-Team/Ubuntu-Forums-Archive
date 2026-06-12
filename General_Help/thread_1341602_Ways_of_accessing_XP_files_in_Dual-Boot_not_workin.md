---
title: "Ways of accessing XP files in Dual-Boot not working"
date: 2009-11-29
forum: General Help
---

### Post by Magael on 2009-11-29
I have a Lenovo G530 laptop, and a few weeks after I got it, I installed Ubuntu 9.04, which is now upgraded to 9.10 alongside XP. It was installed with the method of installing inside Windows XP, and has its own 40 GB folder.

Recently Windows XP is essentially broken, when I try to use it, it immediatly goes to the BSOD and my laptop restarts.

[http://www.wikihow.com/Access-Windows-Files-in-Ubuntu](http://www.wikihow.com/Access-Windows-Files-in-Ubuntu)

I had tried to use the above method to access my Windows XP files, but when I try to select my sda1 Parition, it says "Unable to mount location Internal Error: no mount object for mounted volume"

Is there a way to make this work, or another method to access the files in XP? All I really need are some open office word files, but they are very vital.

In Short: What is a reliable method of accessing XP files in a dual boot computer?

Thanks.

---

### Post by fluffman86 on 2009-11-29
Boot from an Ubuntu live CD and try to mount your Windows drive from there by going to Places > 100GB Media (or whatever size it is).  If you get an error, then open Applications > Accessories > Terminal, and type:

sudo mkdir /media/sda1
sudo mount /dev/sda1 /media/sda1 -t ntfs-3g -o force

It should then show up on your desktop.  If the wrong partition shows up (like a D: recovery drive instead of your C: drive) then change sda1 to sda2 and re-run the commands.

---


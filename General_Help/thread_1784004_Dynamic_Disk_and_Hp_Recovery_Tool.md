---
title: "Dynamic Disk and Hp Recovery Tool"
date: 2011-06-16
forum: General Help
---

### Post by cribcaged on 2011-06-16
Hi to everyone,

it's my first post :)

i have a laptop (hp dv6 pavillion i7 etc...) with windows 7

some time ago i tried to install ubuntu on dual boot with windows7 but i didn't because i discovered that my disk is dynamic and ubuntu can't install on that type of disk so i left windows7 and i tried to work with ubuntu on virtualbox

but now after some months...i really need ubuntu natively...so i decide to format all my entire disk and install ubuntu...but first i need to know which is the right sequence to do

i just made my dvd disks with HP Recovery Tool
i recall that my goal is also to have windows7 on dual boot with ubuntu...

so, is this the right sequence?:
- backup my data and app from windows
- format all with ubuntu live and install ubuntu from scratch
- use HP Recovery Tool to reinstall windows
- have fun

or:
- backup my data and app from windows
- use HP Recovery Tool
- resize the disk and install ubuntu
- have fun

i think that the right sequence is the second...but i fear that HP Recovery Tool will create again a dynamic disk...that is my problem now!

I really appreciate your help
Thank you

Daniele

---

### Post by Quackers on 2011-06-16
It is likely that you have dynamic disks because a fifth partition was created at some time when all 4 primary partitions were used up by your OEM system.

The correct sequence is the second one except that after recovery you will need to have a look at the Windows Disk Management screen. I suspect that you will find that all 4 primary partitions are used by the recovered system.
If this is the case you MUST NOT create another partition or install another operating system until one of those primary partitions has been deleted. Often the HP TOOLS partition is the one that is deleted, though this does not give enough space for Ubuntu to install into, so it is also necessary to shrink another partition, usually the C: partition (in Windows Disk Management screen) AFTER DEFRAGMENTING IT FIRST!
You will then get the "install alongside" option in the Ubuntu installer which should be enough for your needs (unless you want a separate home partition) - as long as you are not using Ubuntu 10.10, that is.

---

### Post by cribcaged on 2011-06-16
thank you for the answer!

in this weekend, i'll try :-)

Daniele

---

### Post by Quackers on 2011-06-16
Ok, take your time. 
If you're not sure about something just ask. It's easier to not do something wrong than fix it when it has gone wrong :-)

---


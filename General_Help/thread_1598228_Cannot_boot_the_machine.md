---
title: "Cannot boot the machine"
date: 2010-10-16
forum: General Help
---

### Post by r_lachu on 2010-10-16
Hi,

My filesystem crashed/corrupted. When i start my machine i see the following message

[I]Target filesystem doesn't have /sbin/init.
No init fount. Try passing init= bootarg.

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built in shell (ash)
Enter 'help' for a list of build in commands[/I]

After googleing, found that i need ti run fsck on my partition (/dev/sda5)

I used a Livecd and logged in the single user mode and tryed

fsck /dev/sda5

But i get 

[I]fsck.ext4: Device or source busy while trying to open /dev/sda5
Filesystem mounted or opened exclusively by another program?[/I]



When i do 

lsof | grep sda5

I see
[I]
jbd2/sda5 594  root cwd dir 0,17 280 2/
jbd2/sda5 594  root rtd dir 0,17 280 2/
jbd2/sda5 594  root txt unkown     /proc/594/exe
[/I]

I tried kill process 594 using
[I]
kill 594
kiill -9 594[/I]

and it didnt kill and also fsck still failed

I am not sure what to do next. Is reinstalling the only option available?

Help me
Lakshmanan

---

### Post by r_lachu on 2010-10-16
one more thing

When i try

umount /dev/sda5

it says the drive is not mounted

and 

mount /dev/sda5 /mnt

Took a long time and I couldnt kill this and hence rebooted the machine

---

### Post by r_lachu on 2010-10-16
Please help. All i need is some files from this machine and I think i will lose them if i reinstall the os. Please...

---

### Post by r_lachu on 2010-10-16
Finally found the solution

Created a bookable disk with [http://partedmagic.com/](http://partedmagic.com/) and used 'Failsafe option ->Console' option to goto console and executed fsck /dev/sda5.

Now i can log into my machine :)

---

### Post by capiscuas on 2010-10-26
THANKS A LOT!

I had the same problem and thanks for your post saying the solution you finally found it saved me a lot of time.

Keep that attitude!

Bes Regards.

---


---
title: "Ubuntu doesn't boot anymore"
date: 2010-07-06
forum: General Help
---

### Post by Indian Art on 2010-07-06
Hi!

I have installed Ubuntu 10.04 as a dual boot with XP.
For a few days I am not able to boot into Ubuntu. 

The computer starts and after the GRUB 10 seconds countdown this is the message I get:
"Starting Up ..."

Nothing happens after that. If I press Ctrl + Alt + Delete the computer reboots till the GRUB loader.

The computer can boot Ubuntu successfully from the Ubuntu 8.10 LiveCD successfully and I can see & access my files. I can also boot into XP.

I had a few improper shutdowns due to a UPS problem and power outages.

Please help. 

Thanks :)

---

### Post by Muttley99 on 2010-07-06
During boot press and hold the shift key. Select another Kernel from the list and try and boot into that. If you can get to a command prompt, type;

[HTML]touch /forcefsck[/HTML]

try restarting by typing;

[HTML]sudo shutdown -r now[/HTML]

---

### Post by Indian Art on 2010-07-09
> **Muttley99 said:**
> During boot press and hold the shift key. Select another Kernel from the list and try and boot into that. If you can get to a command prompt, type;

[HTML]touch /forcefsck[/HTML]

try restarting by typing;

[HTML]sudo shutdown -r now[/HTML]

I appreciate your prompt response, Muttley99.

I tried to get to the command line from GRUB but holding down Shift doesn’t work.

I tried typing ‘c’ to enter the GRUB command line, when I typed touch /forcefsck after GRUB> this is what I got:

“Error 27: Unrecognized command”

Is there any other way to get to the command line. 

Other versions of the Linux kernels of Ubuntu in GRUB have the same problem, ie, doesn’t get past, "Starting Up ..." with the curser blinking.

Typing ‘e’ also doesn’t get me to the command line.

I am able to access the Ubuntu partition with Ubuntu LiveCD. Will that work?

Eagerly waiting for help.

Thanks.

---

### Post by Muttley99 on 2010-07-13
Start the computer from the Live CD.
Enter the terminal and type;

[HTML]fdisk -l[/HTML]

'thats an ell not a one'!

from the list, find your boot partition - maybe /dev/sda1

type;

[HTML]cd /media[/HTML]

type;

[HTML]sudo mkdir a[/HTML]

type;

[HTML]sudo mount /dev/sda1 /media/a[/HTML]

(use the boot directory you found above i.e. /dev/sda1 or /dev/sba1 etc).

type;

[HTML]cd /media/a[/HTML]

type;

[HTML]sudo touch forcefsck[/HTML]

Then restart your computer (removing the disk)

---

### Post by Indian Art on 2010-07-14
> **Muttley99 said:**
> Start the computer from the Live CD.
Enter the terminal and type;

[HTML]fdisk -l[/HTML]

'thats an ell not a one'!

from the list, find your boot partition - maybe /dev/sda1

type;

[HTML]cd /media[/HTML]

type;

[HTML]mkdir a[/HTML]

type;

[HTML]mount /dev/sda1 /media/a[/HTML]

(use the boot directory you found above i.e. /dev/sda1 or /dev/sba1 etc).

type;

[HTML]cd /media/a[/HTML]

type;

[HTML]sudo touch forcefsck[/HTML]

Then restart your computer (removing the disk)

Thanks Muttley99 for your help,

I have a small question.

My LiveCD is Ubuntu 8.10 and the Ubuntu version that is installed on the computer is 10.04. So the question is:
Could I follow your suggestions with the LiveCD of Ubuntu 8.10 or do I need to download and make a LiveCD of Ubuntu version 10.04?

Appreciate your help.
:)

---

### Post by Muttley99 on 2010-07-14
You can use the 8.10 version. When you boot your computer with the live CD, it makes no changes to your hard drive. One cd I use which makes everything easy should any problems occur is 'Gparted live'. It boots to a graphical interface so its easy to run a disk check on your unmounted drives.

---

### Post by Indian Art on 2010-07-14
**Thanks Muttley99** for your help.

I will keep you posted on the results after following your suggestions.

Please expect a delay in my reporting the developments as I am in the midst of some other work.

---

### Post by 3Miro on 2010-07-14
By default 10.04 uses ext4 filesystem while 8.10 uses ext4. If you are using 10.04 with ext3 you will have no problems, otherwise it may be a better idea to get a 10.04 live CD.

---

### Post by m4tic on 2010-07-14
The filesystem used in Ubuntu 10.04 wasn't supported in Ubuntu 8.10
You need to get an Ubuntu 9.04 or upwards live cd to be able to use it as a recovery cd.

---

### Post by Indian Art on 2010-07-15
Thanks 3Miro & m4tic,

I haven't got to the recovery process yet. However, I found a final version of 9.10 (Karmic Koala) lying around at home. I will use that for recovery.

Appreciate the help.

---

### Post by Indian Art on 2010-07-16
Hi folks,

I was not able to rescue the system with the LiveCD (Ubuntu 9.10).
I got some messages in the terminal. One of them is appended after my note (this time I gave up 1/2 way). 

I am now going to do a fresh install with Ubuntu 10.04. That will give me EXT 4, the new Grub etc.

Thanks everyone. :) 

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ cd /media
ubuntu@ubuntu:/media$ mkdir a
mkdir: cannot create directory `a': Permission denied
ubuntu@ubuntu:/media$

---

### Post by Muttley99 on 2010-07-16
Sorry IA, I assumed you knew about sudo! I've ammended my original post; that should get rid of the errors.
You will be asked for your admin password.

---


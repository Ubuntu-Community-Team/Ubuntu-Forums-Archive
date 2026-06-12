---
title: "Help cannot boot ubuntu"
date: 2009-12-29
forum: General Help
---

### Post by gotanothergrot on 2009-12-29
Using distro loaded dvd which came from the latest (linux format magazine) I decided to install open SUSE. Now when I bootI cannot Get to Ubuntu or vista with all my files emails ect.  What did I do wrong I think I lost that partition to this new OS :( which I Know nothing about.  HELP

---

### Post by s.fox on 2009-12-29
Misread the question.  Apologies.

---

### Post by s.fox on 2009-12-29
Hi,

I assume you are booting into open suse at the minute.  Can you open up a terminal and post the output from

```
cat /proc/partitions
```

Again sorry for the first post.

-Silver Fox

---

### Post by Leppie on 2009-12-29
boot using the ubuntu livecd, then issue these commands:
```
$sudo mount /dev/sda5 /mnt  ##change /dev/sda5 to the partition ubuntu is installed
$sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by gotanothergrot on 2009-12-30
> **Silver_fox_ said:**
> Hi,

I assume you are booting into open suse at the minute.  Can you open up a terminal and post the output from

```
cat /proc/partitions
```

Again sorry for the first post.

-Silver Fox
graham@linux-ry1h:~> cat /proc/partitions
major minor  #blocks  name

   8        0  312571224 sda
   8        1      64228 sda1
   8        2   10485760 sda2
   8        3  146856445 sda3
   8        4          1 sda4
   8        5   14683378 sda5
   8        6    6048441 sda6
   8        7  128921593 sda7
   8        8    5502231 sda8
graham@linux-ry1h:~>

---

### Post by gotanothergrot on 2009-12-30
Leppie Ive written that code down (printer not working) and will follow as per instructions.

Thankfully All was not lost as the folders folders shows ubuntu and windows in my system, so I'm learning I think, that GRUB is in another location/partition when I boot.:confused:

---

### Post by gotanothergrot on 2009-12-30
OK this is using the live CD followed as per Leppie's instructions..

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt  ##change /dev/sda5 to the partition ubuntu is installed
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/disk/by-id/ata-WDC_WD3200AAKS-75B3A0_WD-WMAT12413982
ubuntu@ubuntu:~$ 


All looks good :) now for reboot.........

---

### Post by gotanothergrot on 2009-12-30
On reboot without the live CD I have black screen with:

                                    GNU GRUB version 1.97 beta
[minimal BASH-like line editing is supported. for the first word TAB lists possible command completions. Anywhere TAB lists possible device/file completions]

sh:grub>


Not so good for me I'm afraid  I am now down to the live CD (so much for trying new distro's)


Now back to live CD and
Added G-parted screen shot

---

### Post by gotanothergrot on 2009-12-30
help

---

### Post by Leppie on 2009-12-30
Please [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt

---

### Post by gotanothergrot on 2009-12-30
I cant open the download

---

### Post by Leppie on 2009-12-30
> **gotanothergrot said:**
> I cant open the download

it´s a script, so you will have to make it executable first:
```
$cd Desktop
$sudo chmod +x boot_info_script042.sh
```

run the script:
```
$sudo ./boot_info_script042.sh
```

---

### Post by gotanothergrot on 2009-12-30
I can't.

ubuntu@ubuntu:~$ cd Desktop
ubuntu@ubuntu:~/Desktop$ sudo chmod +x boot_info_script042.shsudo ./boot_info_script042.sh
chmod: cannot access `boot_info_script042.shsudo': No such file or directory
chmod: cannot access `./boot_info_script042.sh': No such file or directory
ubuntu@ubuntu:~/Desktop$ 


I feel like a total amature :(

---

### Post by Leppie on 2009-12-30
> **gotanothergrot said:**
> I can't.

ubuntu@ubuntu:~$ cd Desktop
ubuntu@ubuntu:~/Desktop$ sudo chmod +x boot_info_script042.shsudo ./boot_info_script042.sh
chmod: cannot access `boot_info_script042.shsudo': No such file or directory
chmod: cannot access `./boot_info_script042.sh': No such file or directory
ubuntu@ubuntu:~/Desktop$ 

not sure what you did here, but it should've been:
```
$cd Desktop
$sudo chmod +x boot_info_script042.sh
```

the message:
> chmod: cannot access `boot_info_script042.shsudo': No such file or directory
suggests you concatenated two commands.

---

### Post by gotanothergrot on 2009-12-31
no, its not working




Is there anything else that I can do? I just want to get to my OS 



When I boot normally (without live CD)
I get:

GNU GRUB version 1.97 beta
[minimal BASH-like line editing is supported. for the first word TAB lists possible command completions. Anywhere TAB lists possible device/file completions]

sh:grub>

'I'm completely lost'

---

### Post by Leppie on 2009-12-31
i just found out it's version 0.43 now:
```
$cd Desktop
$sudo chmod +x boot_info_script043.sh
```

---

### Post by gotanothergrot on 2009-12-31
no, sorry.

I even tried 044 as in the download.

---

### Post by Leppie on 2009-12-31
where was the script downloaded to?
right click on the script in ff and choose "open folder" this will show you where it put it. then change to that folder before using chmod.

---

### Post by gotanothergrot on 2009-12-31
Looks like it put it in downloads

---

### Post by gotanothergrot on 2009-12-31
is this correct so far?

---

### Post by Leppie on 2009-12-31
yes, this seems correct. if you're in the correct folder you can use tab-completion (press tab to complete a file name).

---

### Post by gotanothergrot on 2009-12-31
> **Leppie said:**
> yes, this seems correct. if you're in the correct folder you can use tab-completion (press tab to complete a file name).

no sorry.


ubuntu@ubuntu:~$ cd Downloads
ubuntu@ubuntu:~/Downloads$ sudo chmod +x boot_info_script044.sh
ubuntu@ubuntu:~/Downloads$ 
Display all 2689 possibilities? (y or n)

---

### Post by Leppie on 2009-12-31
you already seem to have completed the filename, so there's nothing to complete for the tab-completion functionality.

---

### Post by gotanothergrot on 2009-12-31
Is this correct?

---

### Post by Leppie on 2009-12-31
yes, it is. allow it to execute and post the generated file RESULTS.txt

---

### Post by gotanothergrot on 2009-12-31
Results.txt:
Your file of 61.0 KB bytes exceeds the forum's limit of 19.5 KB for this filetype.

---

### Post by gotanothergrot on 2009-12-31
Hope this works

---

### Post by Leppie on 2009-12-31
i get an error opening this file, could you re-uploa?

---

### Post by FDamn on 2009-12-31
Hi!

I installed ubuntu 9.10 in my netbook and after a grub actualization via internet the system doesn't start.

My problem is that I dont know how use the prompt of grub becouse its documentation use some commands that my grub doesn't have.

Any help? 
Some recomendation to avoid this problem in the future?

Thanks!
FDamn.

---

### Post by gotanothergrot on 2009-12-31
How about this

---

### Post by Leppie on 2009-12-31
> **gotanothergrot said:**
> How about this
this seems to be the script itself, not the generated RESULTS.txt.

---

### Post by gotanothergrot on 2009-12-31
Hallelujah I got it :)

---

### Post by Leppie on 2009-12-31
i had not understood this was a wubi install (ubuntu in windows).
are you still able to boot into opensuse?

---

### Post by gotanothergrot on 2009-12-31
no

---

### Post by Leppie on 2009-12-31
from the grub prompt (when your pc boots up), issue these commands:
```
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro		
initrd /initrd.img		
boot
```

this should boot you into openSuse. I do not know how to restore grub legacy to your mbr though (I have no experience with grub legacy).

---

### Post by Leppie on 2009-12-31
to re-install grub:
```
$sudo grub
> root (hd0,4)
> setup (hd0)
> exit
```
this should reinstall grub legacy to your master boot record, let me know if this doesn't work.

---

### Post by gotanothergrot on 2009-12-31
> **Leppie said:**
> to re-install grub:
```
$sudo grub
> root (hd0,4)
> setup (hd0)
> exit
```
this should reinstall grub legacy to your master boot record, let me know if this doesn't work.

Leppie, is this at the grub prompt when pc boots or in terminal?

---

### Post by Leppie on 2009-12-31
this is in a terminal, but from within one of your installations (let's say opensuse as i provided instructions for booting that os).
i believe that the grub prompt does not support the sudo command.

anyway, the sudo grub command triggers the grub shell.

---

### Post by gotanothergrot on 2009-12-31
output

ubuntu@ubuntu:~$ $sudo grub
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
grub: command not found
ubuntu@ubuntu:~$ > root (hd0,4)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ > setup (hd0)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ > exit

---

### Post by Leppie on 2009-12-31
> **gotanothergrot said:**
> output

ubuntu@ubuntu:~$ $sudo grub
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
grub: command not found
ubuntu@ubuntu:~$ > root (hd0,4)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ > setup (hd0)
bash: syntax error near unexpected token `('
ubuntu@ubuntu:~$ > exit

it looks like you are using a livecd, try booting using the instructions from post #35 and then retry the operation.

---

### Post by gotanothergrot on 2009-12-31
That didn't work, each line when entered returned me to the grub prompt.

I have open SUSE On the live CD that got me into this mess will booting that help me?

---

### Post by Leppie on 2009-12-31
> **gotanothergrot said:**
> That didn't work, each line when entered returned me to the grub prompt.

I have open SUSE On the live CD that got me into this mess will booting that help me?

yes, try the instructions from post #36 with the opensuse livecd.

---

### Post by gotanothergrot on 2009-12-31
> **Leppie said:**
> yes, try the instructions from post #36 with the opensuse livecd.

That went OK. Following the above procedure has enabled me to boot the open suse operating system. I still cannot get to Ubuntu 

I ran another boot script.

---

### Post by Leppie on 2009-12-31
I think you should be able to get to your windows and ubuntu installs selecting the "windows 2" option in the grub menu. this will chainload you into the boot menu your wubi install set up before you installed opensuse.
so, selecting "windows 2" will get you into another menu offering windows 7 and ubuntu.

---

### Post by gotanothergrot on 2009-12-31
Hey Leppie.  Thanks very very, much for sticking by this rookie, Much appreciated. I love Linux and you have been patient with me,Thanks.

PS
Its nearly midnight I have a big glass of southern comfort and I toast you a HappyNewYear2010.

Graham

---

### Post by Leppie on 2009-12-31
You are welcome, just glad it's working now.

May I suggest that if you really do like linux, you install Ubuntu into the 2 unused partitions you have on your hd? Actually you can use the swap partition for both distro's since it's only used for hibernation purposes (if you have sufficient ram).

A Happy New Year to you too! All the best for 2010!!

---


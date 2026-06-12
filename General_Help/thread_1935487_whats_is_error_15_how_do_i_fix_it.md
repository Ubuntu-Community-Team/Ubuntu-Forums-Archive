---
title: "whats is error 15? how do i fix it?"
date: 2012-03-04
forum: General Help
---

### Post by gudurukarthik on 2012-03-04
hi, i have just re-installed ubuntu in my Sony fw series laptop. as to boot through usb for installation i have changed the boot location to external drive and later after the installation is completed the movement to restart- i pressed f2 changed the bios back to internal hard drive and saved. but then comes
'' GRUB loading stage1.5.

GRUB loading, please wait..
Error 15
 ''
please ask for more required information to resolve this issue

---

### Post by Khayyam on 2012-03-04
The "Error 15" is "file not found", no doubt you installed grub with the device location of the external drive. [This]("http://stringofthoughts.wordpress.com/2009/05/25/grub-error-15-debianubuntu/") explains why it happens and should give you some idea of how to fix it.

HTH ... khay

---

### Post by raja.genupula on 2012-03-04
> **gudurukarthik said:**
> hi, i have just re-installed ubuntu in my Sony fw series laptop. as to boot through usb for installation i have changed the boot location to external drive and later after the installation is completed the movement to restart- i pressed f2 changed the bios back to internal hard drive and saved. but then comes
'' GRUB loading stage1.5.

GRUB loading, please wait..
Error 15
 ''
please ask for more required information to resolve this issue
 +1 to above 
do boot repair , look at grub recovery in my signature .

---

### Post by gudurukarthik on 2012-03-04
thank you firstly, 
but i was following the linked instructions and i type in [B]/boot/grub/menu.lst [B]terminal it just shows 
' ubuntu@ubuntu:~$ sudo fdisk -l | grep -i linux
/dev/sda1   *        2048   199999487    99998720   83  Linux
ubuntu@ubuntu:~$ menu.lst
menu.lst: command not found
ubuntu@ubuntu:~$ /boot/grub/menu.lst 
bash: /boot/grub/menu.lst: No such file or directory'

im sorry but did i do something wrong:(
[/B][/B]

---

### Post by raja.genupula on 2012-03-04
hi actually menu.lst file was replaced as grub.cfg in GRUB2 . now if you wanna understand clearly  whats the problems is look at here 

[https://help.ubuntu.com/community/Grub2#File_Not_Found_.28Error_15.29](https://help.ubuntu.com/community/Grub2#File_Not_Found_.28Error_15.29)
that link have solution also .

---

### Post by oldos2er on 2012-03-04
grub2 doesn't use a menu.lst file, see [https://help.ubuntu.com/community/Grub2#File_Not_Found_.28Error_15.29](https://help.ubuntu.com/community/Grub2#File_Not_Found_.28Error_15.29)

---

### Post by Khayyam on 2012-03-04
> **gudurukarthik said:**
> thank you firstly, but i was following the linked instructions and i type in /boot/grub/menu.lst terminal it just shows

```
ubuntu@ubuntu:~$ sudo fdisk -l | grep -i linux
/dev/sda1   *        2048   199999487    99998720   83  Linux
ubuntu@ubuntu:~$ menu.lst
menu.lst: command not found
ubuntu@ubuntu:~$ /boot/grub/menu.lst 
bash: /boot/grub/menu.lst: No such file or directory
```****I'm sorry but did i do something wrong

Firstly, those instructions are somewhat dated, and as raja stated Ubuntu now uses Grub2 and the config file has changed, so your best to follow the instructions provided by raja.

Secondly, yes you did do "something wrong" .. your treating "menu.lst" as a command, and not as a file. Also, you should codeblocks rather than use **bold**

best ... khay

---

### Post by gudurukarthik on 2012-03-04
thank you. 
one last thing sir, i'm now re installing the os .. i choose the something else part in the installation type and i have two partitions out their.. on is device: /dev/sda type: ext 4   size: 102398 mb and a other device: free space and now file type given and sized 397708 mb: 
as i understood that i'm doing something wrong in this part i tried to make it clear. what should i be doing here.. pls help me out im a beginner and very interested in using ubuntu.

---

### Post by Khayyam on 2012-03-04
> **gudurukarthik said:**
> thank you. one last thing sir, i'm now re installing the os .. i choose the something else part in the installation type and i have two partitions out their.. on is device: /dev/sda type: ext 4   size: 102398 mb and a other device: free space and now file type given and sized 397708 mb: 
as i understood that i'm doing something wrong in this part i tried to make it clear. what should i be doing here.. pls help me out im a beginner and very interested in using ubuntu.

1). not every user here is male and so best not to make assumptions in that regard.
2). not every user here is using Ubuntu

The first device will be /dev/sda1 this will be where Ubuntu is installed. The installer will then make "extended" partitions for the rest of the disk and create a "swap" on /dev/sda5 (the first "extended" partition) using the "free space". In your case this "free space" is much bigger than you've asigned to "sda1" you may or may not have done this for a reason (like installing another OS on the disk), but generally you want the largest space alloted to the partition (sda1) where the OS will be installed and where you will store you files. Other partitions could be created (from "free space") for this purpose, but its best to do this at the install stage.

Hopefully I've understood your question, as its not altogether clear what your asking.

best ... khay

---

### Post by oldfred on 2012-03-04
You do want to use manual install or something else to reuse or change your existing partitions. The automatic install would probably just create new partitions leaving old install.

I often suggest a smaller / (root) partition of 10 to 25GB and use the rest of the space you want for Ubuntu as /home in a separate partition. Swap can be 2GB or the size of RAM in GiB or a little larger that RAM in GB so it truly is the same size as RAM and can have enough room to hibernate.

Some examples with screen shots:

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by Khayyam on 2012-03-04
> **gudurukarthik said:**
> thank you. one last thing sir, i'm now re installing the os [...]

Why are you reposting the same message (half an hour later) when you've recieved a reply?

---

### Post by gudurukarthik on 2012-03-04
hey the issue is solved and thank you for the support

---


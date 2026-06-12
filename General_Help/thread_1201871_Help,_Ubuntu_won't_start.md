---
title: "Help, Ubuntu won't start"
date: 2009-07-01
forum: General Help
---

### Post by tracker741 on 2009-07-01
I get into the menu where I choose operating systems and after I pick ubuntu it brings me to a weird screen. It looks simalar to a command prompt screen but where you type is preceeded by grub>. Also if you click escape it brings you to a menu where you can choose to find several files, reboot, or halt. Sorry for the lack of technicality when describing this.
 
What should I do?

---

### Post by Megrimn on 2009-07-01
could you post the contents of /boot/grub/menu.lst?  post if you need help accessing the file.

---

### Post by ramnarayan on 2009-07-01
Hi

Describe you OS's a bit
what Ubuntu are you using, did you install something recently (like another OS)

Have you used your system at all ?

What other OS's are available in the grub
is there a recovery option, if yes down arrow to that and enter and see what happens.

Try and note the exact error message and post the message as well as google for it.

do you have a live Ubuntu CD with you, in case you need to do any recovery stuff.

---

### Post by tracker741 on 2009-07-01
ok so to go to more detail. The screen im seeing after I click ubuntu on the operating systems list displays this:
 
--------------------------------------------------------------------------------------
GRUB4DOS 0.4.4 2008-10-27, Memory: 640k/1021m, CodeEnd: 0x42910
[Minnimal BASH-Like line editing is supported. for the first word, TAB lists possible command completions. Anywhere esle TAB lists the possible completions of a device/filename. ESC at anytime exits.
 
GRUB>
---------------------------------------------------------------------------------------
If I click escape this screen comes up:
 
---------------------------------------------------------------------------------------
Find /ubuntu/disks/boot/Grub/menu.lst
Find /ubuntu/install/boot/Grub/menu.lst
Find /menu.lst
Find /boot/Grub/menu.lst
Find /Grub/menu.lst
commandline
reboot
halt
----------------------------------------------------------------------------------------
 
I'm running ubuntu 8.10 and haven't installed programs or files since a few sessions before the problem occured.
 
Hopefully that helps.

---

### Post by Megrimn on 2009-07-01
I think that your menu.lst file may be corrupt... posting the contents of it would help.  

have you tried *recovery mode*?

---

### Post by tracker741 on 2009-07-01
the only options that do anything are the reboot and halt options. All the others just bring me back to the first screen. There is no recovery mode option. How would I go about getting into that?

---

### Post by ramnarayan on 2009-07-02
> **tracker741 said:**
> the only options that do anything are the reboot and halt options. All the others just bring me back to the first screen. There is no recovery mode option. How would I go about getting into that?

Do you have any idea what your partitioning table looks like ??
means where is your /boot /root /home etc installed 

Boot using the live cd

once thats up and running
try this command sudo fdisk -l 
this should give you an idea of your partition table

go to Places and computer where a list of your partitions will be available and try and navigate to /mediafoo/boot/grub/menu.lst

post this here and lets see what's happened for this error.

IMP QUESTION - do you have any other OS installed alongside ??

ram

---

### Post by ramnarayan on 2009-07-02
[QUOTE=tracker741;7547196]
--------------------------------------------------------------------------------------
GRUB4DOS 0.4.4 2008-10-27, Memory: 640k/1021m, CodeEnd: 0x42910
[Minnimal BASH-Like line editing is supported. for the first word, TAB lists possible command completions. Anywhere esle TAB lists the possible completions of a device/filename. ESC at anytime exits.
 
DID you install Ubuntu through WUBI - that is through WINDOWS ??

ram

---

### Post by ronaldprettyman on 2009-07-02
> **tracker741 said:**
> ok so to go to more detail. The screen im seeing after I click ubuntu on the operating systems list displays this:
 
--------------------------------------------------------------------------------------
GRUB4DOS 0.4.4 2008-10-27, Memory: 640k/1021m, CodeEnd: 0x42910
[Minnimal BASH-Like line editing is supported. for the first word, TAB lists possible command completions. Anywhere esle TAB lists the possible completions of a device/filename. ESC at anytime exits.
 
GRUB>
---------------------------------------------------------------------------------------
If I click escape this screen comes up:
 
---------------------------------------------------------------------------------------
Find /ubuntu/disks/boot/Grub/menu.lst
Find /ubuntu/install/boot/Grub/menu.lst
Find /menu.lst
Find /boot/Grub/menu.lst
Find /Grub/menu.lst
commandline
reboot
halt
----------------------------------------------------------------------------------------
 
I'm running ubuntu 8.10 and haven't installed programs or files since a few sessions before the problem occured.
 
Hopefully that helps.

Your at the grub menu. You can type grub commands from here. If your still have this problem try these command to get into to linux to even look at your /boot/grub/menu.lst that everyone is refering to.

hd0,0 is primary drive partion 1
so hd1,0 would be a second drive
if you only have one drive and only have ubuntu its probably
hd0,0
if you have windows installed and only one drive its probably
hd0,1 or hd0,2
if you have windows on the first drive and linux on the second try
hd1,0
if you have windows on the second drive and linux on the first
hd0,0
```
grub> root (hd0,0)
grub> kernel /boot/vmlinuz
grub> initrd /boot/initrd.img
grub> boot
```
experiment between these until it works
you might have to go though it two or three times.

you can also type help to get a full list of commands
```
grub> help
```

---


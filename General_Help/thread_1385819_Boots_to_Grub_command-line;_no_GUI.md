---
title: "Boots to Grub command-line; no GUI"
date: 2010-01-20
forum: General Help
---

### Post by whattf on 2010-01-20
Hello,
        I'm fairly new to this all so any help is appreciated. I used the Wubi installer to install the latest version (available from the website) on my second physical HDD. I rebooted my machine and used the Windows 7 bootloader to launch Ubuntu and it launched a GUI install. I wasn't sure how long it was going to take, so I left for about a half hour and when I returned I was back to my Windows 7 logon screen. Naturally, I assumed the install was a success and I rebooted my machine. When I boot again I get the Windows bootloader and I see my options for Windows 7 (which works properly) or Ubuntu. However, if I select Ubuntu I am brought to a command-line and there is an output at the top of the screen stating "Grub bootloader." At this point do I need to type anything to launch the GUI  (I'm assuming Gnome) from this? How should I proceed from this point, reinstall? Any input would be appreciated. Thank you.

---

### Post by dzon65 on 2010-01-20
That doesn't sound right.After the boot choice should find something like ntfs and after that a blinking choice which kernel and proceed to the boot.There should not be a command line whatsoever.

---

### Post by wlraider70 on 2010-01-20
I can't give you too much help here.
Wubi is quite a different beast and rather difficult.

try "sudo apt-get install ubuntu-desktop"

or

"sudo apt-get install kubuntu-desktop"


rather i would recommend using a live CD to check it out and install ubuntu to a partition or 2nd drive when you are ready.

---

### Post by whattf on 2010-01-20
> **wlraider70 said:**
> I can't give you too much help here.
Wubi is quite a different beast and rather difficult.

try "sudo apt-get install ubuntu-desktop"

or

"sudo apt-get install kubuntu-desktop"


rather i would recommend using a live CD to check it out and install ubuntu to a partition or 2nd drive when you are ready.

Alright, those are some good suggestions, thank you. Yeah, I originally left 60 GB free on my second HDD to use the Live CD to install. However, I browsed your forums and they mentioned that it would automatically write Grub to the MBR. I wanted the Windows bootloader to stay in the MBR so I was hesitant to try that method.

---

### Post by whattf on 2010-01-20
> **wlraider70 said:**
> I can't give you too much help here.
Wubi is quite a different beast and rather difficult.

try "sudo apt-get install ubuntu-desktop"

or

"sudo apt-get install kubuntu-desktop"


rather i would recommend using a live CD to check it out and install ubuntu to a partition or 2nd drive when you are ready.

That's not working. It returns "error: unknown command 'sudo'". Can you tell me how to use the live CD to install Ubuntu without also installing Grub?

---

### Post by whattf on 2010-01-20
Also, there is some text that flashes before it presents me with the grub command prompt, is there a way to slow this down? 

Additionally, if I hit tab (to present the commands) it has a list including- boot, cat, chainloader, echo, dump, linux ....      

If I type "boot" it will return no kernel loaded.

---

### Post by amsterdamharu on 2010-01-20
Your menu.conf is missing or has errors so nothing is booted just grub, grub should load the kernel and the initrd.

try the following commands:

```
find /boot/grub/stage1
```This should return something like (hd0,4) which means first harddisk second partition.
If this doesn't return anything I suggest install again.
if it does replace (hd0,4) with what you got:

```
root        (hd0,4)
find (hd0,4)/boot/vmlinuz-(press tab here)

```my output of find is:
 Possible files are: vmlinuz-2.6.24-24-generic vmlinuz-2.6.24-25-generic vmlinu
z-2.6.24-26-generic vmlinuz-boot
lets use vmlinuz-2.6.24-26-generic

```
kernel        /boot/vmlinuz-2.6.24-26-generic ro quiet splash
```Lets see what initrd is available:
```
find (hd0,4)/boot/initrd(press tab)
```My output is:
Possible files are: initrd.img-2.6.24-24-generic.bak initrd.img-2.6.24-24-gene
ric initrd.img-2.6.24-25-generic.bak initrd.img-2.6.24-25-generic initrd.img-2.
6.24-26-generic.bak initrd.img-2.6.24-26-generic initrd-boot.img
Lets use initrd.img-2.6.24-26-generic

```
initrd        /boot/initrd.img-2.6.24-26-generic
boot

```
This should boot your ubunto, however this stuff should be in your grub.conf file in /boot/grub so if you got it booted you have to create that file with the correct values.

My grub.conf:
```

default        0
timeout        1
title        Ubuntu
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-26-generic ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

```

---

### Post by Leppie on 2010-01-20
follow a guide like this one: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by amsterdamharu on 2010-01-20
No please don't restore, the poster says he doesn't want to change win mbr and installed grub on a partition. Nothing's wrong with the mbr or grub on the partition for that matter it just has something wrong in the grub.conf or there is no grub.conf.

---

### Post by Leppie on 2010-01-20
> **amsterdamharu said:**
> This should return something like (hd0,4) which means first harddisk second partition.
since you're showing grub legacy, (hd0,4) is actually partition number 5 (not second partition) on disk 1

---

### Post by Leppie on 2010-01-20
i modified posts after rereading.
my advise: do a side by side install, wubi installs can be a pain troubleshooting.

---


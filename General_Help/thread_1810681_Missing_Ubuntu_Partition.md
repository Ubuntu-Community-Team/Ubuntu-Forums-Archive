---
title: "Missing Ubuntu Partition"
date: 2011-07-23
forum: General Help
---

### Post by Richiegs on 2011-07-23
My computer has 2 partitions, Ubuntu and Windows XP. After I upgraded from Windows XP to Vista. The Ubuntu partition is missing at startup. I know Ubuntu is still there and it probably has something to do with bootloader. Can anyone show me how to fix it? Thank you

---

### Post by jramshu on 2011-07-23
Do you want grub or Windows to control the bootloader?

---

### Post by Blasphemist on 2011-07-23
You should be able to boot to the live cd and reinstall Grub to fix it, if nothing unusual has happened. This is the code to run where sdax is sda and the number of the ubuntu partition.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
```

The word boot in the second line would be root if you are using grub legacy. Actually root will work with either version but it just isn't the recommended parameter from the developers.

---

### Post by temporos on 2011-07-23
First, good god, man!  Why would you want to "upgrade" to Vista?!  :shock: Even Microsoft admits that XP is the better Windows OS.

Anyway, this is a common problem for Vista users.  The Windows boot loader disabled Grub and installed its own.  Then, it told the new boot loader to automatically boot into Windows, because that's just how Microsoft works.  They don't want you using Linux.  ;)

To fix it, just re-install Grub from the Ubuntu LiveCD or a Knoppix CD (I like to use Knoppix for emergency maintenance and repair issues).  If you installed Ubuntu with the default partition scheme, then Blasphemist's solution will work.  If you set up your own partitions, then you'll need to run *fdisk* to find the Ubuntu OS partition.

---

### Post by Richiegs on 2011-07-25
> **jramshu said:**
> Do you want grub or Windows to control the bootloader?

I want Grub to control the bootloader.

---

### Post by Richiegs on 2011-07-25
> **Blasphemist said:**
> You should be able to boot to the live cd and reinstall Grub to fix it, if nothing unusual has happened. This is the code to run where sdax is sda and the number of the ubuntu partition.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
```The word boot in the second line would be root if you are using grub legacy. Actually root will work with either version but it just isn't the recommended parameter from the developers.

Thanks, but when I turn on my PC, it will automatically go to Windows Vista. I can't select or access Ubuntu.

---

### Post by Richiegs on 2011-07-25
> **temporos said:**
> First, good god, man!  Why would you want to "upgrade" to Vista?!  :shock: Even Microsoft admits that XP is the better Windows OS.

Anyway, this is a common problem for Vista users.  The Windows boot loader disabled Grub and installed its own.  Then, it told the new boot loader to automatically boot into Windows, because that's just how Microsoft works.  They don't want you using Linux.  ;)

To fix it, just re-install Grub from the Ubuntu LiveCD or a Knoppix CD (I like to use Knoppix for emergency maintenance and repair issues).  If you installed Ubuntu with the default partition scheme, then Blasphemist's solution will work.  If you set up your own partitions, then you'll need to run *fdisk* to find the Ubuntu OS partition.

What is Ubuntu LiveCD? Is it same as Ubuntu installation disk?

---

### Post by wildmanne39 on 2011-07-25
Hi you need to select boot from a cd in the bios when you first turn on the computer and then use the livecd to reinstall grub here is a great guide if you need it.
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

---

### Post by Quackers on 2011-07-25
Yes.
Which partition is Ubuntu on? If it's on /dev/sda5 and it's 11.04 then Blasphemist's instructions will work.
If it's not on sda5 and it's not Ubuntu 11.04 the commands will need changing slightly.

---

### Post by Richiegs on 2011-07-25
Ubuntu 11.04 was installed in my PC. Can I use the disk which contains Ubuntu 10.04 as Ubuntu Live CD to reinstall Grub?

---

### Post by Quackers on 2011-07-25
Is 10.04 the version that is installed on your hard drive?
If so, yes. Boot from the live cd and select "try Ubuntu" then open up gparted and see which partition Ubuntu is on.

---

### Post by wildmanne39 on 2011-07-25
Hi, you said you have ubuntu 11.04 installed so you will need to use 11.04 livecd or you will really mess up grub.

---

### Post by Richiegs on 2011-07-25
> **Quackers said:**
> Is 10.04 the version that is installed on your hard drive?
If so, yes. Boot from the live cd and select "try Ubuntu" then open up gparted and see which partition Ubuntu is on.

Version 11.04 was installed in my PC through Update Manager in Ubuntu. But I have a disk containing Ubuntu 10.04. Will that disk work? Many thanks

---

### Post by Quackers on 2011-07-25
It should get it booting again but it will install an older version of grub, but having said that, grub may update itself via synaptic later.
A 11.04 live cd would be better, if possible.
You still need to open gparted and find out which partition is your Ubuntu root partition before you can re-install grub.

---

### Post by Richiegs on 2011-07-25
> **jramshu said:**
> Do you want grub or Windows to control the bootloader?


If I reinstall Grub,  I probably have to download Ubuntu 64-bit 11.04. Jramshu, if I want Windows to control the bootloader, what should I do? Many thanks

---

### Post by Richiegs on 2011-07-25
> **Quackers said:**
> It should get it booting again but it will install an older version of grub, but having said that, grub may update itself via synaptic later.
A 11.04 live cd would be better, if possible.
You still need to open gparted and find out which partition is your Ubuntu root partition before you can re-install grub.

that sounds easier because I really do not want to download the 64-bit Ubuntu 11.04. The 64-bit 11.04 version is a lot slower than the 64-bit 10.04 version I used previously. I am not sure if the 32-bit Ubuntu 11.04 is also as slow as the 64-bit version. I will try it later. Many thanks for your help.

---

### Post by Quackers on 2011-07-25
No problem. Have fun :-)

---

### Post by Richiegs on 2011-07-25
> **wildmanne39 said:**
> Hi you need to select boot from a cd in the bios when you first turn on the computer and then use the livecd to reinstall grub here is a great guide if you need it.
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

When I type $ sudo chroot/mnt  
The response is sudo: chroot/mnt: command not found

What does it mean?
Now I can't even access Vista either. 

HELP

---

### Post by Quackers on 2011-07-25
You don't need to chroot. Unmount everything you've mounted and run ```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
``` where sdXY in the first command is your Ubuntu root partition and sdX in the second command is your hard drive designation. Swap them for yours.
If you had told us which partition your Ubuntu root is on, as asked several times, I could give you specific commands. But you haven't.

If you could access Vista before and now you can't then you've done something wrong and the above may not now be enough.

---

### Post by wildmanne39 on 2011-07-25
Hi, you are in good hands so I will let Quackers help you.

---


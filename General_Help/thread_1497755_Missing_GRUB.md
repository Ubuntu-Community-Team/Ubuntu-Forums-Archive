---
title: "Missing GRUB"
date: 2010-05-31
forum: General Help
---

### Post by sanderson113 on 2010-05-31
Ok, I'm not sure where to post this so I figured here would be a good start.

I have a two drive dual boot system. SATA 1 is a 250 gb drive with Windows XP installed. I then installed Ubuntu 10.04 on SATA 2 and had it checked to install GRUB to SDA1. After Ubuntu installed and I rebooted my computer, there was no GRUB. Instead just booted into Ubuntu. How can I get GRUB installed so it comes up and allows me to select the OS that I want? Thanks,

Scott

---

### Post by dcstar on 2010-05-31
> **sanderson113 said:**
> Ok, I'm not sure where to post this so I figured here would be a good start.

I have a two drive dual boot system. SATA 1 is a 250 gb drive with Windows XP installed. I then installed Ubuntu 10.04 on SATA 2 and had it checked to install GRUB to SDA1. After Ubuntu installed and I rebooted my computer, there was no GRUB. Instead just booted into Ubuntu. How can I get GRUB installed so it comes up and allows me to select the OS that I want? Thanks,

Scott

If Grub was not configured to see the other OS then it will boot up without a menu, do this:

```
sudo update-grub
```

---

### Post by garvinrick4 on 2010-05-31
If you cannot get grub menu I believe you should have put grub in sda not sda1.

You can do it with a live CD.

If you need help post outcome of this here. If you got it working great.

```
sudo fdisk -l
```

```
sudo blkid
```

---

### Post by finlost on 2010-05-31
> **garvinrick4 said:**
> If you cannot get grub menu I believe you should have put grub in sda not sda1.
Should it be sda0 instead of sda?

---

### Post by Elfy on 2010-05-31
> After Ubuntu installed and I rebooted my computer, there was no GRUB. Instead just booted into Ubuntu.Did you try pressing shift to see the menu?

---

### Post by garvinrick4 on 2010-05-31
If need the assistance still.


  Given my ubuntu install with grub is in sda5 and it is labeled as maverick.
Use whatever yours are. My mbr is in sda1 labeled SYSTEM. As you see I am putting it 
into sda and never sda1, sda5 alway, always sda.


--------------Use a Live CD.-------------------------------------------------
      Make directory for mbr if there is a seperate partition for mbr.  
      Code:
 sudo mkdir /media/SYSTEM
  
Make directory OS
Code:
 sudo mkdir /media/maverick 
  
Mount OS
Code:
 sudo mount [/dev/sda5]("file:///media/dev/sda5") [/media/maverick]("file:///media/media/maverick") 
  
Mount mbr partition if have one.
Code:
 sudo mount [/dev/sda1 ]("file:///media/dev/sda1")[/media/SYSTEM]("file:///media/media/SYSTEM") 
  
install grub to sda
Code:
 sudo grub-install --recheck --root-directory=/media/maverick [/dev/sda]("file:///media/dev/sda") 
  
Unmount
Code: (Not a typo)
 sudo umount /media/maverick 
  
Unmount
Code:
 sudo umount /media/SYSTEM

---


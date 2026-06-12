---
title: "Usb Boot Help"
date: 2009-07-25
forum: General Help
---

### Post by maggot2014 on 2009-07-25
OK i have looked and looked for hours on here on how to fix my problem with no luck so here si my problem.
I am running a acer aspire one doul boot with windows xp sp3 and ubuntu 9.04. for some reason my grub 1.5 became currupted and everytime i boot my computer it goes to an error 17. The acer aspire one does not come with an optical drive and I ahve yet to obtain one. but i do have a ubuntu 9.04 live cd. so i am using another computer running windows 2000 to try and find a fix. i made an iso from the cd and tried to install it on a flash drive with unetbootin and with no luck didnt work.. just went to a blank screen when i booted from it. so i tried to format my usb to try that. now everytime i try and boot from it it give me a "Invalid System Data" "please replace disk and press any key to continue" i ahve another 1gb flash drive at my use but its holding the iso... So to come down to my question. Is there anything else i can use to put the iso on the flash drive besides unetbootin. the works really well on my windows 2000 computer to install stright form the cd to the usb

---

### Post by nabokov on 2009-07-25
what do you have your flash drive formated in NTFS or FAT32.. for a bootable flash for linux it needs FAT32.. or soo i heard

---

### Post by pro003 on 2009-07-25
there is a nice iso image to download and it's free, called [Super Grub Disk]("http://www.supergrubdisk.org/index.php?pid=5")



although you can boot into repair mode and then try to fix grub from given menu

other method is to mount ur live ubuntu cd and select Fix Broken System, then mount /dev/sda# (#=-number of ur partition where ubuntu is installed)

drop to root shell and type

```
# grub-install /dev/hd0
```

If it is the first BIOS drive, this is the same as well:

```
# grub-install '(hd0)'
```

if this doesn't work try

```
# grub-install /dev/sda

# reboot
```

select repair mode, then select from menu UPDATE GRUB CONFIGURATION...

---

### Post by maggot2014 on 2009-07-25
> **nabokov said:**
> what do you have your flash drive formated in NTFS or FAT32.. for a bootable flash for linux it needs FAT32.. or soo i heard


I have it formatted to Fat 32

---

### Post by maggot2014 on 2009-07-25
> **pro003 said:**
> there is a nice iso image to download and it's free, called [Super Grub Disk]("http://www.supergrubdisk.org/index.php?pid=5")



although you can boot into repair mode and then try to fix grub from given menu

other method is to mount ur live ubuntu cd and select Fix Broken System, then mount /dev/sda# (#=-number of ur partition where ubuntu is installed)

drop to root shell and type

```
# grub-install /dev/hd0
```

If it is the first BIOS drive, this is the same as well:

```
# grub-install '(hd0)'
```

if this doesn't work try

```
# grub-install /dev/sda

# reboot
```

select repair mode, then select from menu UPDATE GRUB CONFIGURATION...


I tried to run super grub disk from my unetbootin and nothing i got from it loaded bootable. and i canot get into any repair mode i cnt boot into anything once it starts it goes to my acer screen with f2 setup and f12 for boot order..(and yes i changed boot order to usb when trying to boot from it) and then once that screen changes it says grub 1.5 error 17

---

### Post by maggot2014 on 2009-07-25
please any one if i can just get to a comand i can get it to work but i cant get into anything

---

### Post by pro003 on 2009-07-25
man it's got to be working, download iso image about 4mb size and burn it to cd-rom, boot from it and then just follow the instructions, it guides you to boot from any partition of your hard drives, it never fails, you can even remove your broken grub conf and automatically install new one, i tried it x times and always worked...

---

### Post by maggot2014 on 2009-07-25
> **pro003 said:**
> man it's got to be working, download iso image about 4mb size and burn it to cd-rom, boot from it and then just follow the instructions, it guides you to boot from any partition of your hard drives, it never fails, you can even remove your broken grub conf and automatically install new one, i tried it x times and always worked...

If you read my original post carefully i have no optical drive on the computer i am trying to fix so i cant burn it to a cd well i can bubt it would be of no use

---

### Post by pro003 on 2009-07-25
> **maggot2014 said:**
> If you read my original post carefully i have no optical drive on the computer i am trying to fix so i cant burn it to a cd well i can bubt it would be of no use

sorry, hence there are different super grub ways, there is also a a way to install it on USB pendrive.

btw, whats ur first boot device?

---

### Post by maggot2014 on 2009-07-25
well now that i haave been trying to install from usb for hours its set to usb before that it was set to my hddi just need a program that will whipe my flash drive and install an iso on to it besides unetbootin

---

### Post by pro003 on 2009-07-25
I just remembered that there are nice tools to fix grub from new Puppy Pendrive Linux... Gooogle it and see if that will work.

---


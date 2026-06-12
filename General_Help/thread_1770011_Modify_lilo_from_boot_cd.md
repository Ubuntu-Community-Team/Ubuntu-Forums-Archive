---
title: "Modify lilo from boot cd"
date: 2011-05-28
forum: General Help
---

### Post by ladlers on 2011-05-28
Is there a way to run the lilo command from the ubuntu 10.10 boot cd? It doesn't get the directories right, as it has / mounted as the ramdisk memory file system, and / can't be demounted since it's busy. I can install lilo in the ram after booting from the cd with sudo apt-get install lilo. Mounting / to my sdb1 partition (where Ubuntu is installed) does not get the proper "maps" for the lilo command, since the cd ramdisk / takes priority. I prefer not to use grub, as I wish to use windows vista's bcd(edit) as the main boot selector and it won't boot grub from bcd to a partition; at least I couldn't get it to work in 11.04. I got lilo to work from the vista's bcd menu in 11.04, but had many glitches. Windows allows this type of proceedure from its recovery cds. Thanks.

---

### Post by andrew.46 on 2011-05-28
I cannot completely grasp the problem you describe but if you have lilo installed you should be able to edit its configuration file from the rescue cd by opening /etc/lilo.conf. You will need to run 'lilo' after you have done so.

---

### Post by Rubi1200 on 2011-05-28
ladlers, I am also not quite sure what you want to do. 

Do you mean install lilo to the MBR of the drive from the LiveCD? If so, then the answer is yes.

You can do it like this:

```
sudo apt-get install lilo

sudo lilo -M /dev/sdX mbr
```

Replace X with whatever designation you need e.g. sda, sdb, sdc etc.

lilo will throw up some warnings, but these can be ignored since you just want to install it to the MBR of the relevant drive.

If this is not what you mean, please explain more clearly so we can help you.

Also, posting the results of the boot info script would also give us a clearer picture.

Thanks.

---

### Post by ladlers on 2011-05-28
I think that's the thing, Rubi1200. I got by an alternate route so I can't test what you tell me. Next install (October?)

---

### Post by ladlers on 2011-07-01
Just for your information, I had to do this with Slackware linux, so everyone will know how to recover a nonbooting system. Remember, this is Slackware, so you may have to throw in some sudo commands. You simply boot the Knoppix live cd and type:

mount /dev/sda2 /media/sda2
chroot /media/sda2 lilo -v

Since I am quadrupile booting with 2 Vistas and a Ubuntu, I then must prepare lilo for the Vista bcdedit system by, copying the boot sector:

dd if=/dev/sda2 of=/media/sdc1/linux.bi bs=512 count=1

I then copied the file linux.bi to my first Vista partition and viola.

---


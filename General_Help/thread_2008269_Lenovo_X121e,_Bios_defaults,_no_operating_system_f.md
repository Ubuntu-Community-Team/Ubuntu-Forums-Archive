---
title: "Lenovo X121e, Bios defaults, no operating system found"
date: 2012-06-22
forum: General Help
---

### Post by subculture on 2012-06-22
Hello,

Lenovo X121e, OCZ Agillity SSD, Ubuntu Studio 12.04

After reset Bios setup defaults, booting display -> no operating system found


This is what i have done so far <from within the live cd>... please need help
```

ubuntu-studio@ubuntu-studio:/$ sudo find -name grub-install
./usr/lib/grub/i386-pc/grub-install
./usr/sbin/grub-install
./rofs/usr/lib/grub/i386-pc/grub-install
./rofs/usr/sbin/grub-install
ubuntu-studio@ubuntu-studio:/$ sudo /usr/sbin/grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
ubuntu-studio@ubuntu-studio:/$ sudo mount /dev/sda2 /mnt
ubuntu-studio@ubuntu-studio:/$ sudo chroot /mnt
root@ubuntu-studio:/# sudo /usr/sbin/grub/install /dev/sda
sudo: unable to resolve host ubuntu-studio
sudo: /usr/sbin/grub/install: command not found
root@ubuntu-studio:/# sudo /usr/sbin/grub-install /dev/sda
sudo: unable to resolve host ubuntu-studio
/usr/sbin/grub-mkdevicemap: error: cannot open /dev/stdout.
/usr/sbin/grub-probe: error: cannot find a device for /boot/efi (is /dev mounted?).
/usr/sbin/grub-mkdevicemap: error: cannot open /dev/stdout.
/usr/sbin/grub-probe: error: cannot find a device for /boot (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
root@ubuntu-studio:/# 
```

---

### Post by Enigmapond on 2012-06-22
Try this and use the second option while in the LiveCD...
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by subculture on 2012-06-22
first of all, thank for your reply... such a tool like boot repair is great...

unfortunately i do get an error message with boot repair...

```
GPT detected. Please create a BIOS-Boot partition (>1Mo, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [] option.
```

This is the Boot Summary Info.. or something like that which i could create in boot repair tool>
[http://paste.ubuntu.com/1054753/](http://paste.ubuntu.com/1054753/)

---

### Post by subculture on 2012-06-22
This stuff seems to be a big headnut... since the first time i installed linux on this laptop, i recognised that during the boot from dvd, there was not the regular menu... i got an message "no prefex is found or set"... i didnt thought about anything but knew somehow its got to be something because of the bios in this lenovo laptop...

however... i have now tryed all kinds of stuff in relation to the first errormessage of the boot repair tool... and i dont even know anymore if all this was realy good... i delete the so called efi partition, createt a new unformated one and changed flag to grub something... so after i did this i got more messages in the boot repair tool, like tis one:

```
The boot of your PC is in EFI mode, but no EFI partition was detected.  You may want to retry after creating a EFI partition (FAT32, >200Mo,  start of the disk, boot flag).
The boot of your PC is in EFI mode. You may want to retry after changing it to BIOS-Legacy mode.
Do you want to continue?
```Anyway, after the wizzard, and some more terminal copy paste action i got this one:

URL: [http://paste.ubuntu.com/1054798/](http://paste.ubuntu.com/1054798/)




Soooo

because i dont know anything about gpt or efi... i went into wikipedia and read something about new version of mbr and so on... and then after all i checked the bios... well i went to Startup -> UEFI/Legacyboot and changed to legacy only.... then the next time it still did not find the operating system, but this probably comes because i messed up somthing durring my trys with boot repair and gparted.... but now.. when i boot from the linux dvd i get the usual menu like i know and i know also can choose to use the hardrive to boot.. and it works i can boot the old system... the message "no prefex is found or set" dissapered

i want to get a new hdd next week anyway so i am happy with this now...

summary:

it seems to be highhly recommended to check the UEFI/Legacyboot Option / Startup Menu in those Bios (Lenovo) and change them to "legacy only"... no boot repair tool can change something about the bios settings, so there was no problem with grub and there was no need to mess up the systempatitions and so on... all it was, ist this one stupid bios option, i have never heard of before

srz for my bad english

---


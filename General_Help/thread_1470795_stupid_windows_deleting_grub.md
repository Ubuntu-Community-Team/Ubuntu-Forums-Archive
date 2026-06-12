---
title: "stupid windows deleting grub"
date: 2010-05-03
forum: General Help
---

### Post by dd1linux on 2010-05-03
I run 3 OS's:  Win vista, win 7, and ubuntu.  Every month I reinstall windows 7 (because I dont have a key), and everytime I do that it reinstalls the MBR.  After that, I cant access ubuntu.  I have used live cd's to try and reinstall grub with no sucess.  What is the easiest way to achieve this?  I was hoping I could make a CD to pop in my computer that could reinstall grub as it should be, or atleast boot me into ubuntu, and work from there.  But even if I get into ubuntu, I dont know the commands to reinstall grub with autodetect of the other OS's.  I have fixed this problem before, but now I cant remember what I did.  Any help would be greatly appreciated.

---

### Post by colorlessprism on 2010-05-03
this is what you need to know:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by dino99 on 2010-05-03
what the problem is:

- every time you reinstall windows, the boot loader is reinstalled too
 ( i dont know how many hdd you have but let say windows install its bootloader on the 1st hdd on the 1st parttion (default))

- when you have installed ubuntu i suppose you have let the installer install grub by default, ie the same place than windows, here is the problem.

what to do: grub have to be installed on the ubuntu mbr partition
ie : if ubuntu installed on /dev/sdc1, install grub on /dev/sdc

Now you have to boot ubuntu with a cd or usb stick (unetbootin), then into console: grub-install to choose the good place, then:

sudo grub-mkconfig && update-grub

---

### Post by john newbuntu on 2010-05-03
I am assuming that you are using grub as your default bootloader.

Once you fix the MBR as pointed out in the link by Colorless prism, what you could do is to boot into windows and backup the mbr from windows to an external media.  You can then restore it from there (assuming that you do not modify any of the partitions).  There is a utility that you can download in windows mbrwiz that will help you in creating and restoring mbr.

---

### Post by dd1linux on 2010-05-03
@ colorlessprism:  thanks for the link, it looks very helpful and I will TRY that next time I re-install win7, but it looks very complicated (I'm a noob)


@dino99: Yours was the method I had used previously. I only have one HD, with about 6 partitions.  I tried your method, but didnt know what my HD was referred to (/dev/sdc .. etc.) so I kept getting errors. What is the command to list the devices/partitions?  I thought it was lspci, but thats not giving me what I wanted.

@john: I like your idea, I will try that one first next time I re-install win7

Thank you everyone for the quick replies, but I may be back in about 26 days, lol.

---

### Post by spiky001 on 2010-05-03
```
sudo fdisk -l
```

---

### Post by dd1linux on 2010-05-03
THAT was it! thanks spiky

---


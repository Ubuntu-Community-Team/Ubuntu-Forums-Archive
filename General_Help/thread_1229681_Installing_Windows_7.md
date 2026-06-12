---
title: "Installing Windows 7"
date: 2009-08-02
forum: General Help
---

### Post by tom.swartz07 on 2009-08-02
Hey everyone,

As crazy as it sounds, I would like to try Windows 7 on my system. I already have Vista and Jaunty in dual boot, and I have used gParted to open up a 12-15gb unallocated space on my harddrive. The main problem is that I do NOT have a DVD drive, although I do have a 4gb thumb drive.

I have the .iso file and I have followed the instructions on [http://www.thaivisa.com/forum/Install-Windows-7-Windows-Vista-t232522.html ]("http://www.thaivisa.com/forum/Install-Windows-7-Windows-Vista-t232522.html")I run into trouble when I must copy the .iso on to the drive. For some reason or another, my system will not navigate to the Boot Folder, and complete the task. Is there something that I am doing wrong?

Does anyone have any tips to get windows 7 on my system without corrupting any of my other partitions?

I have already tried using uNetbootin and the Ubuntu usb startup drive creator, both to no avail. 

Thanks!

---

### Post by Sidewinder1 on 2009-08-02
From everything that I have read, if you install a winbloze OS *after* ubuntu, you will bork GRUB and loose your ability to multi-boot. (Thank-you very much Micro$oft). The good news is that GRUB can be repaired after the fact. Search for "repairing GRUB after windows installation".
HTH,
Side

---

### Post by tom.swartz07 on 2009-08-02
Thanks for the tip sidewinder,

I'll keep it in mind. Does anyone know how well windows 7 works in virtual with iTunes?

---

### Post by Roberticus on 2009-08-02
> **Sidewinder1 said:**
> From everything that I have read, if you install a winbloze OS *after* ubuntu, you will bork GRUB and loose your ability to multi-boot. (Thank-you very much Micro$oft). The good news is that GRUB can be repaired after the fact. Search for "repairing GRUB after windows installation".
HTH,
Side
OR he/she could install EasyBCD on either Win 7 or Vista and add Ubuntu to Windows Bootlist.
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by mike555 on 2009-08-02
I'm running Windows 7 in vitualbox and it runs pretty good , you should get vitualbox from their site because it has better usb support ........

---


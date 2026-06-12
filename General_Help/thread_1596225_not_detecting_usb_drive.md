---
title: "not detecting usb drive"
date: 2010-10-14
forum: General Help
---

### Post by Rodayo on 2010-10-14
I'm a first time ubuntu user. I installed the system and I'm trying to transfer some songs onto my laptop with a usb drive. But when I pop it in I'm not getting any sort of alert like "media detected" and I don't know how to find it myself. 

I'm running Ubuntu 10.10 Netbook on an HP Mini if it helps.

---

### Post by garvinrick4 on 2010-10-14
I think it is under file manager or file browser on left hand side of window when opened. I am not in netbook right now but I do believe you will find it there. Open both windows
and drag and drop.

---

### Post by akoskm on 2010-10-14
> **Rodayo said:**
> I'm a first time ubuntu user. I installed the system and I'm trying to transfer some songs onto my laptop with a usb drive. But when I pop it in I'm not getting any sort of alert like "media detected" and I don't know how to find it myself. 

I'm running Ubuntu 10.10 Netbook on an HP Mini if it helps.

Does the USB icon appear on your desktop, or any new folder in /media?

---

### Post by garvinrick4 on 2010-10-14
> **akoskm said:**
> Does the USB icon appear on your desktop, or any new folder in /media? No it does not show on desktop just in the left side of the nautilus file system. Once it is mounted it should be in /media in the file system. The only difference is no icon on desktop but as long as it shows the little mark next to it when it is mounted in nautilus should make no difference.
Most likely easier if you give all your usb medium a label in gparted while not mounted or course so as to identify your partitions and medium simply.

---

### Post by earthmeLon on 2010-10-14
Remove your thumb drive.
Run dmesg | tail
Put your thumb drive in.
Run dmesg | tail

Tell us the new stuff that prints out.

Edit:
Also, you can try running gparted to see if your system identifies it as a drive, but hasn't/isn't able to mount it.

---

### Post by garvinrick4 on 2010-10-14
> **earthmeLon said:**
> Remove your thumb drive.
Run dmesg | tail
Put your thumb drive in.
Run dmesg | tail

Tell us the new stuff that prints out.

Edit:
Also, you can try running gparted to see if your system identifies it as a drive, but hasn't/isn't able to mount it. He is running the new Unity interface in Netbook and it is a bit different with no actual desktop. Nice once you get used to it.

---


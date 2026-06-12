---
title: "Lost UBUNTU option from dual boot system"
date: 2011-12-29
forum: General Help
---

### Post by vasant.bhusare on 2011-12-29
Hi,

I had Win7 and Ubuntu11.10 on my laptop with an dual boot option.Win7 was the primary(default) and Ubuntu was the secondary option.

But few days before I have removed some program named 'Ubuntu' from win7 control panel(Just because I feel it is not required) and from that time it is not showing me two options while booting:(.It boots into Win7.

Please suggest me how I get back the Ubuntu option?

Thank you in advance.

---

### Post by vpharry on 2011-12-30
Ok boot into your ubuntu live cd
Then we nee dto find out which partition ubuntu is installed. Type this: 
sudo fdisk -l
Then mount the partition:
sudo mount /dev/sda1 /mnt
Where "sda1" is the partition where you installed Ubuntu (or any other Linux distro). It could be "sda5", "sda6", etc. for you.
Then install grub to the partition mounted:
sudo grub-install --root-directory=/mnt/ /dev/sda
Finally boot into ubuntu(from your harddrive) and type:
sudo update-grub
Hope this helps

---

### Post by 2F4U on 2011-12-30
Was that a Wubi installation or did you dedicate a seperate partition to Ubuntu? I am wondering because usually you won't have Ubuntu in the Windows control panel.

---

### Post by vasant.bhusare on 2011-12-30
> **2F4U said:**
> Was that a Wubi installation or did you dedicate a seperate partition to Ubuntu? I am wondering because usually you won't have Ubuntu in the Windows control panel.

I have(actually had) a dedicated windows partition (E: drive) for the UBUNTU.
Yes. I feel the same (usually you won't have Ubuntu in the Windows control panel.) and hence I removed (uninstalled) it and now suffering:(.

---

### Post by vasant.bhusare on 2011-12-30
> **vpharry said:**
> Ok boot into your ubuntu live cd
Then we nee dto find out which partition ubuntu is installed. Type this: 
sudo fdisk -l
Then mount the partition:
sudo mount /dev/sda1 /mnt
Where "sda1" is the partition where you installed Ubuntu (or any other Linux distro). It could be "sda5", "sda6", etc. for you.
Then install grub to the partition mounted:
sudo grub-install --root-directory=/mnt/ /dev/sda
Finally boot into ubuntu(from your harddrive) and type:
sudo update-grub
Hope this helps


Thank You very much for the detailed and prompt reply...
My bad luck is that every time I have upgraded my Ubuntu online:(....and hence have no LIVE cd...
Anything that I can do from windows7....?:confused:

Will try to get LIVE cd meanwhile....

---


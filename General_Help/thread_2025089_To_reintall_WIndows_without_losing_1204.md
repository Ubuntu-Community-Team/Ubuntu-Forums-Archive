---
title: "To reintall WIndows without losing 12/04"
date: 2012-07-14
forum: General Help
---

### Post by Jayhawker on 2012-07-14
Is there a way to save my 12/04 installed through wubi in WIndows when the latter is failing. I can enter into Ubuntu, but not into Windows. If I install Windows again I'll lose Linux Ubuntu and I wouldn't want that occurs. 

Do you know how to reintall WIndows without losing 12/04?

Thanks a lot.

---

### Post by Cheesemill on 2012-07-14
You need to back up the root.disk file which is the virtual drive which contains your entire Ubuntu installation (I think it's located in C:\ubuntu\disks\).

Once you have reinstalled Windows you then do a fresh Wubi installation. Once this is done simply replace the new root.disk file with the one that you've backed up previously.

If you can't boot Windows then you'll have to boot from a Live CD to make the backup.

---

### Post by Jayhawker on 2012-07-15
Thanks for your help and attention. Must this back-up be reloaded in Windows, or rather in the Linux reinstalled, through File System/host/ubuntu/disk?

Thanks again  

> **Cheesemill said:**
> You need to back up the root.disk file which is the virtual drive which contains your entire Ubuntu installation (I think it's located in C:\ubuntu\disks\).

Once you have reinstalled Windows you then do a fresh Wubi installation. Once this is done simply replace the new root.disk file with the one that you've backed up previously.

If you can't boot Windows then you'll have to boot from a Live CD to make the backup.

---

### Post by ranger1021994 on 2012-07-15
Hope this helps :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Install Windows normally and boot into live CD.
Boot-repair :
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair
Now run boot repair

---

### Post by Cheesemill on 2012-07-15
> **ranger1021994 said:**
> Hope this helps :

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Install Windows normally and boot into live CD.
Boot-repair :
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair
Now run boot repair
None of this will work for a Wubi installation.
> Must this back-up be reloaded in Windows, or rather in the Linux reinstalled, through File System/host/ubuntu/disk
From Windows. You don't even need to boot the fresh Wubi installation first.
All the Wubi installation is doing is adding a boot option for the root.disk file to Windows.

---

### Post by YannBuntu on 2012-07-18
> **Cheesemill said:**
> None of this will work for a Wubi installation.

+1
I added a note at the top of the Community Wiki page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
and created this tutorial:
[https://help.ubuntu.com/community/ReinstallWindowsWithoutLosingUbuntu](https://help.ubuntu.com/community/ReinstallWindowsWithoutLosingUbuntu)

Don't hesitate to improve it.

---

### Post by Hungry Man on 2012-07-18
If you have a LiveCD it's simple. Use gparted to create your free space partition. Install Windows to that.

After that:
1) Boot into LiveCD

2) Open up root terminal

3) mkdir /mnt/tmp

4) mount /dev/sda1 /mnt/tmp

5) grub-install &#8211;root-directory=/mnt/tmp /dev/sda

6) Boot into Ubuntu and run update-grub

where SDA is you want grub installed.

I just did this yesterday.

---

### Post by Cheesemill on 2012-07-18
> **Hungry Man said:**
> If you have a LiveCD it's simple. Use gparted to create your free space partition. Install Windows to that.

After that:
1) Boot into LiveCD

2) Open up root terminal

3) mkdir /mnt/tmp

4) mount /dev/sda1 /mnt/tmp

5) grub-install &#8211;root-directory=/mnt/tmp /dev/sda

6) Boot into Ubuntu and run update-grub

where SDA is you want grub installed.

I just did this yesterday.
Don't do this, it will wipe your Ubuntu installation !!!

If you had a normal dual boot it would work fine but as you are using WUBI you have to take the steps I outlined in my post #2 above.

[SIZE=3] Before anyone else starts mentioning boot-repair, **please** take note that this is a WUBI installation not a normal dual boot.
Reinstalling Windows without backing up the root.disk file would also wipe Ubuntu.
Any attempt to use boot-repair or to install grub would also leave the system unbootable
See post #2 for the correct procedure :)
[/SIZE]

---

### Post by YannBuntu on 2012-07-18
_@all:_ **what would wipe Ubuntu here is neither Boot-Repair nor GRUB, but the fact to remove or reinstall Windows when Ubuntu is located INSIDE this Windows** (because it has been installed via Wubi).

_@Cheesemill:_ installing GRUB in the MBR would indeed leave the system unbootable, but using Boot-Repair would not.

---

### Post by Jayhawker on 2012-07-25
Thanks a lot. So, if I install WIndows and then again Linux Ubuntu by WUBI, and change the root.disk placing instead the one from my old 12/4 installed before, it will show up all my previous linux ubuntu. Am I right?


> **Cheesemill said:**
> Don't do this, it will wipe your Ubuntu installation !!!

If you had a normal dual boot it would work fine but as you are using WUBI you have to take the steps I outlined in my post #2 above.

[SIZE=3] Before anyone else starts mentioning boot-repair, **please** take note that this is a WUBI installation not a normal dual boot.
Reinstalling Windows without backing up the root.disk file would also wipe Ubuntu.
Any attempt to use boot-repair or to install grub would also leave the system unbootable
See post #2 for the correct procedure :)
[/SIZE]

---


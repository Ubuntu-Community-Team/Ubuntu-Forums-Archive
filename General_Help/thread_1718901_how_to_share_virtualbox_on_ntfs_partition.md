---
title: "how to share virtualbox on ntfs partition"
date: 2011-04-01
forum: General Help
---

### Post by lindevox on 2011-04-01
Hi,
I've setup my PC using ubuntu 10.10 (desktop) as follows:

1. On my system, I Have 2 user account. One is Administrator, another is User.
2. create an NTFS partition (/dev/sda3) on the system.
2. install virtualbox-4.0 using Administrator account.
3. Install windows7 on virtualbox using Administrator account.
4. The windows7.vdi is located in the NTFS partition.
5. I try to login as user, and mount the NTFS partition in which the windows7.vdi resides, but it prompt me to enter Administrator password not the user password. 

Question:
1. How to change the permission permanently on the NTFS partition so that both administrator and user can mount it when they login to their account.
2. How to share windows7.vdi to the user.

Any Help Please?

---

### Post by anglican on 2011-04-01
> **lindevox said:**
> Hi,
I've setup my PC using ubuntu 10.10 (desktop) as follows:

1. On my system, I Have 2 user account. One is Administrator, another is User.
2. create an NTFS partition (/dev/sda3) on the system.
2. install virtualbox-4.0 using Administrator account.
3. Install windows7 on virtualbox using Administrator account.
4. The windows7.vdi is located in the NTFS partition.
5. I try to login as user, and mount the NTFS partition in which the windows7.vdi resides, but it prompt me to enter Administrator password not the user password. How are you trying to mount the ntfs partition? Could you supply the exact command and error that you're getting please.

> **lindevox said:**
> 
Question:
1. How to change the permission permanently on the NTFS partition so that both administrator and user can mount it when they login to their account.
2. How to share windows7.vdi to the user.

Any Help Please?In ubuntu linux the user should be able to run the mount command using sudo i.e. ```
sudo mount /dev/sda3 /mount/point
```for which you will need to give user's password. To make the mount permanent, put it in /etc/fstab. Permissions on an ntfs partition are not relevent, everything will belong to root and have 777 permissions as ntfs can't handle linux's more fine-grained ownership and permissions.

H

---

### Post by lindevox on 2011-04-01
Quote:
How are you trying to mount the ntfs partition? Could you supply the exact command and error that you're getting please.

Fisrt Setup Attempt:
Previously I install Ubuntu 10.10 desktop version on my 250GB hd using default partition setting provided by the installer. Also create another USER for testing purpose. So I have a root account and a USER. Both have different password.

Then,I installed win7 under VB and get warning from VB that suggest me to install win7.vdi on a seperate partition but I just ignore it and continue the installation. It went successfully. As root, I can run win7 from VB without any problem.

But then I was thinking of If I could just share the Win7vdi create by root to the user without the need to create another win7.vdi, thus it will save space on my hdd.

Then I logout from root and login as USER and run VB. VB shows only New Button. I Click it and pointing VB to the location where win7.vdi resides which is in the /home/root/.virtualbox/win7.vdi.

It fails to open because win7.vdi belongs to root while I logon as USER.

That's my first attempt.

The Second Attempt:
I boot my PC using ubuntu 10.10 USB Stick, and resize partition leaving 100 GB and set it as NTFS.

Login as root, install VB & Win7 on NTFS, everything's ok.

login as USER, when I select the NTFS partition( I label the partition as win7drive) from Places-> win7drive, ubuntu pop-ups authentication and asking the USER to enter root (administrator) password. ofcourse I don't want this to happend, because it is imposible for root to type neither give its password every time the USER want to access the NTFS partition.

Quoted:
for which you will need to give user's password. To make the mount permanent, put it in /etc/fstab. Permissions on an ntfs partition are not relevent, everything will belong to root and have 777 permissions as ntfs can't handle linux's more fine-grained ownership and permissions.

my question is:
1. How to grand the USER to access the NTFS partition (win7drive) using his password (not the root password).
2. how to modified the fstab things? could you please explain in details 'cos i'm just a newb in linux world...:)
3. suggested to change ntfs partition to linux partition (ext2,3 or 4), will I have to deal with setting up file access permission for users when they want to share files? FYI: I have 50+ users and all aren't familiar with linux. That is why it keeps us using windows rather than linux because I'am affraid it will cause big problem to our daily job activities.

Big Thanks to You anglican!

---

### Post by lindevox on 2011-04-01
Got it Solved!

I just went tru here:
[http://ubuntuforums.org/showthread.php?t=1434702]("http://ubuntuforums.org/showthread.php?t=1434702")

and here:

[http://ubuntuforums.org/showthread.php?t=1435044]("http://ubuntuforums.org/showthread.php?t=1435044")

I change usr/share/polkit-1/actions/org.freedesktop.udisks.policy according to the posting above and VOILA....! when I logon as USER and mount the partition, Ubuntu didn't ask for the root password.

Cheers!

---


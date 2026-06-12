---
title: "How to share a USB drive"
date: 2012-08-26
forum: General Help
---

### Post by RedRat on 2012-08-26
I have a Seagate Freeagent 1.5Tb drive (NTFS) attached to my 12.04 Ubuntu machine. This machine and another Mint Ubuntu (13) are all attached to my router, basically forming a network. I want my Mint machine to be able to access (R&W) that Freeagent drive. I have tried sharing it by right clicking on that drive as it appears on my desktop and then clicking on Properties. While I can go to the sharing tab and declare it shared, I cannot change its permissions! Every time I open the network on my Mint machine, it shows the drive as available but I cannot mount it. In Windows XP I could do this very easily.

How do I do this in Ubuntu?

---

### Post by user333 on 2012-08-26
You may need root access to do this. Try ```
sudo nautilus
``` and do the same thing.

---

### Post by RedRat on 2012-08-26
> **user333 said:**
> You may need root access to do this. Try ```
sudo nautilus
``` and do the same thing.
Tried that but it still does not allow me to change permissions. I cannot change "Owner" or "Group", cannot change any of the access methods, e.g., R&W.

There must be a way to do this.

---

### Post by user333 on 2012-08-26
What if you created a folder on the drive and changed it's permissions? You might have to change ownership of the folder first by using the chown command.

---

### Post by zero2xiii on 2012-08-26
Sigh,

Linux (ubuntu) ownerships does not apply to NTFS or FAT formats. Only root can share the drive and a folder on the drive.

Also, sudo nautilus will not work since [this]("http://askubuntu.com/questions/11760/what-is-the-difference-between-gksudo-nautilus-and-sudo-nautilus") and [this]("https://help.ubuntu.com/community/RootSudo") which is a more technical way to explain things.

Running gksudo nautilus however is VERY DANGEROUS. Read up on it first. Also consider alternatives to sharing an entire drive.

Cherz

---

### Post by RedRat on 2012-08-27
> **zero2xiii said:**
> Sigh,

Linux (ubuntu) ownerships does not apply to NTFS or FAT formats. Only root can share the drive and a folder on the drive.

Also, sudo nautilus will not work since [this]("http://askubuntu.com/questions/11760/what-is-the-difference-between-gksudo-nautilus-and-sudo-nautilus") and [this]("https://help.ubuntu.com/community/RootSudo") which is a more technical way to explain things.

Running gksudo nautilus however is VERY DANGEROUS. Read up on it first. Also consider alternatives to sharing an entire drive.

Cherz

Interesting. I understand that I should not share the root directory--in point of fact I do not want to do this. However this 1.5Tb drive has a collection of my music mp3s and I want another computer within my network to access these files. I also have photos that I want available to other computers in my home network. 


It appears that I cannot share the whole drive or any portion of that drive then. Is there any way to do this then???? I really do not want to setup a Windows XP machine and reconnect my FreeAgent drive back to that--that is a PITA to have to have another computer running and acting as a file server. There really must be a reasonable way to do this.

---

### Post by Morbius1 on 2012-08-27
On the machine that has the USB device:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section - right under the workgroup line:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your own login user name on this box*[/COLOR]
Then restart samba:
```
sudo service smbd restart
```
Wait a few minutes ( restarting samba drives the network crazy ) then try to access the shared drive.

When you plug in or turn on a USB drive it mounts to you with access only to you. Force user will make the remote user appear to be you for these shares.

---

### Post by RedRat on 2012-08-27
> **Morbius1 said:**
> On the machine that has the USB device:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section - right under the workgroup line:
```
force user = morbius
```[COLOR=Blue]*Change morbius to your own login user name on this box*[/COLOR]
Then restart samba:
```
sudo service smbd restart
```Wait a few minutes ( restarting samba drives the network crazy ) then try to access the shared drive.

When you plug in or turn on a USB drive it mounts to you with access only to you. Force user will make the remote user appear to be you for these shares.
Morbius1 that worked!!! Thanks! :p

---


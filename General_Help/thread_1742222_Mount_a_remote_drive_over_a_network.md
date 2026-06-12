---
title: "Mount a remote drive over a network"
date: 2011-04-28
forum: General Help
---

### Post by washable mist on 2011-04-28
in 10.10 Gnome i could use an option (i think it was connect to remote server or something) where i could mount a windows folder share or a samba share, Since upgrading to 11.04 i cannot find this option, has it been removed or hidden?

---

### Post by bobwyajnr on 2011-05-01
> **washable mist said:**
> in 10.10 Gnome i could use an option (i think it was connect to remote server or something) where i could mount a windows folder share or a samba share, Since upgrading to 11.04 i cannot find this option, has it been removed or hidden?

Are you afraid of the commandline? If not I highly recommend the **mount.cifs** command for mounting Samba folder (disk) shares. I can talk you through how to use it - if that would be useful.

It tends to be more useful than going through Nautilus or Dolphin (default Gnome and KDE file-managers) as you can directly specify the user name you want to use to access the share (I think Nautilus is quite keen to access shares as a *guest* account). Being familiar with it allows you to mount shares on any Desktop Manager (be it Gnome, Unity, KDE, LXDE, etc., etc.)

Bob

---

### Post by mn_voyageur on 2011-05-07
Bob,

It would be useful to me, if not washable mist.

I use cli on a regular basis.  

The remote machine is setup for share.  Sharing does require a password, if this changes anything.  It is a local network.  

For the sake of this lesson:
The desktop is: 192.168.2.100
The laptop is:  192.168.1.105
The drive on the desktop is: Laptop_1 

How do I get to the drive from my laptop?

Is it possible to automatically mount this drive when I connect to the network?  

I appreciate the help.

MarkN

---

### Post by Morbius1 on 2011-05-07
Are you not using Gnome?

```
nautilus smb://192.168.2.100/Laptop_1
```

It will bring up Nautilus at that location and automatically create a mount point at:

/home/your-user-name/.gvfs/laptop_1 at 192.168.2.100

---

### Post by bobwyajnr on 2011-05-07
> **mn_voyageur said:**
> Bob,

It would be useful to me, if not washable mist.

I use cli on a regular basis.  

The remote machine is setup for share.  Sharing does require a password, if this changes anything.  It is a local network.  

For the sake of this lesson:
The desktop is: 192.168.2.100
The laptop is:  192.168.1.105
The drive on the desktop is: Laptop_1 

How do I get to the drive from my laptop?

Is it possible to automatically mount this drive when I connect to the network?  

I appreciate the help.

MarkN

My CIFS share mounting BASH script goes like this:
```

#!/bin/bash
for cifs_share in "Laptop_1"
do
        sudo mkdir "/mnt/${cifs_share}/"
        sudo mount.cifs "//192.168.1.100/${cifs_share}/" "/mnt/${cifs_share}/" --verbose -o user='WINDOWS-USERNAME',password='*****',domain='WORKGROUP',rw,exec,noperm,uid=UNIX-USER-NAME,gid=UNIX-GROUP-NAME
done

```
I presumed that your machines are both on the same subnet and the 192.168.2. was a typo. Save the script in users home folder. Replace the capitalized words/**** with something sensible! UID/GID will be the  user/group that the share will accessed as remotely on the laptop (can be either specified as: text, code or one of each). Make the script executable. Run the script and enter your root password as required.

To automount a SMB share gets a bit fiddly - to the best of my knowledge. To all the experts am I right? It involves adding cifs/smb mount commands to the **fstab** file. Uhmmm not sure if that's a good idea for system stability. Haven't risked it myself yet! 

Anyway hope that helps! :popcorn:
Bob

---

### Post by mn_voyageur on 2011-05-08
I'll work on all of it.  

When I get fstab working, I'll let you know.

Thanks for the help.

MarkN

---

### Post by bobwyajnr on 2011-05-08
> **mn_voyageur said:**
> I'll work on all of it.  

When I get fstab working, I'll let you know.

Thanks for the help.

MarkN

I suppose if you remember (!) to backup the **fstab** file... If the worst comes to worst - you can always live boot any recent distro to restore the backup! :P

Bob

---

### Post by nothingspecial on 2011-05-08
Open nautilus, go to the top bar thingy and click file > connect to server

---


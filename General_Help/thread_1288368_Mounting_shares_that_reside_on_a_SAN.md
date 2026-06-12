---
title: "Mounting shares that reside on a SAN"
date: 2009-10-11
forum: General Help
---

### Post by Pelsia on 2009-10-11
I've been racking my brain like crazy trying to figure a way to mount shares that are on my SAN.  I'm not sure if its best to force them to mount via /etc/fstab, samba, or some other way.  Several hours of reading through forums/documentation has done more confusion than clarification; I'm hoping that there's a more clear cut way of achieving the task out there.  :confused:

The bad news is that the shares reside on a Windows 2003 server (the domain controller), and uses NTFS.  Unfortunately I don't have enough free disk space floating around to move the terabyte and change worth of data to reformat the SAN into NFS.  The machine that I need to do this on (mount the shares) is a laptop which is otherwise in fully functioning order.

The laptop is setup for dual boot with XP (there's still a couple of Windows only apps that I need for doing research) that don't have a comprable/compatible unix counterpart.  With the NTFS tool I know you can mount drives connected to the machine, in this case I could mount my XP partition.  Something I was wondering is if I mounted the XP partition, mapped all the shares while booted into XP, would they also show up in the Ubuntu NTFS tool and be mountable (creating a symbolic link in a sort of way)?  Since all this is being done within my own home security can be much more lax since only me and guests/friends that come over will be on the network.

I know that Samba is one way of dealing with this issue, but after reading its documentation and forum posts it became unclear if it needs to be installed on the server or client machine, or unix file services enabled on the windows server?  Bascially I've got contradictory information on how to properly do this and would appreciate any help with anyone that's done the same kind of operation.  I'm eager to shed all my Window machines and turn them into nice unix ones (save one for gaming :P) and this is the last big hurdle in the process.

---

### Post by noelvh on 2009-10-11
Well I am not sure if this will help, but I have never been able to get to my windows shares via samba. I just connect to server from with in Nautilus. I have a simple desktop with a hard drive shares out as a NAS. To day I wanted to do a permanent mount for this NAS drive. The easy way was to edit the fastab. I created a mount point.
```
sudo mkdir /media/MOUNTNAME
```

From there I edited my fstab and added this line to the end.
```
//SERVERNAME/SHARENAME  /media/MOUNTNAME  cifs  username=YOURUSERNAME,password=YOURPASSWORD  0  0
```
Replace all caps with your names. Now for me I was not able to use server name in the fastab so I user the ip address, as it is static and not DHCP. 

To test do a 
```
sudo mount -a
```
This will remount drives in the fstab file. 
This is not a very secrue way of doing this but it works. There is a way to have a file to supply your username and password but it did nto work for me. I will be looking to changing this but it is just on my home network so I don't really care.

I can not take credit for this info as I just looked it up. I can state that it worked for me.

I hope this will help.

Noel

---

### Post by Pelsia on 2009-10-11
In the past I'd tried mounting the shares via Nautilus but kept getting can't connect to smb://192.169.0.2.  Oddly enough this time just entering the ip allowed the shares to connect and mount.

Only problem is that since the network connection is wireless it fails to mount at bootup.  Is there a way to make Nautilus mount the shares after boot (and the wireless established), or for that matter a delay mount command that only executes after say 60 seconds (plenty of time for the wireless to connect)?  Thanks ^^

Edit:  Found a work around for the time being.  You can bookmark the network shares inside of Nautilus; then just click on them again after boot to remount them.

---

### Post by noelvh on 2009-10-11
I have no clue, but I can say this- my mount is done on a wireless laptop, and it works. I never thougt of this till you brought it up. I would have been a bumb *** if it failed for me. I will say this I have mounted it with Ubuntu 9.10 so I do not know if this is a factor or not. I also have my wifi connect on logon.

Noel

---

### Post by Pelsia on 2009-10-11
It'll be interesting to see if the mount handling is indeed different in 9.10, or if its just that you have your wireless to connect before mine.  Getting my wireless adapter to work was way harder than it had any right to be, waiting to see if it starts giving me problems before I change it to something like you have setup in order to automount the network shares.

---


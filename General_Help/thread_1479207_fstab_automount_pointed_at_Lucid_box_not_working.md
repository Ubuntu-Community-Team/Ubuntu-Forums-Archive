---
title: "fstab automount pointed at Lucid box not working"
date: 2010-05-10
forum: General Help
---

### Post by VanCardboardbox on 2010-05-10
I'm probably missing something noobishly obvious here. I recently did a fresh Lucid install on my main desktop box, which had previously been running Karmic. With Lucid I can no longer use fstab in my laptops to automatically mount the desktop's shared media drive. Using the mount command works fine. One laptop is running Karmic, the other is running Hardy. 

This is the line in fstab on both laptops:

```
//192.168.0.123/multimedia /media/multimedia cifs username=x,password=y 0 0
```

This is unchanged since the desktop was running Karmic, where auto-mounting from the lappys worked just fine. I've tried that same line substituting smbfs for cifs. smbfs is installed on the laptops. No go.

I can mount the shared drive just fine with the mount command:

```
sudo mount -t smbfs //192.168.0.123/multimedia	/media/multimedia

```
So, what am I missing, forgetting?

Thanks for any help.

---

### Post by Zorael on 2010-05-10
If you do **mount -a**, does it properly mount it then?

I'm just reminded of the **_netdev** fstab/mount option. From the man page;
```
**_netdev**
    The filesystem resides on a device that requires network access
    (used to prevent the system from attempting to mount these
    filesystems until the network has been enabled on the system).
```
Could it be that in Lucid your network connection is established too late, causing fstab to freak out and ignore the mount definition?

---

### Post by Morbius1 on 2010-05-10
Zorael, I too remember _netdev working and I have recommended it about 3 times on this forum. Unfortunate in all three cases it didn't work.

Putting a script in /etc/network/if-up.d to mount it and in /etc/network/if-down.d to unmount it apparently does:

[http://ubuntuforums.org/showthread.php?p=9226244#post9226244](http://ubuntuforums.org/showthread.php?p=9226244#post9226244)

If _netdev doesn't work you might give this a try.

---

### Post by VanCardboardbox on 2010-05-11
Thanks for the reply. The mount -a command resulted in a permission error:

```
mount error (13) : permission denied
```

If I use the mount.cifs command, however, the shared drive mounts just fine. Why would a permission error result from mount -a, but not mount.cifs or mount?

While I'd love to get to the bottom of this, I need to get things working. The script solution sounds good. I'll give that a try.

---

### Post by VanCardboardbox on 2010-05-11
Got the fstab to work on both laptops by removing user=*x* from the options and leaving only password=*y*:

```
//192.168.0.123/multimedia /media/multimedia cifs password=y 0 0
```

The username was entered correctly, so why should including it in the options result in a permission error? Same thing happens with mount or mount.cifs - including the username results in permission error.

Happy its working now, however!

---

### Post by maedox on 2010-05-12
Glad you got it sorted. For what it's worth, I have this in my fstab:

```
//server.domain.com/share  /home/username/shared       cifs    uid=username,credentials=/home/username/.credentials.cifs 0 0
```

In the .credentials.cifs file I have this:
```
username=
password=
domain=
```

Just add your credentials there, install smbfs and sudo mount -a should work.

---

### Post by nixIT on 2010-05-12
I am having a similar problem with the mounting in my fstab.  I can't copy anything from the server, it appears the copy just hangs.  I have to xkill the copy dialog box.  I've tried letting it attempt to complete, but after a couple hours of trying to copy a 120k file, I gave up.

All of this worked with Ubuntu 9.04, and I'm currently running Lucid.

my current fstab looks like this:

```

//192.1686.0.16/homedir /mnt/hdrive cifs credentials=/home/nixit/.creds 0 0
//192.168.0.16/c$ /mnt/shareroot cifs credentials=/home/nixit/.creds 0 0

```

From withing nautilus I can connect to the share via:

```

smb://192.168.0.16/homedir

```

and then I enter in my credentials and all is well, everything works.

The above did not work for me.

---

### Post by shaav on 2010-05-12
One more thing to double-check, especially if you can connect using nautilus: the ip addresses. I swapped out network cards on my machine with the shares and the dhcp reservation is of course attached to the *card* not the *computer*.  This was the error I was getting trying to connect to the wrong machine.

Coincidentally corresponded to upgrading to Lucid today so I assumed it was related to that change.

---

### Post by nixIT on 2010-05-13
have not made any network card changes, and the ip address of the server has been the same for 2 years.

I would like to find out what's causing this, as it's much easier to just open up nautilus and navigating to /mnt/<mounted drive name> as opposed to opening nautilus and having to log into the machine via SMB://... in the address bar.

--nixIT

---

### Post by maedox on 2010-05-14
Try adding uid=username, before credentials. username is your local username/uid who shall be the owner of the mounted files.

---

### Post by nixIT on 2010-05-14
Thanx, I have tried the following:

```

//192.168.0.16/homedir$ /mnt/hdrive cifs _netdev,iocharset=utf8,uid=1000,credentials=/home/nixit/.smbcredentials,file_mode=0777,dir_mode=0777 0 0
//192.168.0.16/c$ /mnt/fsroot cifs _netdev,iocharset=utf8,uid=1000,credentials=/home/nixit/.smbcredentials,file_mode=0777,dir_mode=0777 0 0

```

and


```

//192.168.0.16/homedir$ /mnt/hdrive cifs _netdev,iocharset=utf8,uid=nixit,credentials=/home/nixit/.smbcredentials,file_mode=0777,dir_mode=0777 0 0
//192.168.0.16/c$ /mnt/fsroot cifs _netdev,iocharset=utf8,uid=nixit,credentials=/home/nixit/.smbcredentials,file_mode=0777,dir_mode=0777 0 0

```

both don't seem to change anything, copying anything from the fileserver (the 2 mounted drives above) results in what appears to be a "stalled" copy progress window that needs to be "xkill"ed

do I have something wrong with the lines above?  I recently added the _netdev parameter, not sure what that does but some forum posts recommended on having it.

--nixIT

---

### Post by Zorael on 2010-05-14
As a sidenote, whenever you're able to make manual mounts and you're trying to make them permanent in fstab, but you're unsure of what options to set (perhaps **mount** applies some automatically that fstab doesn't), mount them normally and then check **/etc/mtab**. It lists current mounts in the same format that fstab wants them, so it's possible to directly copy and paste it into there.

This is of particular help when you want to mount a directory with escaped characters in them, like spaces. Instead of trying to manually construct your mount location string with spaces**\040**expressed**\040**like**\040**this, just mount it easily with quotes and then copy the definition from mtab to fstab.

---

### Post by nixIT on 2010-05-14
I appreciate the info, and I tried mounting manually,

```

sudo mount -t cifs //192.168.0.16/c$ /mnt/fsroot -o credentials=/home/nixit/.smbcredentials,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

```

and when I try to copy a file FROM the fileserver (/mnt/fsroot) to either my desktop (or anyone on my hardrive) or another network folder the copy dialog comes up and just stays up, never goes away.

So, not sure what changed in the way this is handled from 9.04 to 10.04 Ubuntu.  Also, not sure why the copy works fine when I open nautilus and connect to the drive with "smb://..."

is there a way to view how nautilus is mounting the fileshare?

--nixIT

---

### Post by Schnitty on 2010-05-17
i think i have a similar problem - if not, tell me and i'll search elsewhere.  i made no changes from 9.10 to 10.04, but when i did the upgrade, now that mappings i had in fstab no longer auto-mount. there's no reason that should have stopped working - everything in my network is the same and i can manually mount -a and everything seems to work like it did before.

what changed with 10.04 that would break the smbfs setup i had before?

---

### Post by Morbius1 on 2010-05-17
Schnitty,

I believe your situation is different than the original posters. You might want to look at: [http://ubuntuforums.org/showthread.php?p=9226244#post9226244](http://ubuntuforums.org/showthread.php?p=9226244#post9226244)

The problem appears to originate from Ubuntu's desire to boot as quickly as possible. It's booting so fast that the mount instructions in fstab are being executed before the network is up. The link above shows how to set up mount instructions in a script and run them at automatically after the network is up. You'll also have to set up scripts to unmount them when the network goes down and before shutdown.

---


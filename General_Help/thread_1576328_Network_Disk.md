---
title: "Network Disk"
date: 2010-09-17
forum: General Help
---

### Post by jodlajodla on 2010-09-17
Hello!
I have a question about network disk, which I need for documents, photos, music, ... 

I've done the NTFS partition which have 20GB storage and now I need solve for network disk. This disk need to will be showed on Windows and Linux OS, and all users in our network needs to copy and paste files. 

Thanks! :)

---

### Post by Fafler on 2010-09-17
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by jodlajodla on 2010-09-17
Thanks! But which chapter I need to follow?

I also need to start disk automatically at startup - on my (admin) account and also on (custom, user) account.

---

### Post by Morbius1 on 2010-09-17
I'm mildly confused ( which it pretty much my natural state ). Is this disk an internal disk that you're trying to share to the network or an external disk, or a NAS disk.

And by automount do you mean as a remote share by a client machine or do you mean as a partition on your own machine?

---

### Post by jodlajodla on 2010-09-17
Yes, I mean only partition ;) Thanks!

---

### Post by Morbius1 on 2010-09-17
_To automount an NTFS partition use the following as a template:_

*STEP 1: Find out how your system sees the partitions:*
```
sudo blkid -c /dev/null
```You should get a lising that looks something like this:
> /dev/sdc1: LABEL="BACKUP" UUID="66E4DC83E4DC56C1" TYPE="ntfs" *STEP2: Create a mount point for that partition to live in:*
```
sudo mkdir /media/Data
```*STEP 3: Edit fstab as root:*
```
gksu gedit /etc/fstab
```Add a line to fstab to automount that partition:
```
/dev/sdc1 /media/Data ntfs defaults,nls=utf8,umask=000,uid=1000 0 0
```*[COLOR=Blue]EDIT: The above line was edited to include correct mount point.[/COLOR]*

Save the file, exit gedit, and back in the terminal type:
```
sudo mount -a
```See if you can access /media/Data

_To share that partition across your network, I would suggest this Samba method first:_

Open Nautilus ( your Home folder )
Right click on /media/Data
Select "Sharing Options"
[COLOR=Blue]* It will ask you if you want to install Samba ( it calls it Windows Networking ) - you do*[/COLOR]
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
[COLOR=Blue]* It will ask you if you want it to modify permissions - you do.*[/COLOR]
Done

---

### Post by jodlajodla on 2010-09-17
I can't access to the partition... -.-" I copy this in terminal > sudo mount -aand I get fail
> fuse: failed to access mountpoint /Data: No such file or directory 
I only change sdc1 to sda3 in step 3 (when adding a new line to file).
How can I solve this? 

Thanks! :)

---

### Post by Morbius1 on 2010-09-17
> fuse: failed to access mountpoint /Data: No such file or directory                      That's because I'm an idiot.:oops:

Step 3 should have read:
```
/dev/sdc1 /media/Data ntfs defaults,nls=utf8,umask=000,uid=1000 0 0
```

---

### Post by jodlajodla on 2010-09-17
Disk is automounted, but I can't find media/Data in my home dir or anywhere else. Can I only do the directory on this disk and then I share it? Will be same effect? 

Thanks! :)

EDIT: I found it :) xD Thanks! :)

---

### Post by jodlajodla on 2010-09-17
Now I have only question how to be this partition showed on Windows computers?

Thanks! :)

---

### Post by Morbius1 on 2010-09-17
That's what all this was about in my earlier post:
> 
_To share that partition across your network, I would suggest this Samba method first:_

Open Nautilus ( your Home folder )
Right click on /media/Data
Select "Sharing Options"
[COLOR=Blue]* It will ask you if you want to install Samba ( it calls it Windows Networking ) - you do*[/COLOR]
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
[COLOR=Blue]* It will ask you if you want it to modify permissions - you do.*[/COLOR]
Done

---

### Post by jodlajodla on 2010-09-17
Yes, yes ;) But I think for Windows - where on OS Win I need to open this "network disk" now? (On Ubuntu I've finished for now)

---

### Post by Morbius1 on 2010-09-17
I'm not in front of a Windows machine at the moment but I think it's called "Network Neighborhood".

---

### Post by jodlajodla on 2010-09-17
Yes, I need to change option in smb.conf file. I need to change WORKGROUP to default Windows group in our network. 

Thanks for all!!! :)

---

### Post by Morbius1 on 2010-09-17
```
gksu gedit /etc/samba/smb.conf
```Find the line in the [global] section that looks like this:
> [global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
    [COLOR=Blue]workgroup = workgroup[/COLOR]Change the second "workgroup" to whatever you want. 

Then save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```

---

### Post by jodlajodla on 2010-09-17
Thanks! :)

Now is my problem solved ;)

---


---
title: "Which File System"
date: 2010-12-20
forum: General Help
---

### Post by lucast on 2010-12-20
Hi,

I need some help to pick a filesystem.  I am running Windows XP 64bit Professional and Ubuntu 10.04 (dual boot).

I have an internal 500gb drive that I want to use between the two systems and I need to choose a file system.

In the past I have used NTFS but I have noticed recently that some files have become corrupt.  I have also had quite a few problems sharing my NTFS drive using SAMBA as read and write (ended up having to modify FSTAB)

I decided to go with FAT32 until I realised that files (Video files) larger than 4gb can't be stored under FAT32.

I researched this and changed to ExFat (Fat64) and this is now fine under Windows except Ubuntu doesn't seem to recognise it.

So can anyone help.

I need a filesystem that I can share files between windows XP x64 and Linux, supports large files and partitions, and can easily be shared on my home network Read/Write using Samba in Ubuntu without having to edit config files.

---

### Post by Grenage on 2010-12-20
For cross-platform, I recommend NTFS.

---

### Post by BlueSpecial on 2010-12-20
> **Grenage said:**
> For cross-platform, I recommend NTFS.

+1. Agree 100%.

---

### Post by lucast on 2010-12-20
Hi,

Well yes, but I always seem to have trouble sharing NTFS via Samba.  I have now found a solution but it always means modifying FSTAB.

Also after some research I read that FAT tends to be more reliable in Linux than writing to NTFS. I have found some corrupt files recently and im not sure why.  I thought it might be the fact im writing to NTFS from Linux.  After running ScanDisk I found that I often have registry problems after using Ubuntu.

Regardless of that can you recommend another filesystem with full support in Linux and Windows which isn't FAT32 or NTFS?

---

### Post by karthick87 on 2010-12-20
+1 on post #2

---

### Post by cascade9 on 2010-12-20
EXT2/3 work (and I think 4 works now as well).

---

### Post by Grenage on 2010-12-20
> **lucast said:**
> Hi,

Well yes, but I always seem to have trouble sharing NTFS via Samba.  I have now found a solution but it always means modifying FSTAB.

Also after some research I read that FAT tends to be more reliable in Linux than writing to NTFS. I have found some corrupt files recently and im not sure why.  I thought it might be the fact im writing to NTFS from Linux.  After running ScanDisk I found that I often have registry problems after using Ubuntu.

Regardless of that can you recommend another filesystem with full support in Linux and Windows which isn't FAT32 or NTFS?

I believe that there is an EXT3 'patch' for XP, which gives support but I've never used it.

I've probably used over 400 NTFS internal, esata, and USB drives on Ubuntu in the last couple of years, and I've yet to experience any random corruption.  In your position, I'd probably give the disc a check.

---

### Post by BlueSpecial on 2010-12-20
True for me also. I usually download a lot thru Ubuntu saving the files (some with 6/7 GB) **_directly_** to a NTFS formatted external drive and I never had corrupted files.

---

### Post by lucast on 2010-12-20
Ok :-)

Then one more attempt with NTFS it is then.

Out of interest, what is the best way to share NTFS folders using Samba?

I did start a post quite some time ago and my result was that I had to change the way the drive was mounted in FSTAB to look something like this:

```
UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```

I also have to modify smb.cof and change this line:
```
'usershare owner only = False' 
```
Is there an easier way to do this now in a GUI ?

---

### Post by Grenage on 2010-12-20
> **lucast said:**
> Ok :-)

Then one more attempt with NTFS it is then.

Out of interest, what is the best way to share NTFS folders using Samba?

I did start a post quite some time ago and my result was that I had to change the way the drive was mounted in FSTAB to look something like this:

```
UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```

I also have to modify smb.cof and change this line:
```
'usershare owner only = False' 
```
Is there an easier way to do this now in a GUI ?

I usually use ntfs-3g, so for me:

```
UUID=947C603B7C6019EE /windows/D      ntfs-3g    defaults 0       0
```

I also find that you can share entirely by the GUI, by right-clicking on the folder and using the *share* options.

---

### Post by lucast on 2010-12-20
Great,  then I will try this and see how it goes.  Thank you for all your help.

---

### Post by Morbius1 on 2010-12-20
Some thoughts about possible NTFS file corruption. The line you added to fstab:
>  UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8,umask=007,gid=46 0       0This is exactly how Ubuntu would create the line in fstab had you told it to do so during the initial install using the manual partitioning option. 

There's only one problem with it and it's that it doesn't preserve time stamps properly: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9919254](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9919254) From a purists point of view that's file corruption. 

On way to circumvent the problem is to take possession of the mount point by adding uid=1000 to fstab so that your line looks like this:
```
UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8,uid=1000,umask=007,gid=46 0       0
```[COLOR=Blue]*BTW, that would have eliminated your need to use "'usershare owner only = False'"*[/COLOR]

Another way is to let root be the owner of the mount point but allow everyone to read and write not just members of gid=46. Your line in fstab would then look like what Grenage suggested. 
[COLOR=Blue]*And then you would have to add the "usershare owner only = False" option to smb.conf*[/COLOR]

---

### Post by lucast on 2010-12-21
Hi Morbius1.

I just tried what you suggested and it allowed me to add the share to a folder on this NTFS drive.

I then went to my windows computer which is on the same network and I can see the share.

When I try and access the share from Windows it says Permission Denied.  Any idea how to fix this? ( I am running Windows XP Professional x64)

Thank you for your help.

Tim

---

### Post by Morbius1 on 2010-12-21
It sounds like Linux file permissions and Samba authorizations are not in sync. If you have your nautilus-share set up to allow guest access for example then it won't work since the only users allowed access are uid=1000 and member of gid=46 and "guest" are nether of those. 

There are two ways around this:

[1] Modify the line in fstab one more changing your umask to 000 so that it looks like this:
```
UUID=947C603B7C6019EE /windows/D      ntfs    defaults,nls=utf8,uid=1000,umask=000,gid=46 0       0
```Or if your using Grenage's line, add uid=1000:
```
 UUID=947C603B7C6019EE /windows/D      ntfs-3g    defaults,uid=1000 0       0
```Grenage's way is shorter ;)

[2] Add a line to smb.conf that will create a mask that converts all remote users to you -  at least as far as that share is concerned:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf:
```
force user = lucast
```[COLOR=Blue]*Change lucast to your actual login user name*[/COLOR]
Save the file and restart samba:
```
sudo service smbd restart
```

---

### Post by lucast on 2010-12-21
Perfect

This has now worked :-)

Thank you very much

---

### Post by Grenage on 2010-12-21
Morbius1, you know your stuff. :)

---

### Post by john1923 on 2010-12-21
Could your corrupted files be due to permissions problems, or diferences in the maximum file name length? 

I have run into both of these, but NTFS is still the best one to use.

---

### Post by Morbius1 on 2010-12-21
> **Grenage said:**
> Morbius1, you know your stuff. :)
If you knew how many times a day I still make mistakes - even on things I should just know by now - you wouldn't say that :lol:

---

### Post by lucast on 2010-12-21
I did have that problem with files named incorrectly or that were too long, but the files I am referring to were actually corrupt.

I have just opened another question to find out if its possible to find files where the name is too long or the characters will not work with windows.

---

### Post by areteichi on 2010-12-28
I was actually asking myself the same question.

Since I only use Windows in VirtualBox, I decided to stick to FAT32 for the most part and just created a small 50GB Ext4 partition for storing files greater than 4GB. This should do for me since I don't have very many large size files.

---


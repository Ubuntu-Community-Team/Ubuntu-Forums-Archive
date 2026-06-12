---
title: "Shares for Windows Media Center"
date: 2010-07-27
forum: General Help
---

### Post by primetime34 on 2010-07-27
I am having a really difficult time getting my Windows 7 computer and Ubuntu machine to talk to each other.  I see the folders in the network but on the Ubuntu machine it says it can't mount the drive from the other Ubuntu machine.  Also, when I try to network into the windows machine it asks for a username/password even though I didn't set it up to use a username/password.  Finally, the windows machine shows the Ubuntu shared folder (which is on an external hard drive) but when I double-click on it, it doesn't let me in....it just says that it can't get into the drive and then nothing....any help?

---

### Post by arrrghhh on 2010-07-27
I'm assuming you're using samba?  How did you configure it?  Did you setup a user/pass with samba?

Please see this doc on [samba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by primetime34 on 2010-07-27
I can see the windows shares on my ubuntu machine and access them.  However I cannot access the ubuntu share on either my windows 7 machine or my other ubuntu machine.  I can see the folder but it won't mount.  Obviously I am not setting something up right to host files on my Ubuntu machine.  Any help/direction for that part?  Thanks.

---

### Post by arrrghhh on 2010-07-27
> **primetime34 said:**
> I can see the windows shares on my ubuntu machine and access them.  However I cannot access the ubuntu share on either my windows 7 machine or my other ubuntu machine.  I can see the folder but it won't mount.  Obviously I am not setting something up right to host files on my Ubuntu machine.  Any help/direction for that part?  Thanks.

You... didn't answer my question.  Should I even ask if you read the link/document I posted?  I don't mean to be rude, but **please** go over that documentation I posted.  Then I can help you troubleshoot, because you will understand what you need/are looking at :D

---

### Post by primetime34 on 2010-07-28
Sorry...yes, I did read the document and I am using samba.  I installed smbfs, but that didn't change anything.  I've gone through the article twice and I'm still not sure which of the parts of the article I am supposed to be reading/using in order to share folders from my Ubuntu machine with my Windows 7 machine.  Thanks and sorry for the lack of earlier clarification.

---

### Post by arrrghhh on 2010-07-28
smbfs is for the client, and is deprecated.  Please look at the Samba Server Configuration, that's what you need to concern yourself with if you're sharing to Windows clients.  You need the samba **server** stuff.

[Here's](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html) another doc on troubleshooting Samba.  It was linked at the bottom of that other doc I sent...

---

### Post by primetime34 on 2010-07-28
Okay, almost there.  If I set a folder within my home folder (downloads for example) then everything works just fine.  However, the folder I want to share is connected to an external drive that I have connected to my Ubuntu machine.  That folder still won't open on the windows client, even though I have set it to share just like the downloads folder.  Is there some special setting because it is in a mounted location that I am missing?  Thanks.

---

### Post by primetime34 on 2010-07-29
Bump...I'm so close but can't figure out this last part.  Any help?

---

### Post by JustinR on 2010-07-29
I didn't read the posts above but the easiest way to configure SAMBA to allow full access to everybody is to install System-Config-Samba. its a GUI that allows you to configure your shares much easier than through command line.

Accessories > Applications > Terminal
```

sudo apt-get install system-config-samba

```

---

### Post by Morbius1 on 2010-07-29
Before you install anything else please post the output of the following commands:

```
net usershare info
``````
testparm -s
```

If the problem is the external drive, it's probably not a samba problem its a linux permissions problem. That's an easy fix if true.

---

### Post by Morbius1 on 2010-07-29
Well, Ive got to shut down for the day. I'm going to shoot from the hip and make the following assumption: The external hard drive if formatted in FAT32 or NTFS. If so then it will automount with the owner ( you ) having full read / write access but all other users will have none.

You may have told samba to allow guest access but samba can't change linux file permissions. One way around this problem is to mask the identity of the remote user to you so that Samba authorization and linux file permissions are in sync. To do that you need to add the following line to **/etc/samba/smb.conf**:

```
force user = morbius
```[COLOR=Blue]*Changing morbius to you own local login user name*[/COLOR]

Where you put that line depends on what method of samba sharing you're using - there are 2:

Samba Nautilus-share ( the output of net usershare info ). You create this samba share by going to Nautilus and doing a Right-click > Sharing Options. If this is the method you used then you need to put the line in the [global] section of smb.conf.

Samba Classic-share ( the output of testparm -s ). If this is the method you used then the best place is in the share definition section itself in smb.conf.

---

### Post by primetime34 on 2010-07-30
That did it...thanks!!!  I really appreciate it.

---


---
title: "Making a &quot;Simple Home file server based on ubuntu&quot; issue"
date: 2011-04-20
forum: General Help
---

### Post by andy1027 on 2011-04-20
Hi :)
 
I am making a simple file server on Ubuntu Server 10.10 or whatever it is, using this tutorial
 
[http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)
 
(Im currently on page three)
 
I have encountered a problem.
 
On the tutorial where it says "Install the Second Hard Disk" the command provided for it doesn't work.
 
I have don't know what to search for on help.ubuntu.com
 
Can someone help me on this
 
Also can someone send me a link leading to a range simple commands for ubuntu (like shutdown etc.)
 
Thanks :) All contibutions are appreciated.

---

### Post by Grenage on 2011-04-20
> **andy1027 said:**
> On the tutorial where it says "Install the Second Hard Disk" the command provided for it doesn't work.


You'll probably need to use:

```
sudo fdisk -l
```

*sudo* elevates your permissions to that of root (for that command).

EDIT:

Oh, I see the tutorial shows you how to set a root password and then stay logged in as root.  I wouldn't recommend that; I'd go as far as saying that's just a bad article.  If you have to read a tutorial, then you probably don't want to be logged in as root.

What exactly was returned, and 'didn't work'?

---

### Post by andy1027 on 2011-05-03
Just that the command wasn't found.

So what do I do now in order to continue in setting up what I set out to achieve?

I'm kinda stuck here :/ lol

So just to recap im stuck on [http://www.howtoforge.com/ubuntu-home-fileserver-p3](http://www.howtoforge.com/ubuntu-home-fileserver-p3)

number 8 (install the second hard disk) which is currently connected. :)

---

### Post by Grenage on 2011-05-03
The command wasn't found when you used the following?

```
sudo fdisk -l
```

That's an L, not a one.

---

### Post by Morbius1 on 2011-05-03
You're trying to mount partitions on a second disk right?

Post the output of the following command and tell us which one you want to mount:
```
blkid -c /dev/null
```

---

### Post by andy1027 on 2011-05-03
I inputted that but nothings happenin whatsoever

---

### Post by Morbius1 on 2011-05-03
Maybe you didn't enable a root account after all:
```
sudo blkid -c /dev/null
```

---

### Post by andy1027 on 2011-05-03
Ok I got it I logged out of administrator and logged back in as root.

I got the following after typing in that blkid thing:

[HTML]/dev/sda1:UUID="5b1e8094-70c7-496c-907d-2eacf10cb294" TYPE="ext4"
/dev/sda5: UUID="4cb30241-80d6-464f-81f8-bc8bd8e30aa7" TYPE="swap"
/dev/sdb1: UUID="EEACA9BFACA982A7" TYPE="nfts"[/HTML]

Phew! A lot of typing there lol

---

### Post by andy1027 on 2011-05-03
Ahh right well i didn't know that was a L lmao

Sorry about that

---

### Post by Morbius1 on 2011-05-03
So to follow th HowTo and bring it up to current standards add the following line to the end of fstab:
```
 UUID=EEACA9BFACA982A7 /media/store ntfs defaults 0 0
```Then run the following command to test for errors and mount the new partition:
```
sudo mount -a
```You don't need to chmod /media/store before the mount. Whatever permissions are on the mount point will be overridden by the fstab instructions.

[COLOR=Blue]**EDIT:**[/COLOR] You do need to create the mount point first though:
```
 sudo mkdir /media/store
```

---

### Post by andy1027 on 2011-05-03
Thanks for all your helo I will refer back to this when required in the future.

However I realised I made a mistake and have now fixed it

But can you please tell me what this means "^X" they want you to do it to exit editing the grub config file. But what hot key do I use? Thanks :)

---

### Post by Morbius1 on 2011-05-03
I'm shutting down for the day so I thought I would leave you with one piece of advice:

**Section 9: Configure Samba** is incoherent and will give you at least 2 errors - maybe 3:

[1] Change the path to include a leading /
> [hda public hard disk]
comment = Public Folder
[COLOR=Blue]**path = /media/store**[/COLOR]
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = no group[2] There is no samba daemon anymore so to restart samba:
```
sudo service smbd restart
```If for some reason it's wasn't started to begin with then start it:
```
sudo service smbd start
```[3] He has you adding a samba password for a user named "family":
> smbpasswd -a family But nowhere in this HowTo did he have you create a user named "family" so smbpasswd will fail. As it turns out he had you create a guest share ( public = yes ) that doesn't require any username or password so you can skip that step completely.

---


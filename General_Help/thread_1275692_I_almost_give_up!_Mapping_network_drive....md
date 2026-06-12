---
title: "I almost give up! Mapping network drive..."
date: 2009-09-26
forum: General Help
---

### Post by Frank14 on 2009-09-26
I cant connect to my NAS no matter what I do. Although I have no problems with any other computer and device in the house Ubunto can't "see" the NAS.
 
I go to places, connect to server. Enter the appropriate information and it just asks for the password, and when I enter the correct password it waits for a long time and I get an error message like this:
 
Cannot display location "smb://FS@n3200/public/"
 
Failed to mount windows share.
 
where FS is the username, n3200 the NAS name, and public the folder name.
 
Please help me.'
All my devices can see the NAS even my phone and xbox... what the heck is wrong!:confused:

---

### Post by scorp123 on 2009-09-26
> **Frank14 said:**
> Cannot display location "smb://FS@n3200/public/" And you are sure you got the "SMB" tools and what not installed? Can we see the output of this command please:

```
dpkg -l samba*
```

---

### Post by Cato2 on 2009-09-26
See the Samba mini HOWTO in my signature.  I had a similar problem (accessing share on Windows PC from an Ubuntu PC) with some fixes mentioned there - primarily installing winbind seemed to help.  Also you should install smbfs and cifs even though the latter is the most up to date one.

---

### Post by Frank14 on 2009-09-26
I got to admit that I am a complete linux n00b :) I try the thing you posted and get back.
 
Didn't expect to have problems with such a simple thing... not a great first experience with ubunto.

---

### Post by 3rdalbum on 2009-09-26
What if you put this into the Nautilus location bar:

```
smb://n3200/public/
```

Also make sure you don't have a configured firewall on the client Ubuntu machine; by default Ubuntu has an **un**configured firewall. If you have configured your firewall on Ubuntu try accessing the NAS through IP address rather than by computer name.

---

### Post by 3rdalbum on 2009-09-26
> **Frank14 said:**
> Didn't expect to have problems with such a simple thing... not a great first experience with ubunto.

Don't get discouraged. I tried connecting to my home server on Windows the other day... took me about ten minutes to figure out why it wasn't working, whereas I've never had troubles connecting on Ubuntu.

---

### Post by Iowan on 2009-09-26
[Here]("http://ubuntuforums.org/showthread.php?t=1169149") is another How-To for Windows sharing problems.

---

### Post by Cato2 on 2009-09-27
> **Frank14 said:**
> I got to admit that I am a complete linux n00b :) I try the thing you posted and get back.
 
Didn't expect to have problems with such a simple thing... not a great first experience with ubunto.

Actually I've often had problems with Windows networking, regardless of whether it's two Windows PCs, or a Windows and an Ubuntu PC - there are many configuration differences and various protocol versions...

---

### Post by simartem on 2009-09-27
I am not experiencing any problems with samba & windows & ubuntu. All i did was to configure /etc/samba/smb.conf with
> 
"wins support = yes"
"wins server = 192.168.1.4" (depends on your network config)
"workgroup = workgroup" (depends on your network config)


and i also added a line into /etc/hosts
> 
"192.168.1.4   mycomputer" (depends on your client name)


to resolve dns name each time i open ubuntu. I wish this helps.. It will be a good idea to restart everything after modifications.. (Reboot windows pc, reboot ubuntu also reboot your modem/router if possible).

---

### Post by Cato2 on 2009-09-28
If you don't have a Windows PC that acts as a WINS server (maybe that's a domain controller, not sure if an ordinary XP Home or Professional PC would do this), just install winbind on your Ubuntu PC.  See my signature for a link about this.

---


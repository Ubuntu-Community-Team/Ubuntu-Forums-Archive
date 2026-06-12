---
title: "Help mounting drive"
date: 2010-02-18
forum: General Help
---

### Post by reptilezone2002 on 2010-02-18
hi i hope this is the correct page to post this

im using ubuntu for last 2 years. in ubuntu 9.10 when i open my NTFS drives is allays ask the password from me.. is there any way around this or can u fix this in ur next release.. because its a real pain to enter the password every time i access the NTFS drives.. i want to completely replace windows but the web cam support for yahoo chat is not good still..

& Thank u

---

### Post by Barriehie on 2010-02-19
Post your /etc/fstab please.

---

### Post by Jackzor on 2010-02-19
> **reptilezone2002 said:**
> hi i hope this is the correct page to post this

im using ubuntu for last 2 years. in ubuntu 9.10 when i open my NTFS drives is allays ask the password from me.. is there any way around this or can u fix this in ur next release.. because its a real pain to enter the password every time i access the NTFS drives.. i want to completely replace windows but the web cam support for yahoo chat is not good still..

& Thank u

Search Ubuntu Software Center for ntfs config? (I think) And install that. It will do what you need.

---

### Post by Morbius1 on 2010-02-19
Doing it the old way really isn't that hard:

***Step 1: Get a list of your partitions***

Open **Terminal**
Type **sudo blkid -c /dev/null**

You will get among other things an output that looks like this:
> /dev/sda1: UUID="DA9056C19056A3B3" LABEL="WindowsC" TYPE="ntfs"***Step 2: Create a home ( mount point ) for your partition to live in:***

Open **Terminal**
Type **sudo mkdir /media/WinC**

[COLOR=Blue]*NOTE: The mount point can be anywhere. If it's in your /home or /media folders it will show up under "Places". If it's directly off "/" or /mnt it will not.*[/COLOR]

***Step 3: Create an entry in /etc/fstab that will automatically mount that partition at startup. Use the following example as a template: ***
```
/dev/sda1 /media/WinC ntfs defaults,nls=utf8,umask=007,gid=46 0 0
```This will mount an ntfs partition with owner = root and with permissions for all local login users ( gid=46) to read and write ( umask=007).

To edit fstab: 
Open **Terminal**
Type [B]gksu gedit /etc/fstab
[/B] 
Insert the line at the end of fstab. When you're done save the file, exit gedit, and back in the terminal type: **sudo mount -a**

---

### Post by reptilezone2002 on 2010-04-06
Thanks Guys for helping me ........

---


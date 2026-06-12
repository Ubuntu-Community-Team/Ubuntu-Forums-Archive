---
title: "Swapping files between partitions"
date: 2011-09-23
forum: General Help
---

### Post by Mike Jubow on 2011-09-23
If I run Ubuntu 11.04 on a partition with MS XP, how do I transfer files between the two systems. For example, take files that exist on XP and transfer them over to Ubuntu.

---

### Post by Sharang.d on 2011-09-23
> **Mike Jubow said:**
> If I run Ubuntu 11.04 on a partition with MS XP, how do I transfer files between the two systems. For example, take files that exist on XP and transfer them over to Ubuntu.

Mount your Windows partitions from Ubuntu.
Refer to the mount command and /etc/fstab on the forums/ubuntu wiki and google

---

### Post by ofnuts on 2011-09-23
> **Sharang.d said:**
> Mount your Windows partitions from Ubuntu.
Refer to the mount command and /etc/fstab on the forums/ubuntu wiki and googleNot sure if iit's still valid, but in the past, when you had two OSes installed each on a primary partition, they couldn't access each other's partition.

---

### Post by raja.genupula on 2011-09-23
No man , it will mount . 
try to mount it , if its not mounting and showing any errors then please post those errors here .

all the best .

---

### Post by coffeecat on 2011-09-23
> **Mike Jubow said:**
> If I run Ubuntu 11.04 on a partition with MS XP,

That's a bit unclear. How did you install Ubuntu? To its own separate partition, or as a wubi install inside the Windows partition?

If Ubuntu is on its own partition, simply open a Nautilus file browser - click on the home icon in the launcher. Your Windows partition will be listed in the left (Places) pane. If the partition has a label, it will be identified with that. If not, it will show the partition size. Simply click on it and the Windows partition will be automounted read-write and you will be able to browse to your Windows My Documents folder.

If you have wubi, open Nautilus and click on "File System" on the left and then open the host folder in the main pane. That's your Windows fileystem.

Be careful when browsing the Windows filesystem. Windows and Linux permissions are entirely different and it is possible to write to or delete system files that are protected in Windows. You can do great damage accidentally. Best not to open the "Windows" folder at all. You'll also see folders and files that are hidden in Windows.

---

### Post by rjbl on 2011-09-23
> **Mike Jubow said:**
> If I run Ubuntu 11.04 on a partition with MS XP, how do I transfer files between the two systems. For example, take files that exist on XP and transfer them over to Ubuntu.

What works for me, in 11.04 / XP SP3 on a dual boot; and on 10.04LTS on its own box; is simply plugging in one of my USB external HDD's. Both OS's see it as part of their own file systems and can read and write to it quite happily. 

Can't recall whether I formatted it as FAT or NTFS - it hardly seems to matter, although if you are really worried about access control you could easy stick a big Truecrypt virtual disk file on the external HDD. Truecrypt runs in GNU/Linux and in Windows.

Hope this helps

rjbl

---

### Post by Mike Jubow on 2011-09-23
> **rjbl said:**
> What works for me, in 11.04 / XP SP3 on a dual boot; and on 10.04LTS on its own box; is simply plugging in one of my USB external HDD's. Both OS's see it as part of their own file systems and can read and write to it quite happily. 

Can't recall whether I formatted it as FAT or NTFS - it hardly seems to matter, although if you are really worried about access control you could easy stick a big Truecrypt virtual disk file on the external HDD. Truecrypt runs in GNU/Linux and in Windows.

Hope this helps

rjbl

I haven't partitioned my wifes XP computer yet but this is one of the questions I would need to resolve before I do it. I was hoping that there was a method, for want of a better description, like Copy and Paste that you could do without burning a disc, transferring the file to an  external HD, etc.

Please explain what Truecrypt is and what do I need to buy.

---

### Post by raja.genupula on 2011-09-23
you can go here for complete idea about truecrypt 
[http://en.wikipedia.org/wiki/TrueCrypt](http://en.wikipedia.org/wiki/TrueCrypt)

all the best

---

### Post by Mike Jubow on 2011-09-23
> **raja.genupula said:**
> you can go here for complete idea about truecrypt 
[http://en.wikipedia.org/wiki/TrueCrypt](http://en.wikipedia.org/wiki/TrueCrypt)

all the best


Thanks everyone. I think I have enough for this old brain to be able to muddle through and have a good chance of running the show.

Thanks again.[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by raja.genupula on 2011-09-23
Hi
     We all hope that you got the right things for this issue .

---

### Post by Morbius1 on 2011-09-23
Is there some reason no one actually read coffecat's post.

If the OP truly dis this:
> If I run Ubuntu 11.04 on a partition with MS XPThen the answer is this:
> If you have wubi, open Nautilus and click on "File System" on the left  and then open the host folder in the main pane. That's your Windows  fileystem.If on the other hand he did what the title of this thread implies and actually installed Linux into it's own separate partition then a properly configured fstab entry for that partition will provide access control.

---


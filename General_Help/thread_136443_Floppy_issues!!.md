---
title: "Floppy issues!!"
date: 2006-02-26
forum: General Help
---

### Post by bfonseca on 2006-02-26
I swear I have tried everything to figure out my issue with the floppy.  I tried adding it to my fstab, tried sudo mknod --mode=0660 /dev/fd0 b 2 0 (the reason I did this is because for some reason under the /dev dir there was only fd/0 and fd/1 and so on.) I did notice that with the cdrom when I do a ls -l cd* there are links to the cdrom, I have no trouble with the cdrom. Here is what's going on: I restart then the fd0 I created with sudo mknod --mode=0660 /dev/fd0 b 2 0 goes away adn so everytime at bootup I have to do this again. 

the there is no link to the fd0 and I dont know if it needs one or not.  But either way nothing works. This has been driving me bonkers all day today. So decided to post it. I could use alot of help I have tried everything I can think of and I have read posts from others and still no luck. I am ready to give up here, need your help.
Brian

---

### Post by bfonseca on 2006-02-26
oh and another thing when I use the fdmount I get this:

fdmount (/dev/fd0): Can't access /fd0: No such file or directory

Brian

---

### Post by bfonseca on 2006-02-26
one more when I do mount /media/floppy0 i get:

mount: /dev/fd0: can't read superblock

---

### Post by pestilence4hr on 2006-02-26
(wild stab in dark)

modprobe floppy ?

---

### Post by bfonseca on 2006-02-26
thanks for your help, but unfortuanitly it is still not working here is what I did:

[PHP]
root@goofys-computer:/home/bfonseca# mount /mnt/floppy
mount: special device /dev/fd0 does not exist
root@goofys-computer:/home/bfonseca# mount /media/floppy0
mount: special device /dev/fd0 does not exist
root@goofys-computer:/home/bfonseca# modprobe floppy
root@goofys-computer:/home/bfonseca# mount /media/floppy0
mount: /dev/fd0: can't read superblock
root@goofys-computer:/home/bfonseca# mount /mnt/floppy
mount: /dev/fd0: can't read superblock
root@goofys-computer:/home/bfonseca# fdmount
fdmount (/dev/fd0): Can't access /fd0: No such file or directory
[/PHP]

any other ideas?
Brian

---

### Post by bfonseca on 2006-02-26
Thanks for your suggesting, however unfortunatly it didnt work.  What it did do though was it mad fd0 showup inside of the /dev.  All I had was fd/0 fd/1 .. and now I have fd and fd0 the problem is though that it says that the fd0 is not a valid fd0.

Any thought as to why that is?

Brian

---

### Post by pestilence4hr on 2006-02-26
Is the floppy formatted?  What happens if you try to format it before you mount it?

---

### Post by mlind on 2006-02-26
if you remove manually created /dev/fd0,
*sudo modprobe floppy* should create this node again.

then
*sudo mount -t vfat /dev/fd0 /media/floppy*

vfat could be *auto* aswell. If this works, fix your fstab accordingly.

---


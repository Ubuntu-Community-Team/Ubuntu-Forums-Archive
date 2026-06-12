---
title: "/home quota?"
date: 2006-04-12
forum: General Help
---

### Post by frup on 2006-04-12
i just tried copying over some files from another drive to back up to /home/username and i got a message saying not enough space... hda1 has 30gb free! whats going on here?

thanks

---

### Post by nanotube on 2006-04-12
heh, i guess the obvious question is, are you sure your /home is on hda1, then? :)

---

### Post by justleen on 2006-04-12
Is the /home mounted separetly? 
try a fstab -l, and see if theree is a seperate mention of /home.
if thats the case, you probably have created a xxGB partition for /home, which is now full

---

### Post by frup on 2006-04-12
home is on hda1... the same as all of ubuntu. its a 40gb drive. the other drive is 80gb and is an ntfs im getting some files off.

right click on home folder shows 7.5gb used (in home) 23.2gb remaining

---

### Post by justleen on 2006-04-12
can you post the output of fstab -l?

---

### Post by frup on 2006-04-12
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1 /windows ntfs nls=utf8,umask=0222 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by frup on 2006-04-12
thats through opening it in gui not nano

---

### Post by justleen on 2006-04-12
[QUOTE=frup]thats through opening it in gui not nano[/QUOTE]

hmm.. ok, so / is the only mounted partition.. which does make this strange!
a df -H   does tell you as well you have free space?

what does the command quota  output?

---

### Post by frup on 2006-04-12
laurent@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/hda1               38G    11G    25G  31% /
tmpfs                  398M      0   398M   0% /dev/shm
tmpfs                  398M    13M   385M   4% /lib/modules/2.6.12-10-386/volatile
/dev/hdb1               81G    54G    27G  67% /windows


laurent@ubuntu:~$ quota
bash: quota: command not found

---

### Post by justleen on 2006-04-12
only thin i can think of is that there is a quota installed on the home dir.. 
quota is an installable package through apt-get. Yet, im not sure, that if the package is not installed that your able to set quotas.  Out of the box ubuntu shouldnt have quotas anyways.. 

is this happening under a useraccount or your root/admin(your first user) account?

---


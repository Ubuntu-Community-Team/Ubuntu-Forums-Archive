---
title: "Obtain list of installed packages"
date: 2009-12-16
forum: General Help
---

### Post by laloruelas on 2009-12-16
I have messed up the permissions of my install, and i cannot boot into my computer, or recovery mode. :( i can recover all my files and maybe settings. but, i was wondering if there was a way to get a list of all the packages i had previously installed on it, through a live cd. it would be great if i could.

---

### Post by slakkie on 2009-12-16
dpkg --get-selections > package.list

to install all the packages:

sudo dpkg --set-selections < package.list
sudo apt-get dselect-upgrade


And done.

---

### Post by sisco311 on 2009-12-16
> **laloruelas said:**
> I have messed up the permissions of my install, and i cannot boot into my computer, or recovery mode. :( i can recover all my files and maybe settings. but, i was wondering if there was a way to get a list of all the packages i had previously installed on it, through a live cd. it would be great if i could.

/var/lib/dpkg/status contains information about whether a package is marked for removing  or not,  whether  it  is  installed or not, etc.

something like:
```
grep -B 1 \
"^Status: install ok installed$" **/media/mountpoint**/var/lib/dpkg/status | \
awk '/^Package:.*$/{print $2"\t\tinstall"}' | \
sort > package.list
```

should create a list of the installed packages.

Use the commands posted by slakkie to install them on  a new system.


or you can try to chroot in the installation:
```

sudo -i
mkdir /mnt/ubuntu
mount /dev/sd**XY** /mnt/ubuntu
mount --bind /dev/ /mnt/ubuntu/dev
mount --bind /dev/pts /mnt/ubuntu/dev/pts
mount -t proc none /mnt/ubuntu/proc
mount -t sysfs none /mnt/ubuntu/sys
chroot /mnt/ubuntu

```
and run *dpkg --get-selections > package.list*

---

### Post by ajgreeny on 2009-12-16
> **slakkie said:**
> dpkg --get-selections > package.list

to install all the packages:

sudo dpkg --set-selections < package.list
sudo apt-get dselect-upgrade


And done.
To the original poster:  Note this procedure is not possible through a live CD, but requires you to be booted into your installed system.

The only way I can think of to get the information you need is to boot the live CD and copy the files in /var/log/apt, though decoding them will be a long, long job.  One of my logs here is over 1000 lines in length.  Perhaps not the best move?

However, you say you have messed up your permissions.  In what way, and what did you do?  If you did this in terminal, you can see what you did by using the live CD again, mounting your installed ubuntu partition, and looking at the /home/username/.bash_history file.  This keeps a record of your commands, and therefore it may be possible to undo what you did, and put permissions right again.

---

### Post by slakkie on 2009-12-16
I overlooked the part that he cannot access his PC. Use the chroot method provided by the person below my original post.

---

### Post by ajgreeny on 2009-12-16
Very useful, thanks!

---

### Post by laloruelas on 2009-12-17
> **ajgreeny said:**
> To the original poster:  Note this procedure is not possible through a live CD, but requires you to be booted into your installed system.

The only way I can think of to get the information you need is to boot the live CD and copy the files in /var/log/apt, though decoding them will be a long, long job.  One of my logs here is over 1000 lines in length.  Perhaps not the best move?

However, you say you have messed up your permissions.  In what way, and what did you do?  If you did this in terminal, you can see what you did by using the live CD again, mounting your installed ubuntu partition, and looking at the /home/username/.bash_history file.  This keeps a record of your commands, and therefore it may be possible to undo what you did, and put permissions right again.


I did a chmod -R 0440,in a terminal, to my whole file system. . . . . i am a noob.... don think i can reset all of the permissions, might as well just reinstall.

---


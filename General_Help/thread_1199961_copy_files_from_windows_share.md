---
title: "copy files from windows share"
date: 2009-06-29
forum: General Help
---

### Post by Destroyertje on 2009-06-29
Hello,

I have a few problems with copying files from a windows share to an ubuntu 9.04 x86 laptop.

In the old situation both pc's had windows XP and I used a simple windows script to copy from a windows network share from 1 pc (\\pc1\pictures) to the other pc with a few parameters. Like only copy the files that were modified.

Now 1 pc has Ubuntu 9.04 x86 and the other still Windows XP. I can access the network share and copy the files but I want a script. The problem is that I don't know how to do that in linux. So hopefully someone can make or help me with the script. Only the modified and new files needs to be copied.

Destroyertje

---

### Post by koenn on 2009-06-29
you can use smbclient, your commands would look something like

```
 smbclient \\server\share password [-Uusername] [-Wworkgroup] -c get name_of_file.ext 
```
man smbclient for exact syntax

if you're more familiar with standard unix/linux commands, you can mount a windows share in the local (unix) filesystem and use standard linux commands such as cp, rsync, mv, ....

that would look something like this
```
# mount share
mount -t smbfs -o rw,username=UserName,password=PaSs,workgroup=WORKGROUP //server/share /mnt

# sync (i.e. new or modified only)
rsync /mnt/ /dest

# unmount
umount /mnt
```
again, look up the syntax and options in the man pages

---

### Post by Elfy on 2009-06-29
moved to General Help

---

### Post by Destroyertje on 2009-06-30
I tried to sync it with grsync and Unison but I didn't worked. Well I can sync when i use unison -socket xxx on the windows pc and then i can connect to it but it was really slow.

Then I tried freesshd on the windows pc and connect with Unison but then I could not get connected to it.

The problem is that I never worked with rsync/samba and I can't get a nice script from the internet.

---


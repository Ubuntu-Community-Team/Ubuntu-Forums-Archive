---
title: "Deleting a file that does not 'exist'"
date: 2009-08-29
forum: General Help
---

### Post by Jonus on 2009-08-29
I haven't been able to find a solution to this problem elsewhere.  I have a file that really shouldn't be there, but I can't delete the directory structure above it because somewhere it's still hanging on.

when I do a 'ls -ial' in the containing directory I get this:

      ? ?--------- ? ?     ?          ?            ? [H?]_Burn-Up_Scramble_-_01.torrent

No inode, no attribs, no type, no size, etc.  When I try to do anything directly to the file i get 'No such file or directory'

Does anyone have any ideas?

---

### Post by drs305 on 2009-08-29
> **Jonus said:**
> Does anyone have any ideas?

You could try to create the file again and, if successful, then delete it:
```

sudo touch /path/_Burn-Up_Scramble_-_01.torrent

```
I don't like posting "sudo rm" commands, but you probably know how to delete it via terminal. If not:
```
gksudo nautilus /path-to-file
```
Use SHIFT-DEL to delete the file.

---

### Post by sailthesea on 2009-08-29
Close all other processes that may be using that file it is probably being seeded 
Sudo rm BAD!

---

### Post by Jonus on 2009-08-29
Interesting.  Thanks for the reply btw.  I tried what you suggested, this is what i get now when i do

```
ls -ial
``````
8060933 -rw-r--r-- 1 root  root       0 Aug 29 21:42 [H?]_Burn-Up_Scramble_-_01.torrent
8060933 -rw-r--r-- 1 root  root       0 Aug 29 21:42 [H?]_Burn-Up_Scramble_-_01.torrent

```I seems to create the file twice, with the same inode.  But when I do go to delete it with 

```
rm -f *.torrent
```It only deletes one and still leaves me with a 

```
?--------- ? ? ? ?            ? [H?]_Burn-Up_Scramble_-_01.torrent

```as before

---

### Post by yabbadabbadont on 2009-08-29
Sounds like a possible case of filesystem corruption...  have you had a power failure recently?  Or any other kind of lockup that required powering off the machine without shutting it down?

---

### Post by Jonus on 2009-08-29
> **yabbadabbadont said:**
> Sounds like a possible case of filesystem corruption...  have you had a power failure recently?  Or any other kind of lockup that required powering off the machine without shutting it down?

Yeah, we've had some lightning storms recently.  You're probably right about it being FS corruption.  Now it's, how do i get rid of that ghost file.

---

### Post by Jonus on 2009-08-29
I'm going to to umount the filesystem and do a 'fsck' to see if that fixes anything.  That's the only thing i haven't done yet.

---

### Post by yabbadabbadont on 2009-08-29
Well, the first thing I would do is force a full filesystme check on next boot.  Who knows what else might be messed up...  You might also consider making sure that your backups are up to date before you do anything else though.

To force a full filesystem check on next boot, you just have to
```
sudo touch /forcefsck
```
then reboot the machine.

EDIT: That command would force the check on the root filesystem.  Just FYI.

---

### Post by Jonus on 2009-08-29
Thanks for the tip.  I'll give that a try if the fsck on the particular filesystem doesn't resolve anything.

---

### Post by theozzlives on 2009-08-29
Your system will eventually run a check on that partition, alternatively, you can run fsck from the live CD.

---

### Post by a3qp on 2009-09-16
I'm having the same problem. My external hard drive was disconnected while saving a backup and I have some ghost files.
Any idea how I can delete those ghost files? :neutral:

---

### Post by dcstar on 2009-09-18
> **a3qp said:**
> I'm having the same problem. My external hard drive was disconnected while saving a backup and I have some ghost files.
Any idea how I can delete those ghost files? :neutral:

Use this command VERY CAREFULLY:

```
rm -i *
```

---


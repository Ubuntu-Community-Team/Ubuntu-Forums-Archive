---
title: "Corrupted permissions, all questionmarks!"
date: 2009-10-25
forum: General Help
---

### Post by mmmod on 2009-10-25
The following listing illustrates my problem:

```
$ ls -l
ls: cannot access pict0841.jpg: Permission denied
ls: cannot access pict0842.jpg: Permission denied
ls: cannot access pict0843.jpg: Permission denied
total 61080
-rwxrwxr-x 1 pundit pundit 1715400 2007-03-09 15:59 pict0819.jpg
-rwxrwxr-x 1 pundit pundit 1393492 2007-03-10 23:38 pict0840.jpg
?????????? ? ?      ?            ?                ? pict0841.jpg
?????????? ? ?      ?            ?                ? pict0842.jpg
?????????? ? ?      ?            ?                ? pict0843.jpg
-rwxrwxr-x 1 pundit pundit 1573074 2007-03-11 00:29 pict0844.jpg
```(a few lines were excluded)

So, I'm having a directory where three files' metadata (such as permissions, owner, creation date and so on) are... well... not what it should be.

The files cannot simply be deleted (since the cannot be stat-ed).

The files are on a ReiserFS filesystem, which lives on a USB disk that have had some problematic disconnects lately.

Any ideas? Restoring the files would be full score, but having them disappear would suffice.

---

### Post by mmmod on 2009-10-27
Bump

---

### Post by CharlesA on 2009-10-27
I believe that it is unable to figure out who the owner of the files are.

Try doing:

```
sudo chown -R pundit:pundit pict0843.jpg pict0842.jpg pict0841.jpg
```

That should get you access.

---

### Post by alphaniner on 2009-10-27
> I believe that it is unable to figure out who the owner of the files are.

I think it's a bit more serious than that (filesystem corruption) but it's a good suggestion nonetheless!

---------------

Have you tried running fsck?  I'm pretty sure it can work with Reiser, but I'm not sure how effectively.

Have you tried copying other files to 'overwrite' the problematic ones?

Or you could just copy all of the 'working' files onto another partition and then reformat.  That would get rid of the problematic files.

But you should definitely look into why the device has been malfunctioning or you'll likely find yourself in the situation again.

---

### Post by Giblet5 on 2009-10-27
> **CharlesA said:**
> I believe that it is unable to figure out who the owner of the files are.

Try doing:

```
sudo chown -R pundit:pundit pict0843.jpg pict0842.jpg pict0841.jpg
```

That should get you access.

+1 on that and I hope you all appreciate my restraint in not commenting that ReiserFS is a killer filesystem. Whoops.

---

### Post by CharlesA on 2009-10-27
> **alphaniner said:**
> I think it's a bit more serious than that (filesystem corruption) but it's a good suggestion nonetheless!

+1 on the fsck. I figured, simplest thing first. :p

If the chown didn't work, try fsck and see what happens. If it's FS corruption (which it probably is), it's more then likely due to the device not disconnecting cleanly.

---

### Post by Giblet5 on 2009-10-27
> **CharlesA said:**
> +1 on the fsck. I figured, simplest thing first. :p

If the chown didn't work, try fsck and see what happens. If it's FS corruption (which it probably is), it's more then likely due to the device not disconnecting cleanly.

+10 - Best Answer Award

---

### Post by mmmod on 2009-10-27
Thanks for the replies, folks!

I tried running fsck on the filesystem, but fsck did not find any corruptions. I unmounted and mounted the filesystem a number of times, tried to chmod, chown and rm the files without any progress.

Then I tried to rm -rf the whole directory (after all, the files were not that important), and then the machine *froze*.

In /var/log/messages:
```
Oct 27 20:04:05 pundit kernel: [246108.101885] ReiserFS: warning: is_tree_node: node level 0 does not match to the expected one 1
Oct 27 20:04:05 pundit kernel: [246108.101892] ReiserFS: sdb1: warning: vs-5150: search_by_key: invalid format found in block 59146753. Fsck?
Oct 27 20:04:05 pundit kernel: [246108.101900] ReiserFS: sdb1: warning: vs-13070: reiserfs_read_locked_inode: i/o failure occurred trying to find stat data of [133119 1740
0x0 SD]
...
(duplicated a few thousand times)
...
Oct 27 22:26:13 pundit syslogd 1.5.0#5ubuntu3: restart.
Oct 27 22:26:13 pundit kernel: Inspecting /boot/System.map-2.6.28-6-386
Oct 27 22:26:13 pundit kernel: Inspecting /usr/src/linux/System.map
Oct 27 22:26:13 pundit kernel: Symbol table has incorrect version number.
Oct 27 22:26:13 pundit kernel: Cannot find map file.
Oct 27 22:26:13 pundit kernel: Loaded 52099 symbols from 95 modules.
Oct 27 22:26:13 pundit kernel: [    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
Oct 27 22:26:13 pundit kernel: [    0.000000] Linux version 2.6.28-6-386 (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #20-Ubuntu Fri Apr 17 08:32:39 UTC 2009 (Ubuntu 2.6.28-6.20-386)
```So, lots of ReiserFS warnings, then reboot using POWER button, then booting again. (As a bonus, note that the system clock jumped forward roughly 2 hours... :confused:)


However... the files are now completely normal. No strange permissions, not removed, but normal.

So, for anyone reading this thread later on. Try to reboot the whole system, or at least reload the "reiserfs" kernel module if you see stuff like this. It might help.

---

### Post by CharlesA on 2009-10-27
What the...? I wonder what caused it to act that way.

Thanks for the update. :-)

---

### Post by mmmod on 2009-10-27
Yeah! :)

My guess is that the kernel module for ReiserFS was in a bad state or something, because that is about the only thing i didn't reload (no rebooting of the system).

---


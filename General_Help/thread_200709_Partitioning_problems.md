---
title: "Partitioning problems"
date: 2006-06-20
forum: General Help
---

### Post by chubsmalone on 2006-06-20
I wasn't sure where to put this in the forums, so I apologize if I'm wrong.

I am running dapper on my Inspiron 1200 right now and I'd like to dual boot with XP Home.  My machine has a 30G drive which had a root partition of 27.something Gig and a swap that filled up the rest.

I used gparted to shrink my root directory to 11.73G and created another 5.42G fat32 partition for me to store music that will be accessed by windows and linux.  I left the swap alone.  I didn't partition the rest of the available space hoping windows would just take it over...if I'm wrong about that one, let me know.

I fired up ubuntu and tried moving all of my music files over to the vfat partition and it gives me errors about not being able to mount it.  I made a directory /music and mounted the drive to the /music directory, and now it tells me I don't have permission to write to the drive.  I did "chmod o+rw /music" and tried again and it still gives me the same error.  

So, how do I make it accessible as a regular user and make the permissions stick after a reboot?  How do I make the drive mount to /music on every reboot?  Is there a better way to set up my partitions for XP and Linux to share some space for common files?

---

### Post by renzokuken on 2006-06-20
i cant really help with the first parts,

but in order to make a partition mount on boot up, you need to add it your "fstab"

```
sudo gedit /etc/fstab
```

the actual line you need to insert depends on the filesystem and partition name, but looking at the other lines should give you some clues

---

### Post by chubsmalone on 2006-06-20
Thanks for the reply renz.  Do you know why the commands that I'm using aren't working?

---

### Post by Third Thoughts on 2006-06-20
[QUOTE=chubsmalone]Thanks for the reply renz.  Do you know why the commands that I'm using aren't working?[/QUOTE]

I think that only the user you mount the drive with can write to it. Since by default only root can mount drives, only root can write to them. Also, by default mounted drives ignore all the ch commands (chown, chmod, etc). To change that call mount with the -o option and add the option suid. In other words 
```
 mount -t vfat -o suid /whatever you're mounting /wherever you're mounting
```
Then you can tell it to chown. However, it's easiest if you just write a line in your fstab file that looks like this
```
 /dev/whatever       /whatever          vfat    defaults        0       0 
```
The defaults option sets it so the drive mounts on start up, can be read and written to, accepts ch commands, and some other more techincal stuff that I don't quite get.

~Andrew S.

---


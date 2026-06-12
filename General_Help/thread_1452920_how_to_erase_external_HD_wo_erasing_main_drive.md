---
title: "how to erase external HD w/o erasing main drive?"
date: 2010-04-12
forum: General Help
---

### Post by rolypolycat on 2010-04-12
Hello!

I'm using karmic koala. I have an external hard drive I use for backups. This drive has entire operating system on it(don't know which one, but I think it's intrepid), from when I did a complete backup eons ago. I have added new stuff since then. I tried to erase the system files on it, since they take up space and aren't likely from my current system. I don't run the drive all the time, only when I'm backing up files. The rest of the time, it's off. When I did this, I couldn't run any programs on my main computer( the bin directory was gone), and it wasn't in my trash on the main drive or the external drive. I tried re-installing without erasing my home directory on the main drive; it went okay, until I tried to open a file. My /home apparently had nothing in it, so i downloaded my backup files, only to run out of room. The files were there; I just couldn't see them. I tried to open several programs, but was told I didn't have root access. Finally, I just reformatted the whole drive and re-installed everything. 
What I'd like to know is:
1. How do I clear the junk from the external drive  without hurting the main drive?
2. Why did erasing the old bin file on the external drive whack the same file on the main drive?
3.Several times before, I have upgraded or re-installed xubuntu, leaving my home directory intact. The upgrade either can't find my files, or forgets half my settings. How can I keep my files and settings? I hate having to re-install everything from scratch each time I upgrade. I thought having a separate /home directory was supposed to protect all that.
I appreciate any help. Thanks in advance!

---

### Post by sanemanmad on 2010-04-12
Hello...


Please post the following from your shell with the external HDD mounted.

# as root
```
sudo -s
```

```
df -h
```

```
fdisk -l
```

The solution is simple, however i want to have better understanding before jumping off the deep end.

---

### Post by prodigy_ on 2010-04-12
What commands or tools did you use to erase your external drive?

Under normal circumstances you can just use **rm -rf** or **mkfs** on all partitions you no longer need. None of them - **if run on the intended partition** - will ever hurt other partitions.

---

### Post by rolypolycat on 2010-04-13
Here are the contents of the commands I ran:Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G  101G   37G  74% /
udev                  496M  276K  496M   1% /dev
none                  496M     0  496M   0% /dev/shm
none                  496M   92K  496M   1% /var/run
none                  496M     0  496M   0% /var/lock
none                  496M     0  496M   0% /lib/init/rw
none                  144G  101G   37G  74% /var/lib/ureadahead/debugfs
/dev/sdb1             6.5G  2.4G  3.7G  40% /media/disk
/dev/sdb6             140G  105G   28G  79% /media/disk-1
oot@the-cathouse:~# fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e53a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19087   153316296   83  Linux
/dev/sda2           19088       19457     2972025    5  Extended
/dev/sda5           19088       19457     2971993+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ebb0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         851     6835626   83  Linux
/dev/sdb2             852       19457   149452695    5  Extended
/dev/sdb5             852         992     1132551   82  Linux swap / Solaris
/dev/sdb6             993       19457   148320081   83  Linux
root@the-cathouse:~#

As to the commands I used; I used a terminal rm- r, since the help file for rm said this would remove the directory. I made sure the terminal said I was in /media/disk1; at least that's what the heading said. I first removed the /bin directory, and from then on, things went haywire. I couldn't find the /bin directory, so I used Synaptic to re-install ubuntu-core and other system files, hoping that would fix things. When it didn't, then I re-installed xubuntu in the root (formatted) directory, but my files didn't show in my home directory when I rebooted. I've had missing files like this before when I've upgraded.
I hope this helps. Thanks!

---

### Post by prodigy_ on 2010-04-13
With **rm** you need to be extra careful about the arguments. An accidental extra whitespace, for example, and you may end up deleting something you didn't want to.

---


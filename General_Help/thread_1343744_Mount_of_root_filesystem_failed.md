---
title: "Mount of root filesystem failed"
date: 2009-12-02
forum: General Help
---

### Post by Fitch on 2009-12-02
I have Karmic on a 1.4 GHz winfast6150M2MA Everything works perfectly (except for NVIDIA, but that seems to be the norm)

This morning the system developed a black screen of death, in as much as every time I start up I get:

Mount of root filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and reboot the system.
Give root password for maintenance
(or type CONTROL-D to continue):

Since I don't have a clue what to do if I enter the shell, I type CONTROL-D and get the following:
problem is, the screen clears so fast, it may not be right..

Unmount /proc/sys/fs/binfmt/misc not mounted
/var/run device is busy

That's all I can get after about 20 reboots as it disappears too fast to write down anymore.

Where do I go from here?

The last thing I did was to get the computer to mount the NAS drive automatically yesterday.

Being only a month old as far a Linux is concerned, I'm pretty clueless right now, can't even edit fstab to see if it is the NAS drive that's doing it.
Tried sudo nano /etc/fstab to rem out the line, but always get Error writing /etc/fstab read-only file system.

I tried chmod 0777 /etc/fstab but it keeps coming up read only filesystem.

---

### Post by john newbuntu on 2009-12-02
I'd suggest starting with a file system check just to make sure your disk is good.  Run this from the shell (assuming /dev/sda2 is where linux root fs is installed):
sudo e2fsck -C0 -p -f -v /dev/sda2
If this is good, then try 
sudo mount -a 
cat /etc/mtab
cat /etc/fstab
see what is missing.  Please look at logs /var/logs/syslog and kern.log to see any errors.

---

### Post by Fitch on 2009-12-02
e2fsk: command not found
mount -a comes up with: 
[20007.375552] CIFS VFS: Error connecting to socket. Aborting operation
[20007.411089] CIFS VFS: cifs_mount failed w/return code = -101
mount error(101): network is unreachable.

So it is the problem with fstab and the NAS drive.  I now realise that the computer mounts the "drives" before it mounts the network...

So it comes back to how do I alter fstab to get it back to what it was?  (see above)

---

### Post by Fitch on 2009-12-02
OK, this is how I did it..

sudo mount -o remount,rw /
sudo chown [owner]:[group] /etc/fstab
cd /etc
chmod fstab 777
nano fstab

Got rid of the line to mount the server
saved it 
restarted
Bob's your uncle...

Now then, next question is...

what is the **correct** way to mount a NAS drive on startup?

---

### Post by Ampi on 2009-12-07
> **Fitch said:**
> e2fsk: command not found

This is a typo, right? Because the command is e2fsck (FileSystem ChecK)
Maybe that's why it doesn't find the command..

---

### Post by Fitch on 2010-01-23
Yeah probably that's why it couldn't find it, never mind. all done & dusted now.

---

### Post by entelexiya on 2011-01-25
I rebooted the server and I have the same bug Mount of root filesystem failed
before that I wrote segfault, ftp is not working properly "proftpd"
 when doing a sudo mount-a also writes a segmentation fault.

---

### Post by icewall on 2011-02-01
Thanks Fitch... had exactly the same root mounting fail issue.

Followed your steps and was able to edit out the "NAS" mounting part and worked like a charm.

Before the root mounting issue, I was editing the fstab to mount the NAS and all hell broke after that. 

Did you manage to find the proper way to add the NAS mounting in the fstab?

regards
icewall.

---

### Post by Fitch on 2011-02-01
I gave up waiting for anyone to tell me.

However, having a look at "System, Preferences, Startup Applications", I would stick the command in there.

---


---
title: "/etc/fstab edited now can't load 11.04"
date: 2011-10-15
forum: General Help
---

### Post by 02darkRS on 2011-10-15
I edited /etc/fstab in an attempt to tweak 11.04 for my SSD as I am noticing it slowing down already. I edited it as follows for / as per this article: 


[http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190](http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190)

I added this information into the line for my /
> **noatime**,discard,**data=ordered**

I am now getting serious errors with the S or M options at boot. I attempted the following in manual recovery & after a reboot is recovery mode:

```

sudo cp /etc/fstab/backup /etc/fstab
```
error came back as read only file. 

```
sudo -e /etc/fstab
```
read only file

What can I do to get back my old fstab? I backed it up but I can't get it to load the back up. I also could simply remove my additions ctrl+s & reboot but it won't let me in that way either........ Please help asap!

---

### Post by 02darkRS on 2011-10-15
```
sudo nano -w /etc/fstab
```
^allowed me in to edit but when I saved it again said read only file........ :confused:

---

### Post by effenberg0x0 on 2011-10-15
I find it an odd structure. /etc/fstab is a file, not a directory. How can it hold backup inside it?

Please, post the output of:
ls -lha /etc/fstab /etc/fstab/backup
sudo -s
cat /etc/fstab
cat /etc/fstab/backup

Regards,
Effenberg

---

### Post by 02darkRS on 2011-10-15
sorry in my quick typing on my sons pc to get this fixed i mistyped....
```
sudo cp /etc/fstabbackup /etc/fstab
```
is what i attempted is this not the command to copy my backed up fstab in? 

I can't post the true contents from the machine as it is stuck in manual edit. my fstab from another thread is below as it looks now with me pasting in what I just added below in red: 
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=124f0412-3e68-46f4-a9df-162dc81b94e6 /               ext4    [COLOR=Red]**noatime**,discard,**data=ordered,**[/COLOR]errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=e3a1a937-a023-4757-a0bb-e3d4c737a7a4 /home           ext4    defaults        0       2
# /tmp was on /dev/sdb7 during installation
UUID=80cecb02-84e2-4e39-8aea-3ddeeca0b391 /tmp            ext4    defaults        0       2
# /var was on /dev/sdb8 during installation
UUID=4e41415f-9378-4fe7-9d2a-95f9f8778802 /var            ext4    defaults        0       2
# swap was on /dev/sdb6 during installation
UUID=2f7fd365-a71d-4401-86dd-29b8002b1e2a none            swap    sw              0       0 			 		
```

all i need to do is get into /etc/fstab comment out my text in red above & it should be back to normal but it keeps telling me it's read only..... how do I address that?

---

### Post by 02darkRS on 2011-10-15
tried this:
```
mount -o remount,rw /
```

as per here:
[http://www.unix.com/linux/54874-how-edit-etc-fstab-when-root-mounted-read-only.html](http://www.unix.com/linux/54874-how-edit-etc-fstab-when-root-mounted-read-only.html)

still says read only file....

---

### Post by effenberg0x0 on 2011-10-15
Don't know if you're mounted RO, but wouldn't hurt to remount rw first. try this:

```

sudo -s
sudo mount -oremount,rw /
sudo chown root:root /etc/fstab*
sudo chmod 644 /etc/fstab*
cat /etc/fstabbackup | sudo tee /etc/fstab
```Not sure if you can change fstab when not on recovery to be honest.
If the above doesn't work, login to recovery in grub (hold shift during boot, choose recovery kernel) and run the same commands.

Please report back.

Effenberg

---

### Post by 02darkRS on 2011-10-15
should:
sudo mount -oremount,rw /

have a space after -0 ?

---

### Post by effenberg0x0 on 2011-10-15
> **02darkRS said:**
> should:
sudo mount -oremount,rw /

have a space after -0 ?

nope.

**EDIT:**

Just noticed you typed a zero (0). Notice that the command uses a "o" (letter) not a zero.
For example:
sudo mount -oremount,rw /
*sudo mount* -no *remount*,*rw* /

Effenberg

---

### Post by 02darkRS on 2011-10-15
```
sudo -s
``` (brought back another command line) 
```
sudo mount -oremount,rw / 
```(unrecognized mount option "discar" or missing value. mount: / not mounted already, or bad option.) 
```
sudo chown root:root /etc/fstab*
``` (changed ownership of both fstab & fstabbackup) 
```
sudo chmod 644 /etc/fstab*
``` (same as above) 
```
cat /etc/fstabbackup | sudo tee /etc/fstab
``` (tee: readonly. then it listed the current contents of my fstab as posted above.) I couldn't scroll up to see the contents of etc/fstabbackup

---

### Post by effenberg0x0 on 2011-10-15
> **02darkRS said:**
> sudo -s  (brought back another command line) sudo mount -oremount,rw / (unrecognized mount option "discar" or missing value. mount: / not mounted already, or bad option.) sudo chown root:root /etc/fstab* (changed ownership of both fstab & fstabbackup) sudo chmod 644 /etc/fstab* (same as above) cat /etc/fstabbackup | sudo tee /etc/fstab (tee: readonly. then it listed the current contents of my fstab as posted above.)


**EDIT:**
mount -n -o remount -t ext4 /dev/sda1 /

I don't know you're in a RO filesystem. Is it in your grub kernel options?
Well, it won't hurt to check and erase ro from there too...

Regards,
Effenberg

---

### Post by 02darkRS on 2011-10-15
I will do that but since it says / is not mounted & when mounting it threw errors & skipped...... then it's not mounted is it? 

also, to go farther why did following the directions as supposedly given by Mr Linux himself cause such mayhem? 

is there somewhere trustworthy to follow to fix the issue. if not I am going to have to ditch ubuntu. it seems to be trashing my ssd already. boot is already 3x as slow & i haven't even added anything to the install except stellarium.

---

### Post by 02darkRS on 2011-10-15
> **effenberg0x0 said:**
> **EDIT:**
mount -n -o remount -t ext4 /dev/sda1 /

I don't know you're in a RO filesystem. Is it in your grub kernel options?
Well, it won't hurt to check and erase ro from there too...

Regards,
Effenberg

sda1 is my windows7 partition which is currently blank as I was planning to install it this weekend. ?????

also, i've been editing fstab before this weekend as seen in my other threads & not had this issue. what's the difference?

---

### Post by effenberg0x0 on 2011-10-15
The command "mount" with no parameters shows you what is mounted. I do believe / is mounted read-only. 

Effenberg

---

### Post by effenberg0x0 on 2011-10-15
Oh, theres windows  there. So use the correct dev, probably sda2. Again, the command mount shows you what is mounted. And sudo fdisk -l shows you the devices.

I have no idea why its RO. This is why I asked if you added ro to the default_linux_command_line in /etc/default/grub...

Effenberg

---

### Post by 02darkRS on 2011-10-15
i believe you're right. errors=remount-ro is what is in my fstab...... why would i want to do that? 
if I have errors I'd need to fix them. man, so it seems like I am stuck & have to wipe the install again?
I was just telling someone last night how great this free community is & I have learned a lot in three weeks...... but I am not reinstalling again. What can I do here? 

if I still need to follow your above code, please let me know what it does. sda1 is an ntfs partition so I am not comfortable commanding what you have above as it sits.

edit:
> So use the correct dev, probably sda2. Again, the command mount shows  you what is mounted. And sudo fdisk -l shows you the devices.I don't understand this^. I have done a lot of work in three weeks & know quit a bit more than the std noob but I am still a noob. I did command mount & read what's there but what do i do with it? sda2 is the / location.

---

### Post by effenberg0x0 on 2011-10-15
If you saw that / is mounted to /dev/sda2 (not sda1), this is the one we should try to remount read-write. 

Let me give you some more info: It's not unusual to have errors=remount-ro on fstab. If errors happen, it protects the filesystem until you fun fsck to find and fix bugs. The problem is that if you look at some bug reports...

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/438379]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438379")
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/515937]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/515937")
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/528981]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528981")

... you'll see that some filesystems are getting mounted RO even when there's no error to fix.

So, the best you can try right now is to remount it with parameters, so it doesn't use the parameters at /etc/fstab: 

```
sudo mount -n -o rw,remount -t ext4 /dev/sda2 /
```Then proceed with to repair of fstab as you were doing before. 

But if it doesn't work, you have to either boot in recovery and see if the system is still ro or rw (if errors persist).

If you can't get the system out of read-only mode, you will have to choose between believing that in fact there might be error and run fsck to fix them or
boot with a Live Ubuntu CD/USB, use nautilus to navigate in your HDD file and edit fstab from there.

Effenberg

---

### Post by 02darkRS on 2011-10-15
```
sudo mount -n -o rw,remount -t ext4 /dev/sda2 /
```
this just gave me a list of what things mean. 

so, i am starting up liveCD now. can i just gedit /etc/fstab from terminal there or is there something special I have to do? 

also, what about the ssd optimizing
and thanks for all the quick replies!

---

### Post by effenberg0x0 on 2011-10-15
Try once more please, like this now:

```
sudo mount -n -o remount -t ext4 /dev/sda2
```

Effenberg

---

### Post by effenberg0x0 on 2011-10-15
No, if you boot to a Live CD desktop you will can use gedit, any editor to edit the fstab in your HDD. 

Effenberg

---

### Post by 02darkRS on 2011-10-15
> **effenberg0x0 said:**
> No, if you boot to a Live CD desktop you will can use gedit, any editor to edit the fstab in your HDD. 

Effenberg

i am already in liveCd. I'd love to try the changed command but don't want to restart the CD again. 
when I gedit in live cd it shows the cd's fstab. how do i navigate to my sda2 / /etc/fstab?

---

### Post by effenberg0x0 on 2011-10-15
> **02darkRS said:**
> i am already in liveCd. I'd love to try the changed command but don't want to restart the CD again. 
when I gedit in live cd it shows the cd's fstab. how do i navigate to my sda2 / /etc/fstab?

No prob. At a console, run sudo fdisk -l to check where your hdd / partition is at. It's the largest of the "Linux" system type. /dev/sd? You have to check what sd<something> it is.

Then, do this at the console:
sudo mkdir /media/myhdd
sudo mount -t ext4 /dev/sd<something> /media/myhdd
sudo gedit /media/myhdd/etc/fstab

Effenberg

---

### Post by 02darkRS on 2011-10-15
I have to leave to take my oldest boy bowling for his bday but will be right back to this when we're done.

---

### Post by 02darkRS on 2011-10-15
I am assuming this is not working as this is what I get:
```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda2/media/myhdd
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```and opening:
```
ubuntu@ubuntu:~$ sudo gedit /media/myhdd/etc/fstab

```nets me a blank fstab edit screen

edit: i was missing the space between sda2 & /media/myhdd in the mount command. I edited the file, saved, & am closing out of the liveCD now.

---

### Post by 02darkRS on 2011-10-15
i am back into my install. thank you! i am marking this thread solved but for searches will come back & link to new thread i am about to create regarding the issue that caused this mayhem.

---


---
title: "CDs wont play"
date: 2009-12-07
forum: General Help
---

### Post by askinne2 on 2009-12-07
Hey guys. I am currently having a problem with CDs playing. The cd drive opens and closes without any problems. The problem is once there in nothing happens. Nothing comes up to play or anything. This problem is for all types of cds (audio, dvd, games, anything on a cd that should play on a computer). 

I am a complete ubuntu noob so please explain everything for me haha. Thanks alot!

Running: Ubuntu 8.10

---

### Post by askinne2 on 2009-12-08
Ok so I upgraded to 9.04 and hoped that might fix it. It says its mounted in read only. I ran the fsck thing manually when it prompted me on start up because it failed to run manually. It said there was errors and when I ran it manually the system finally would start up again. But cds still wont start up at all so I assume its still in read only mode. 

I dont have any idea what to do. Should I run a certain command and give you guys the output? Thanks.

---

### Post by alexfish on 2009-12-08
Hi

 What do you use for the player

list all the players you have

---

### Post by askinne2 on 2009-12-08
Do you mean audio players? I dont just mean audio cds wont run. I mean any type of cd you insert into the drive dont even show up as inserted into the computer.

---

### Post by alexfish on 2009-12-08
Best I can do at the moment is to point you here

[https://help.ubuntu.com/community/JauntyUpgrades](https://help.ubuntu.com/community/JauntyUpgrades)

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Need to do some searching

---

### Post by alexfish on 2009-12-08
Hi 

Can you try this

                                 open your cdrom drive and put the cd inside and close the drive
 

  open up the terminal
 

  the login as root  
 ..........................................................

 code
 

 sudo su
 ............................................................

 

 then
...........................................................

 code


 mount -t auto /dev/cdrom /mnt/cdrom
...............................................................

 

 IMPORTANT: don't remove the cd inside the cdom until you have properly unmounted 

 ......................................................................................................................

 code


 umount /mnt/cdrom

   If any error messages show up  in the terminal KEEP A COPY   Close the Terminal   And  try a CD

---

### Post by askinne2 on 2009-12-08
Thanks for the reply.

The first two commands work fine with no errors. Then I try to umount command and it says that /mnt/cdrom cannot be found. So Ill leave the disk in there until I figure that one out.

The second command you gave me listed this output:

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


Thanks.

---

### Post by alexfish on 2009-12-08
Hi
 I Will Find The List of Commands to make the dir that are missing,
  it won't be instant

It will be ok to take the disk out

---

### Post by alexfish on 2009-12-08
Hi 

One more check 

put the cd in 


From the terminal

  	 	 	 	 	 	  ls /dev/


.......................................................................................................

 post the result

---

### Post by askinne2 on 2009-12-09
adsp             mapper              ram7        tty16  tty43  urandom
agpgart          mcelog              ram8        tty17  tty44  usbmon0
audio            mem                 ram9        tty18  tty45  usbmon1
binder           mixer               random      tty19  tty46  usbmon2
block            net                 rfkill      tty2   tty47  usbmon3
bus              network_latency     rtc         tty20  tty48  usbmon4
char             network_throughput  rtc0        tty21  tty49  usbmon5
console          null                sda         tty22  tty5   usbmon6
core             nvidia0             sda1        tty23  tty50  usbmon7
cpu_dma_latency  nvidiactl           sda2        tty24  tty51  v4l
disk             oldmem              sda5        tty25  tty52  vcs
dri              pktcdvd             sequencer   tty26  tty53  vcs1
dsp              port                sequencer2  tty27  tty54  vcs2
ecryptfs         ppp                 sg0         tty28  tty55  vcs3
fb0              psaux               shm         tty29  tty56  vcs4
fd               ptmx                snapshot    tty3   tty57  vcs5
full             pts                 snd         tty30  tty58  vcs6
fuse             ram0                sndstat     tty31  tty59  vcs7
hpet             ram1                stderr      tty32  tty6   vcs8
input            ram10               stdin       tty33  tty60  vcsa
kmsg             ram11               stdout      tty34  tty61  vcsa1
log              ram12               tty         tty35  tty62  vcsa2
loop0            ram13               tty0        tty36  tty63  vcsa3
loop1            ram14               tty1        tty37  tty7   vcsa4
loop2            ram15               tty10       tty38  tty8   vcsa5
loop3            ram2                tty11       tty39  tty9   vcsa6
loop4            ram3                tty12       tty4   ttyS0  vcsa7
loop5            ram4                tty13       tty40  ttyS1  vcsa8
loop6            ram5                tty14       tty41  ttyS2  video0
loop7            ram6                tty15       tty42  ttyS3  zero


By the way, I upgraded to 9.10 and now it shows a cdrom0 in my "Places" list. When I click that it gives me this error:

Unable to mount cdrom0
mount: special device /dev/scd0 does not exist

---

### Post by ddas4 on 2009-12-09
Look for libdvdcss2 on synaptic and install it. It should solve your problem.

---

### Post by alexfish on 2009-12-09
For  @ askinne2
take any cds out 

try running the update manager

reboot without the cds

see what happens

---

### Post by alexfish on 2009-12-09
From the the system menu select the Disk Utility

   you should see something like this screen shot

  insert a cd or dvd  in the drive and see what happens

---

### Post by askinne2 on 2009-12-09
[IMG]http://img190.imageshack.us/i/screenshotic.png/[/IMG]Well heres what mine looks like. Its missing the CD drive apparently. And now I cant open the disk tray at all unless I do it while its rebooting.

[IMG]http://img190.imageshack.us/img190/3918/screenshotic.png[/IMG]

---

### Post by alexfish on 2009-12-09
> **askinne2 said:**
> [IMG]http://img190.imageshack.us/i/screenshotic.png/[/IMG]Well heres what mine looks like. Its missing the CD drive apparently. And now I cant open the disk tray at all unless I do it while its rebooting.

[IMG]http://img190.imageshack.us/img190/3918/screenshotic.png[/IMG]

No Picture to look at   

    From the Software Center  search box     enter " mountmanager" and install
      you can also do via Synaptic

  then menu will appear in the System Administration Menu

    click on it And Has All The Help You Need  

     Best Desk Top Gadget I Have Seen

---


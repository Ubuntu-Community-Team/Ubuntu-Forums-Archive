---
title: "initramfs at boot !  [9.04]"
date: 2009-10-19
forum: General Help
---

### Post by kemo0o on 2009-10-19
hello all !! 

suddenly my ubuntu stopped working i don't know why ? 
when i turned on the computer and while booting , A console screen appear  saying : 

Busybox v1.10.2 
then at last 
(initramfs) 

when i typed exit to see an error  i found that 

> /init :line 258Cannot open /root/dev/console: no such file
[667.799267] Kernel panic - not syncing : Attemped to kill init 


hint : 
1- My ubuntu is installed on hard drive by using CD and it worked for more than 3 months but why this happenned ?? 
 2- Recovery Mode gives this message also !!

any solution ....

---

### Post by P4man on 2009-10-20
seems like ubuntu cant mount the drive. Did you change anything?
Can you boot from a liveCD and access the drive?

---

### Post by MelDJ on 2009-10-20
do you have windows installed too?
if you do, run a chkdsk then boot into ubuntu

---

### Post by kemo0o on 2009-10-23
> **MelDJ said:**
> do you have windows installed too?
if you do, run a chkdsk then boot into ubuntu

yea ,  i made chkdsk  but also the problem stil exist

---

### Post by jmszr on 2009-10-23
kemoOo,

You are running Wubi, right? As near as I can tell you are, if so, then perhaps this will help:

Wubi installs Ubuntu into a windows folder - usually a NTFS type of file system, this file system has a known reaction of being unstable in other operating systems like Ubuntu when a hard shutdown happens.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in. Click Properties. Select the "Tools" tab and click "check now" under error checking (with Vista you might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After the checking is done, shut down  by using the start menu (Do Not hard reboot) and  try using Ubuntu now. ( From Ago)
                  
You can also accomplish the immediate previous tip by running chkdsk/f  in Windows and then shutting down properly.

---

### Post by kemo0o on 2009-10-23
> **jmszr said:**
> kemoOo,

You are running Wubi, right? As near as I can tell you are, if so, then perhaps this will help:

Wubi installs Ubuntu into a windows folder - usually a NTFS type of file system, this file system has a known reaction of being unstable in other operating systems like Ubuntu when a hard shutdown happens.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in. Click Properties. Select the "Tools" tab and click "check now" under error checking (with Vista you might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After the checking is done, shut down  by using the start menu (Do Not hard reboot) and  try using Ubuntu now. ( From Ago)
                  
You can also accomplish the immediate previous tip by running chkdsk/f  in Windows and then shutting down properly.

bro .... i installed Ubuntu from CD in seperated partition but in the same hard drive that contains Win$ 

BTW this is shoot from Disk Management

[IMG]http://i35.tinypic.com/wvddap.jpg[/IMG]

although the ubuntu partitions are empty as you see .. the ubuntu boot screen appears then  after 5 secs the "initramfs" screen appears

Hint : This Error appeared after Hard shutdown

---

### Post by MelDJ on 2009-10-23
this is a common problem after not shutting down properly
try doing chkdsk /r

---

### Post by kemo0o on 2009-10-25
> **MelDJ said:**
> this is a common problem after not shutting down properly
try doing chkdsk /r

I did this .... but the problem is still exist 
:confused::confused:

---

### Post by kemo0o on 2009-10-25
F1 

sos .... Help plz

---

### Post by orlox on 2009-10-25
I believe I heard somewhere this could be caused by problems on the configuration of grub, the bootloader.

Are you using jaunty? Perhaps this video could help you get grub reinstalled. 0% confident that this will solve this problem, but it wouldn't hurt to try if you're out of options. It wouldn't risk any of your data also.

---

### Post by orlox on 2009-10-25
I forgot the link :P

[http://www.youtube.com/watch?v=WtBBl6HvdpM]("http://www.youtube.com/watch?v=WtBBl6HvdpM")

---

### Post by novafluxx on 2009-10-25
> **MelDJ said:**
> this is a common problem after not shutting down properly
try doing chkdsk /r

chkdsk /r is what you want to run, MelDJ is correct. chkdsk /f won't repair the file system as thoroughly.

---

### Post by RipTorn on 2009-10-25
Generally I found if chkdsk /r has run and it says everything is normal, I'll usually re-install ubuntu (unless you have data you want)

I personally use the windows recovery CD and run fixmbr to take over the mbr again, format the Ubuntu partition and start again.

(granted this isnt the best idea if you want your data, but its always a fallback option if you just want ubuntu working.

---

### Post by kemo0o on 2009-10-26
when i run the live cd and start ubuntu using it (LIVE) 

and tried to open the Ubuntu Partition which installed in this messages appeared 

1- 

> 
Unable to mount location

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


2- 
> 
Unable to mount location

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending


3- 
> 
Cannot mount volume.

Details:
mount wrong fs type,bad option,bad superblock on/dev/sda6,    missing code page or helper program , or other error          in some cases useful info is found in syslog - try     dmesg | tail or so


---

### Post by RipTorn on 2009-10-26
Sounds like the partition for ubuntu is corrupt, can you mount it manually?

sudo mount /dev/sda6 /mnt

or something similar.

---

### Post by kemo0o on 2009-10-30
> **RipTorn said:**
> Sounds like the partition for ubuntu is corrupt, can you mount it manually?

sudo mount /dev/sda6 /mnt

or something similar.

when i write sudo beside (initramfs) it tell me that sudo not found

---

### Post by RipTorn on 2009-10-31
Sorry I mean in a live CD of ubuntu.

Throw in the installer CD and it should have try ubuntu without installing.

try to mount it see if it spits any errors out.

---

### Post by kemo0o on 2009-10-31
I did it but i got this message
> mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

### Post by kemo0o on 2009-11-03
any help !!

---


---
title: "Need Major Help!! Ubuntu not loading."
date: 2010-01-20
forum: General Help
---

### Post by MacGyver666 on 2010-01-20
Hey guys... I'm posting this for a friend of mine. I'm trying to help her resolve her problem through the computer, so this is proving to be difficult lol ... When she tries to turn on her computer, it gets to 86% loaded and gives this message

"unexpected consistency"... an automaticc file system check (fsck) of the root filesystem failed a manual fsck is performed... root filesystem is currently in read-only mode"

So I told her to do a manual fsck, and this is what she gets...

 "fsck(8)
name: fsck check and repaid linux file system


description: fsck is used to check and optionally repair one or more linux file systems. filesys can be a device name (eg: /dev/hdc1, /dev/sdb2), a mount point (eg: /, /usr. /home), or an ext2 label or UUID
if no filesystems are specified on the command line, and the -A option is not specified, fsck will default to checking file systems in /etc/fstab serially. this is equivalent to the -As option
the exit code returned by fsck is the sum of the following conditions: 0 - no errors




I honestly have no idea. I don't use Ubuntu, so most of this doesn't make any sense to me, I don't understand how this system works... Can anyone help me please??

---

### Post by MacGyver666 on 2010-01-20
Anyone?

---

### Post by _H3MLOCK on 2010-01-20
I don't recall Ubuntu ever giving me a %age while booting. 
Firstly, describe the boot a little more clearly... how does she fsck? does it drop her into a command line? does it boot? did she use a livecd? has she tried safe mode? what were the results?

Also post output of uname -a  and dmesg

---

### Post by SchizmWolf on 2010-01-20
What kind of system are you using? We need some details on your system if we're going to be able to help. If you don't know, try the following to get some info:
1) boot with the LiveCD and run the command 
2)enter: ```
 sudo cat /proc/cpuinfo 
```
3)Give us the specs. It may help

I'm just taking a shot in the dark since I've never had this problem, but could one of your partitions be damaged? To check that, go once again into the terminal and type ```
 sudo fdisk -l
```A healthy partition table should look something akin to: ```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris 
```Just a guess, but maybe it'll help.

---

### Post by _H3MLOCK on 2010-01-21
I still need to identify exactly what is going on... It stops, tries to auto fsck, fails, tells you to do it manually.... THEN WHAT HAPPENS???   and what happens if you boot into safe mode?

---

### Post by cenzorrll on 2010-01-21
it sounds like there is an error in the filesystem that is stopping the automatic filesystem check.

in order to do a manual filesystem check you need to enter:
```
fsck /dev/sdax
```
where "x" is the number of the partition with ubuntu

you can do the fdisk command posted earlier and that will tell you what partitions are there (you'll be looking for an ext partition) and just put that in for your fsck command.

that should fix it.

---

### Post by MacGyver666 on 2010-01-21
> **_H3MLOCK said:**
> I don't recall Ubuntu ever giving me a %age while booting. 
Firstly, describe the boot a little more clearly... how does she fsck? does it drop her into a command line? does it boot? did she use a livecd? has she tried safe mode? what were the results?

Also post output of uname -a  and dmesg

It only does a load % when she shuts down improperly, she had said. It was an auto fsck, and then I made her do a manual fsck. It does not boot. She does NOT have a live cd, as of yet... And I'm not sure about the rest. I'm going to go over to her place later on and post more info when I get it. Thanks for your help!!

---

### Post by MacGyver666 on 2010-01-21
> **SchizmWolf said:**
> What kind of system are you using? We need some details on your system if we're going to be able to help. If you don't know, try the following to get some info:
1) boot with the LiveCD and run the command 
2)enter: ```
 sudo cat /proc/cpuinfo 
```3)Give us the specs. It may help

I'm just taking a shot in the dark since I've never had this problem, but could one of your partitions be damaged? To check that, go once again into the terminal and type ```
 sudo fdisk -l
```A healthy partition table should look something akin to: ```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris 
```Just a guess, but maybe it'll help.

Thanks a lot! I'm going to go to her place this afternoon, then I'll post all this info!

---


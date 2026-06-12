---
title: "Karmic updates killed my system"
date: 2010-05-02
forum: General Help
---

### Post by RRK on 2010-05-02
I am running Karmic on two PC's.  One is a  32-bit and the other a 64 bit machine. Yesterday (May 2) I ran the system update manager on the 64-bit, it requested  a restart. All is well. I then ran system update manager on the 32-bit, restarted and it could not mount my "D-Drive".

I have one hard disk on the 32-bit PC. The partition with photos and music I named D-Drive, it's an NTFS format.  The rest of the hard drive is split between primary Ubuntu partition and Linux swap partition.

It allowed me access to a command line where I discovered that /media/D-Drive no longer existed. I created it with SUDO MKDIR D-Drive.

Now it's worse.  It can't mount the swap drive and it does not give me a stable command line. ( I was able to enter a command once - vi /etc/fstab. It wasn't a workable vi. I could do nothing except view fstab in what appeared to be a vi editor. I also get a red screen sometimes - very lovely.

Any ideas? Anyone. I don't want to lose my photos, although most are burned to cd or dvd the most recent ones are not (Burner died and I have not replaced it).

Solved:  

Found another post that resolved this.

created /mnt/2Gb.swap file 
filled it with /dev/zero
swapon -a /mnt/2Gb.swap
updated fstab by removing the UUID entry for swap and replacingit with /mnt/2Gb.swap none swap sw 0 0
rebooted - All is good.

---

### Post by beastrace91 on 2010-05-02
Can you boot from a liveCD/USB drive and see if you can access your files as normal? Live mediums make wonderful recovery medium.

~Jeff

---


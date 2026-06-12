---
title: "low disk space or system error"
date: 2012-05-04
forum: General Help
---

### Post by WinfriedG on 2012-05-04
**Earlier thread on  Low Disk Space was declared as solved; therefore this new thread**
Well unfortunately the problem is not solved for me:

I aim using Lubuntu on an Acer Aspire One netbook with 8GB solid state disk.
I partitioned  it in 2 partitions
sda1(ext4):  /boot with 100MB as primary partition
and an extended partition  sda2 of 7.6 GB
containing 
sda5 (ext4)  /                with 5.6 GB fo the system
sda6(ext4)  /home         with 1 GB
and 
sda7  a swap partition of 1GB


In an earlier thread on low disk space a script was proposed:
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs -p sudo apt-get -y purge
```This script freed about 600 MB on my "/" partition  but it did not free  anything on my /boot partition. The filemanager says still that only 3.5  of 100 MB are free.
The report of this script shows the following end:
....
     
 >   initramfs-tools (0.99ubuntu wird eingerichtet( will be installed)
 ... update-initramfs: deferring update (trigger activated) 
Trigger für initramfs-tools werden verarbeitet (will be processed) ... 
update-initramfs: Generating /boot/initrd.img-3.0.0-17-generic  
gzip: stdout: No space left on device E: mkinitramfs failure cpio 141 
gzip 1 update-initramfs: failed for /boot/initrd.img-3.0.0-17-generic with 1. 
dpkg: Fehler beim Bearbeiten von (error when processing) initramfs-tools (--configure):
  Unterprozess installiertes post-installation-Skript gab den Fehlerwert 1 zurück 
(subprocess generated post-installation script returned error-value 1) 
Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist 
Fehler traten auf beim Bearbeiten von: 
(No Apport-Report was created, since the limit MaxReports was already reached. 
The error occured when processing
initramfs-tools E: Sub-process /usr/bin/dpkg returned an error code (1) The German phrases I translated into phrases in brackets(...)

I deleted manually with the filemanager all the old versions of the kernel and boot files in the boot  partition; the names disappeared but this did not make any effect on the  used space of the partition as shown by the filemanager.
I installed baobab and it says that folder boot stores 11 objects with 22 MB. Which would leave som 78MB free. But when I try to update to kernel 3.0.0.19 I get the message "low disk space on the boot partition"
It seems that some programmes are in disagreement on the free disk space in partition /boot
Any idea what I should do?

---

### Post by WinfriedG on 2012-05-04
:) SOLVED: I found a .Trash-0 folder in /boot, which obviously contained all the files I deleted. I removed this folder and now my free space on partition /boot is 67 MB.

---

### Post by llamabr on 2012-05-04
you'll also find a ~/.local/share/Trash/

also, do an sudo apt-get clean

to get rid of old .deb files

---


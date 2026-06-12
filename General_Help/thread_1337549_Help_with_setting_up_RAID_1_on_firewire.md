---
title: "Help with setting up RAID 1 on firewire"
date: 2009-11-25
forum: General Help
---

### Post by sford422 on 2009-11-25
I installed Ubuntu 9.10 on a MacMini, and want to setup a RAID 1 on two external firewire drives.  I am running into a couple of issues, and have not been able to find the answers to them.  First of all, the MacMini has only one FireWire 800 port.  I connected each of my 1.5 TB  drives to the Mini one at a time and formatted them for Linux using fdisk.  The drives I am using each have two FW800 ports on them.  I daisy chained the two drives together and connected them to the Mini.  Once connected, used the 'sudo fdisk -l' command to check that both drives were showing up fine.  Both drives do show up, but fdisk is displaying a message saying 'WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.'  If I type sudo fdisk -l, there is definitely nothing stating that I'm using GPT.  If I connect the drives one at a time, I don't get this warning.  My first question is does fdisk not support daisy chaining drives?

Second, if I move forward with tying to create a RAID1 on the two drives using the command...

'sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1'

I get the following output...

mdadm: size set to 204736K
mdadm: largest drive (/dev/sdb1) exceed size (204736K) by more than 1%
Continue creating array?

RAID1 should support 1.5TB, right?  

Thanks in advance!

---


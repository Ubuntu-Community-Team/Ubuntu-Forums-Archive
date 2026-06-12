---
title: "Manually Mount My Partition, Man! + GRUB2 failure"
date: 2012-03-10
forum: General Help
---

### Post by janisgeiger on 2012-03-10
blkid

/dev/ramzswap0: TYPE="swap" 
/dev/sda3: LABEL="Vista" UUID="06F0F04C02B31EF7" TYPE="ntfs" 
/dev/sda5: LABEL="Multimedia" UUID="802401cd-9ec0-49a8-a0e7-93f31fbb72aa" TYPE="ext4" 
/dev/sda6: LABEL="Recording" UUID="b89c2b00-b4d1-4375-af1f-1005cde6eef2" TYPE="ext4" 
/dev/sda7: LABEL="Label" UUID="d1a517a2-2aff-44f4-be66-212aceaeeb87" TYPE="ext4" 
/dev/sda8: UUID="094829cf-3029-4035-9a6e-44d3fa38e0bb" TYPE="swap" 
/dev/sda9: LABEL="Listening" UUID="99233393-21cb-45a3-b315-857492627401" TYPE="ext4" 
/dev/sda10: LABEL="Backup" UUID="cf74658e-f008-443c-8319-d2e119426ab0" TYPE="ext4" 
/dev/sda11: LABEL="Working" UUID="4b9269d7-3f1e-440d-b182-e464e0d5c754" TYPE="ext4" 

(sudo) mount /dev/sda5 : can't find sda5 in /etc/fstab or /etc/mtab

I don't care for these files. When I open pcmanfm or Nautilus, they can mount them. Why can I not?


error, unknown filesystem
grub rescue >
set

set prefix=(hda0,8 )/boot/grub
set root=hda0,8


set prefix=(hda0,7)/boot/grub
set root=hda0,7


Grub appears nicely then & works


how to save hda0,7, then?

---

### Post by raja.genupula on 2012-03-10
look at the instructions 
[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting)

---

### Post by janisgeiger on 2012-03-10
i've read them.

and I changed them every time I restarted the computer, which enabled me to boot fine. But they just didn't get saved... So I had tell it to grub every time.

 The solution was the command

sudo grub-install /dev/sda

*smartass-mode* Against my dogma not to re-install. cause it's working fine, just two lines have to be changed, somewhere. Probably inside core.img. But, whatever...

---

### Post by oldfred on 2012-03-11
We like to spend days fixing things. But some just reinstall as it can be only an hour.

Did you solve your mounting issue?

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a
examples:

UUID=01CC498FE4856480 /media/Data2 ntfs defaults,uid=1000,nls=utf8,umask=000 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
UUID=66E4DC83E4DC56C1 /media/Data2 ntfs defaults,uid=1000,windows_names,umask=000 0 0

---


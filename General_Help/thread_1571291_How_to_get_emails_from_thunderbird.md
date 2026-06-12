---
title: "How to get emails from thunderbird"
date: 2010-09-09
forum: General Help
---

### Post by rapattack1 on 2010-09-09
Hi I killed my motherboard and have to put my hard drive into another machine as a slave to get the emails and other data. Where do i find my emails from thunderbird and can i open the emails from the install of Ubuntu in the other machine? Can i mount and read a drive that was a master and now is a slave?;)

---

### Post by josephpmh on 2010-09-09
Try /home/[user]/.mozilla-thunderbird/[xxxxxxx].default/Mail/

Since you're looking to recover emails on your hard drive, I'm assuming your looking for your pop email account(s).

---

### Post by rapattack1 on 2010-09-09
Hi thanks seems i am having some trouble mounting the hard drive. I am never good at that for some reason.
Thanks will check that info when i can mount it. I am using a usb device as it is a sata drive.
The mycomputer folder sees the drive and i selected mount but i got 'unable to mount location
DBus error org.gtk. Private.RemoteVolume.Monitor.Failed
An operation is already pending

then i double clicked in the media directory and got after quite a wait:
Unable to mount 77gb system
error mounting :mount exited with exit code.32.mount.wrong fs type, bad option, bad super block on /dev/sdb1, missing code page or helper program or other error in some cases useful info is found in syslog-try dmesg|tail  or so


I don't know anything about syslogs so i didn't do anything with that but i did the dmesg|tail command and the last line said EXT4-fs(sdb1):unable to read superblock

If you wish to to post this separately I will :0)

---

### Post by rapattack1 on 2010-09-12
Well i got my hard drive to mount and i found the folder but i don't know how to get it to read in thunderbird. I know when i installed mozilla-thiunderbird just now on this newly installed ubuntu pc it ask if i wanted to import anything but the radio button only gave one choice which was 'no'. So not sure what to do from here? :0) Would appreciate your help :0)

---

### Post by jv2112 on 2010-09-12
Follow josephpmh's direction. Just use the cp command to copy from your old drive to the new drive (just overwrite the new: with a fresh install nothing should be there)

Location

/home/[user]/.mozilla-thunderbird/[xxxxxxx].default/Mail/


Hope this helps.

---

### Post by rapattack1 on 2010-09-12
Sorry can't remember hopw to use the cp command i am afraid. Um i did download some messages just after the install of thunderbird so i wouldn't want to overwrite them.

---

### Post by rapattack1 on 2010-09-20
Hi can anyone help? I have now installed Ubuntu 10 on my spare machine and installed thunderbird but i can't find the directory thunderbird. It is not under Mozilla. Can you tell me where it is and how to do the cp thing?

---

### Post by piratebill on 2010-09-20
> **rapattack1 said:**
> Hi can anyone help? I have now installed Ubuntu 10 on my spare machine and installed thunderbird but i can't find the directory thunderbird. It is not under Mozilla. Can you tell me where it is and how to do the cp thing?

You have to run thunderbird before the directory is created

---

### Post by rapattack1 on 2010-09-21
Oh sorry i got it working by myself. I just dragged the directory that i copied manually from the old system(had stored on a thumb drive) into this this install of Ubuntu and ran thunderbird for the first time and it saw the directory and imported everything in there...wow that was easy!!!!!:)

---


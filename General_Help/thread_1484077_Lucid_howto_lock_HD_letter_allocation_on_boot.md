---
title: "Lucid: howto lock HD letter allocation on boot?"
date: 2010-05-15
forum: General Help
---

### Post by Byb on 2010-05-15
Hi all
I can't find how to prevent Lucid to change the letters of the drives.
On install, it was karmic, I installed / and /tmp in my /dev/sda IDE (bios HDD-0) and /var /home and /swap in a addin /dev/sdb SATA (bios called SCSI, bios overlay channel-0)
Then I made some changes: added a /srv partition in the sdb, and changed fstab to use uuid instead of /dev/sdx. Everything was ok until I upgraded to lucid. I began to get the grub screen on boot.
Now every time I reach to recover a normal boot (e.g. I removed uuids in fstab from command line), I check gparted or other utilities and I check OK that HDD-0 is sda and SATA is sdb, on next boot I get again the console screen after fscheck stating it can't find this or that.
Is there a way to check there is no MBR in my SATA that could drive Linux to an error?
How/when are the devices detected by the BIOS passed to Linux? Is there a way to override them? I never enabled boot from SCSI(SATA) in the bios all worked OK. Could tools like bootparm or rdev could help? I'm full newb.

How to force Linux to know that / is in HDD-0 AND keep grub MBR on this same drive? I don't want nothing related to boot in the SATA drive.
PS: In liveCD 10.04, sda is my IDE and sdb is my SATA, so it's seems OK, but after a successful re 
sudo grub-install --root-directory=/media/sda /dev/sda, on first reboot it's OK, and on the next it's dead again
[EDIT] since lucid I also get this on boot, don't know if related: > init unreadahead main process (224) terminated with status 5sometimes its (232)
THanks for help, and excuse my poor english. I had no help in french forums

---


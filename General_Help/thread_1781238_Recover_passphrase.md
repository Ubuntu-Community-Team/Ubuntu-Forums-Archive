---
title: "Recover passphrase"
date: 2011-06-13
forum: General Help
---

### Post by Iqbal_ on 2011-06-13
Hi,
 Summary:
  A laptop with core 2 duo 64 bits, nvidia drivers, dual boot with vista and ubuntu 9.10. Three partitions for Vista and four for Ubuntu (/, /boot, /home and swap) total 500 GB HDD and 4GB RAM
   
  Ubuntu 9.10 was running smoothly. After the release of Natty, I installed it with nomodeset boot option (pressing F6). During installation, I selected the option of encrypting the /home directory. I used it for a day only. Next day, at the time of logging-in, the system hanged, thereafter nothing happened. I tried to reinstall Natty, it took more than usual time. Finally the installer crashed with a message of disk errors.
   
  Because Karmic was running successfully, I installed Karmic again with encrypted /home (Encrypted with 11.04) as /home. It also gave disk errors. Windows also informs that the disk may fail soon.
   
  Now if I boot from Natty’s Live CD the disk utility keeps on telling disk health problems. If I try to mount /home folder on /mnt and try to CD /mnt - Input/Output error comes up. Suddenly, if I fdisk –l, not partition is listed, though there are eight (8) partitions. GParted also showed that no devices found. If I reboot them this issue disappears and fdisk –l lists all partitions.
   
  I rebooted with Natty’s Live CD and could reach to the point to issue the command ecryptfs-unwrap-passphrase /home/username/.ecryptfs/wrapped-passphrase.
   This command gave following massage:
  _ _
  _ecryptfs-unwrap-passphrase: error while loading shared libraries: libecryptfs.so.0: can not open shared object file: No such file or directory_
  _ _
  My problem is
  [FONT=&quot]1-     [/FONT]How to recover passphrase
  [FONT=&quot]2-     [/FONT]Recover data
  3- How to know that wrapped-passphrase file is there?

---

### Post by Grenage on 2011-06-13
Without the passphrase, you're not going to get anywhere.

You mentioned that there were various disc errors, including those mentioned while in Windows.  Are you sure the drive isn't dying?

---

### Post by Iqbal_ on 2011-06-13
Hi,
As both the OS are reporting that the disk has health problem. But from LiveCD I can have backed-up windows files. At times I can also mount /home (encypted) directory.
 I tried to run fsck several times without success.

---

### Post by Mark Phelps on 2011-06-13
Sorry ... but to support what was said about your first question, there is simply no way to recover the passphrase, short of brute-force password guessing techniques -- which, even if you have a VERY power computer at your disposal, will take anything from weeks to YEARS to complete.

If there was a simple and quick way to recover it, then encryption wouldn't be of any real value.

---


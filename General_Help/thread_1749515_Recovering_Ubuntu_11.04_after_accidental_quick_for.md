---
title: "Recovering Ubuntu 11.04 after accidental quick format"
date: 2011-05-04
forum: General Help
---

### Post by sheperson on 2011-05-04
Hi,
I had Ubuntu 11.04 on my 160 GB HDD, along with two more NTFS partisions.
Yesterday, I decided to install Windows XP on my Flash Drive, but I accidentally (quick)formatted the whole disc.
I then tried to recover the lost partitions using TestDrive, and almost succeeded.
Then I re-installed GRUB using the Ubuntu disc.
The first time I ran Ubuntu afer recovery, I got an error message about some inodes. Then I checked the Ext4 partition using e2fsck, and fixed the error.

Now, when I boot into Ubuntu, I get a message like "ureadahead main process (NNN) terminated with status 5" and nothing else happens.

Can anyone guide me to any clues where I can look for what is going wrong?

Thanks in advance.

---


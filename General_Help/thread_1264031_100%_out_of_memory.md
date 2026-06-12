---
title: "100% out of memory"
date: 2009-09-11
forum: General Help
---

### Post by Vostrocity on 2009-09-11
Yesterday, I installed two rather large programs, and apparently that pushed my Ubuntu partition to 100% (which I confirmed in Process Monitor). I tried to launch Synaptics to uninstall something but that failed (due to the same disk space problem). So then I restarted hoping that would magically do something, only to find that I can't even log in now, also due to the disk space problem. My last resort would be to enlarge the partition yet again, but I'm hoping there's another solution.

---

### Post by oldfred on 2009-09-11
Are you able to get to a command line?

If so this are my notes on housekeeping from several threads:
HouseKeeping:
# removes .deb
sudo apt-get autoclean
sudo apt-get autoremove
# also computer janitor in system-admin
# see grub cleanup to remove old linux versions or use synaptic
# empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB

---

### Post by Vostrocity on 2009-09-12
I couldn't wait to get back on Ubuntu so I just extended an extra GB onto the partition. :D But if anyone has a solution for future reference, that's fine.

EDIT:
@oldfred
Thanks for the suggestion but I couldn't logon at all, so no command prompt.

---

### Post by MaxIBoy on 2009-09-13
[LIST=1]
[*]Boot from a LiveCD.
[*]Mount your root filesystem somewhere (for example /media/ubuntu_filesystem)
[*]Run the command "sudo chroot /media/ubuntu_filesystem"
[*]Now it's as if you've booted from your main ubuntu installation, but you're actually running from the CD.
[/LIST]

Also, a major killer of disk space is old kernels, that's usually the first thing I go for.

---


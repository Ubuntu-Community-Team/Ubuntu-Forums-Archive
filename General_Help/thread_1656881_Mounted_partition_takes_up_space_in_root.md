---
title: "Mounted partition takes up space in root?"
date: 2010-12-31
forum: General Help
---

### Post by kei-clone on 2010-12-31
Hi. Today I was notified on my netbook that my root folder is running out of space. When I ran the disk analyzer, it showed that most of the space is going towards the videos folder in /media/win7. My ~/Videos folder is symbolically linked to the videos folder on my Windows partition, which is mounted in my fstab using ntfs-3g under /media/win7. The question now is, shouldn't the videos only exist in the windows partition? /media/win7 usage shouldn't affect space usage in my root folder right?

---

### Post by kei-clone on 2011-01-01
bump?

---

### Post by oldfred on 2011-01-01
You are correct, your data only exists in one place although a link may nake it look like it is someplace else. That should not relate to the message of low space.

I have had some tools show a partition directly mounted into my /home show as part of the data in /home and hidden files not counted. So it depends on what you use to see amount of data.

What does this show?
df -H

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

# empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

# check sizes of 
cd /
sudo du -hc --max-depth=1

df -Th | sort

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by kei-clone on 2011-01-01
good call, apparently I really was running out of space after all and it had nothing to do with that. Thanks for the tips, they were really helpful!

---

### Post by kei-clone on 2011-01-01
good call, apparently I really was running out of space after all and it had nothing to do with that. Thanks for the tips, they were really helpful!

---

### Post by kei-clone on 2011-01-01
good call, apparently I really was running out of space after all and it had nothing to do with that. Thanks for the tips, they were really helpful!

---

### Post by kei-clone on 2011-01-01
argh, can't delete the multipost. internet spazzed out on me, apologies

---


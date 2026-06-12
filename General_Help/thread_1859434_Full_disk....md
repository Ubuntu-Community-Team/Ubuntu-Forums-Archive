---
title: "Full disk..."
date: 2011-10-13
forum: General Help
---

### Post by maghoxfr on 2011-10-13
Hi all,

My ubuntu partition is crammed with I don't know what really because I store all my music, pics and videos on another partition. I don't believe I have so many apps installed as to take the whole 8Gb of it.

Is there some command or app that I can run so it tell me which is the biggest folder on my system?

I have cleaned up from everything non-software and I don't know what is taking so much space. But everyday I have less and less free space.

Thank you

---

### Post by MarjaE on 2011-10-13
I have the same problem.

---

### Post by erind on 2011-10-13
> **maghoxfr said:**
> Hi all,
...
Is there some command or app that I can run so it tell me which is the biggest folder on my system?

I have cleaned up from everything non-software and I don't know what is taking so much space. But everyday I have less and less free space.

Thank you

My preferred way would be using **find **for biggest files:

```
sudo find /home -type f -ls | sort -nr -k7 | head
```To get a mixed output files+directories you can use **du**:

```
sudo du -ab /home | sort -nr -k1 | head
```Adjust **/home **directory to your needs, and **head **options to see more than 10 lines.

---

### Post by MarjaE on 2011-10-13
In my case, the top three were from Tracker. The fourth was from when my brother tried to batch-process some pdfs and crashed the computer. Deleting Tracker...

---

### Post by oldfred on 2011-10-13
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n

gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---


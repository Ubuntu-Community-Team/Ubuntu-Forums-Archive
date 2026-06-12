---
title: "Running out of space but I cant free it up"
date: 2010-11-22
forum: General Help
---

### Post by aresfiend on 2010-11-22
Ubuntu software center keeps telling me that I cannot ad or remove any data until it repairs open arena. Problem is that the harddrive has all of 40 megs left. Please help so I can continue to use ubuntu, this morning I was gong to completely switch from windows on my laptop but could not figure out how to make the entire harddrive become one partition without the disk, so now I am rapidly running out of space for ubuntu.

---

### Post by oldfred on 2010-11-23
Not sure about your specific problem. But you can run these to houseclean and refresh system.

#houseclean
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade
sudo apt-get -f install
suod dpkg --configure -a

---

### Post by aresfiend on 2010-11-23
Okay, this may be a bit clearer. I tried to install a game via the software center & ran out of space before it finished. Now I cannot get enough free space for the repairing broken deps thing to finish so I can remove all of the data that is with the game.

---

### Post by nolag on 2010-11-23
How much space did you have originally?  Why not do a search for all files bigger than say a gig and see if you can remove any (I once had a backup that was in the wrong spot it took 80GB and that was how I found it)?  Also see if there are huge folders with things you no longer need (sometime a lot of medium sized files take a lot of space).  Do you have your personal files on a seperate partition or the same partition as the installation by the way?

---

### Post by oldfred on 2010-11-23
If you want to look for large files:

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by aresfiend on 2010-11-23
The partition is 5gb (but is only showing as 1.7) and I am not able to remove the data associated with the game without the ubuntu software center, which is not letting me do anything until it repairs the libraries

---


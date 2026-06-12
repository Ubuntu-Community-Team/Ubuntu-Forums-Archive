---
title: "update problem"
date: 2011-11-23
forum: General Help
---

### Post by fairoz on 2011-11-23
Hi to all ubuntu friends
 i am using ubuntu for the last two month and i got a problem when i try to update i get is message



W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ae.archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ae.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_source_Sources  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

i dont know what is it  can some one help me i am use ubuntu 11.10 on laptop aspire 5735z

thank you

---

### Post by ventsyv on 2011-11-23
Sounds like the bzip package got broken. Try the following:
apt-get check - check if there are any broken packages
apt-get clean - remove packages files
apt-get repair - To repair broken packages. If you ran the clean command above, the package files will be re-downloaded

You might also want to try

apt-get update - to update to the latest versions.
Good luck

---

### Post by ajgreeny on 2011-11-23
If you remove any files in **/var/lib/apt/lists/partial/** and then run ```
sudo apt-get update
``` you may solve the problem.

---


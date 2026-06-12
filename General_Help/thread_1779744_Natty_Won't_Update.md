---
title: "Natty Won't Update"
date: 2011-06-10
forum: General Help
---

### Post by Luther786 on 2011-06-10
Hello everyone

I am pretty sure I must have done something weird or something went wrong in the install, but I am having an issue now.

I cannot get the update or software center to work now that I am running natty. When I try to update manager it says "E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened"

How do I fix this? I assume that the software center has something to do with this too...

---

### Post by linuxinstalledfromhdd on 2011-06-10
sudo rm -vf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get upgrade

---

### Post by Luther786 on 2011-06-10
Thank you!!!

---

### Post by linuxinstalledfromhdd on 2011-06-10
You are welcome. If you would like to mark this thread solved above that would be great.

---


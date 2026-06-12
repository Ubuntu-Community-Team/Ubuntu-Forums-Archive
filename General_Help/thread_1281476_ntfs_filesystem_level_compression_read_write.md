---
title: "ntfs filesystem level compression read write"
date: 2009-10-03
forum: General Help
---

### Post by sea_monkey987 on 2009-10-03
does the ntfs-3g driver safely support reading and writing to a compressed ntfs filesystem?  i would just try it...but i don't want to corrupt my data

---

### Post by Wild_Doogy on 2009-10-22
Unfortunatly, I dont know the answer to that, but I do have some info that might be helpful. I have a 200Gb hdd with ubuntu 9.04, and windows on it. a few of the folders are compressed, (program files, my documents) and I can read and write from those folders fine. I have been using this setup for almost 2 years and I haven't lost any data. I have had problems but I can trace most of them to fooling around with gparted. :twisted:

I will say however, that I have not had a windows installation last longer than 3 weeks, and I am wondering what the heck it causing that. at the moment I have just reinstalled windows, and I am uncompressing the entire harddrive. (gonna need a major defrag....)
but anyways. I think your data should be safe, but don't rely on your windows installation, I seem to kill them.

IMPORTANT TIP/FACT:
There is a program called Testdisk, and I want to bow down in awe to the creator. I blew my entire 200 GB of data out the window (Resize cancled in the middle (what the HECK was I thinking :confused:)) and testdisk got it ALL back. Also, my dad had a head crash on his hardrive with all the buisness records on it and I was able to extract the important data from that as well.

Wild_Doogy

---

### Post by renkinjutsu on 2009-10-22
also worth noting, i think you need to perform a chkdsk upon booting up to windows everytime you've written to your ntfs partition using linux.. (that was the case when i had windows on this computer)

---

### Post by DeMus on 2009-10-22
> **renkinjutsu said:**
> also worth noting, i think you need to perform a chkdsk upon booting up to windows everytime you've written to your ntfs partition using linux.. (that was the case when i had windows on this computer)

When I still had NTFS partitions I never had any problems reading and writing them. Never lost data. So I think it is pretty safe.

---


---
title: "File Sharing Problem"
date: 2011-06-22
forum: General Help
---

### Post by ssreddy555 on 2011-06-22
On Ubuntu 11.04.
 
I have got two issues:
 
I have installed themes from Synaptic Package Manager. They do not appear in the default Theme Manager or in any folder in Nautilus. Where can they be found?
 
Secondly, on one machine (A), I have installed 11.04 via WUBI & In another (B), directly on to the partition. 
 
Where as in the machine B, I can see File Sharing Options in the right click menu of the folders in the Nautilus, I cannot find these options in A.
 
On both the machines, Samba is installed. In addition, in both the machines, Apache is also installed. 
 
I have enabled File sharing in the System settings > Personal File Sharing Options in A.
 
Now, I can mount the files of B in A but not in the reverse from commandline (sudo <IP of B>:/ ./<Folder in B> after enabling file sharing of the particular folder to be shared, from the right click options). Why are the file sharing options not seen in WUBI machine in the right click menu of folders? Is it normally so in WUBI machines?

---

### Post by mastablasta on 2011-06-22
could be because of Wubi as Wubi is basically a giant file within windows system. it is installed within windows. and it is runnign a type of virtualization. it is goot to try out the system but it's is not how the OS should be installed.

---

### Post by jerrrys on 2011-06-22
themes usually end up in

filesystem>user>share>icons

what is the name of the theme?

---

### Post by Morbius1 on 2011-06-22
> Where as in the machine B, I can see File Sharing Options in the right click menu of the folders in the Nautilus, I cannot find these options in A```
sudo apt-get install nautilus-share
```> On both the machines, Samba is installed. In addition, in both the machines, Apache is also installed.Apache is not required for Samba
> I have enabled File sharing in the System settings > Personal File Sharing Options in A.You have enabled a certain type of file sharing which in fact does require an apache package and also an avahi package. But this is not Samba File Sharing.

---

### Post by ssreddy555 on 2011-06-22
> **jerrrys said:**
> themes usually end up in

filesystem>user>share>icons

what is the name of the theme?

I have installed Metacity themes, x-cursor themes & light theme from Synaptic.

In the location u have indicated, only the default themes are found.

---

### Post by ssreddy555 on 2011-06-22
> **Morbius1 said:**
> ```
sudo apt-get install nautilus-share
```This worked like a charm.
Thanks a lot!

---

### Post by jerrrys on 2011-06-22
user/share/themes

---

### Post by ssreddy555 on 2011-06-22
> **jerrrys said:**
> user/share/themes

Yes, I find them here.

How to use them? Can they be tampered with like any other folder? I'm asking because I was rather wary of touching the files in 'FILE SYSTEM" because I thought they are system files and should not be touched.

Next, I am already running Compiz. Can I use Metacity themes or will it cause some problems? I have already experienced annoying problems with Compiz like disappearence of Desktop  Panels. In fact, once I had to reinstall the OS as nothing seemed to work.

---

### Post by jerrrys on 2011-06-22
i do not run compiz.  so i am of no help on that.  xubuntu uses gtk themes, compiz is not installed.  not by default atleast

---


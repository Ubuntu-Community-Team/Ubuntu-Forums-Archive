---
title: "Backing up settings"
date: 2010-07-10
forum: General Help
---

### Post by groonrix on 2010-07-10
Hio.
After installing Ubuntu for the first time (dual boot, one partition for Win XP and another one for Ubuntu), I decided that I would like to restructure my HD's partitions,
and create a Win partition, an Ubuntu home partition and a third Ubuntu partition.
I think this is a good time to repartition, since all of my documents were backed up recently.
All I need to back up is Ubuntu's settings (key bindings, theme, etc.) and the software packages I downloaded (from apt-get, Ubuntu Software Centre).
Is there an easy way to do so?
Thanks in advance.

---

### Post by aeiah on 2010-07-10
there are a number of methods.. the simplest thing to do would be to copy your settings from your home directory. if you open your home dir with nautilus and so ctrl+h you'll see hidden files and folders (ones beginning with a dot). these'll house all your settings. you could just copy these somewhere and then copy them back when you have things up and running again.

as for the keyring stuff, im fairly sure there'll be more to it than that, and you might want to search just for backing up gnome-keyring etc.

as far as apt-get goes, you'll probably have stuff in the apt cache, although just saving that will only mean you dont have to download the debs again. perhaps something like aptoncd or a custom script will be more suitable for automating the process. there's a few solutions dotted around these forums and elsewhere.


or, if you have the hard drive space for it, you could use dd to take a bit-for-bit image of your partition and then copy it back when you're done. because your partition structure will have changed, you'll have to make sure you edit /etc/fstab to get your partitions all lined up again.

or, instead of dd you could use rsync. likewise, you'll still need to edit fstab since partitions will have changed.


to be honest, the easiest thing to do would probably be to do a fresh install, install things you need with synaptic, and then just copy over your settings

---

### Post by groonrix on 2010-07-10
Thanks!
I think I'll stick with your advice and reinstall.
A few questions:
1. Should I copy ALL the hidden files in my home folder?
2. What is that keyring thing you're referring to? Something that has to do with the root password?
3. Where is this apt cache located? And is there some textual log file containing the names of all debs I downloaded (from Ubuntu software centre also)?

Thanks!

---


---
title: "Broken package help"
date: 2012-05-11
forum: General Help
---

### Post by Biciclettapc on 2012-05-11
Need some help with broken packages.  I was trying to install gimp 2.8.

[I]Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 19.1 MB in 1min 58s (161 kB/s)                                         
Reading package lists... Done
paul@paul-K53E:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
paul@paul-K53E:~$ sudo apt-get clean
paul@paul-K53E:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (<= 2.6.12-z) but 2.8.0-1ubuntu0ppa3~precise is installed
        Depends: gimp-data (<= 2.6.12-z) but 2.8.0-1ubuntu0ppa3~precise is installed
E: Unmet dependencies. Try using -f.
paul@paul-K53E:~$ 
[/I]

Thanks 
Paul

---

### Post by kc1di on 2012-05-11
hi Paul,

try this command in a terminal see what happens:

```
sudo dpkg --configure -a
```

---

### Post by Enigmapond on 2012-05-11
From where are you attempting to install the 2.8? If it's from the new PPA then try this. If you have synaptic installed it's easier. Purge everything GIMP on your system not just delete as you need to get rid of any config files. Delete any .gimp folders in your home directory, backing up any brushes or added things. Then install gimp-data first, then gimp and then anything else. This worked for me and 2.8 works very well in 12.04.

---

### Post by Biciclettapc on 2012-05-11
> **Enigmapond said:**
> From where are you attempting to install the 2.8? If it's from the new PPA then try this. If you have synaptic installed it's easier. Purge everything GIMP on your system not just delete as you need to get rid of any config files. Delete any .gimp folders in your home directory, backing up any brushes or added things. Then install gimp-data first, then gimp and then anything else. This worked for me and 2.8 works very well in 12.04.

from Unixmen using commands

[I]sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp[/I]

---

### Post by Biciclettapc on 2012-05-11
removal from synaptic and re-installed seems to work!

Thanks
Paul

---


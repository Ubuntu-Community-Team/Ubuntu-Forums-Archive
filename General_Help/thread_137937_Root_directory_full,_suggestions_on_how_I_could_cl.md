---
title: "Root directory full, suggestions on how I could clean it up a bit?"
date: 2006-02-28
forum: General Help
---

### Post by brynjarh on 2006-02-28
My root directory is full and I need free space there right now, is there any way to clean it up a bit without damaging anything?

df:
```
**/dev/hda1               270969    270905         0 100% /**
varrun                  112028       104    111924   1% /var/run
varlock                 112028         8    112020   1% /var/lock
udev                    112028       152    111876   1% /dev
devshm                  112028         0    112028   0% /dev/shm
/dev/hda6              2885780    868720   1870472  32% /var
/dev/hda9             66951800   2460888  61089956   4% /home
/dev/hdb1             78145768   3877524  74268244   5% /media/hdb1
/dev/hda8               369000      8349    340991   3% /tmp
/dev/hda5              5763616   1937076   3533760  36% /usr
```

ls
```
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old
```

---

### Post by Iandefor on 2006-02-28
Purge unnecessary packages?

---

### Post by GreyFox503 on 2006-02-28
Empty the lost+found and tmp directories.  Might buy you a little space.  And yes, purging old packages in synaptic.

EDIT:  I noticed several of your directories like /var, /usr, and /tmp are on different partitions.  Hmm...

---

### Post by tinker312 on 2006-02-28
Hi,

From what I understand, Ubuntu by default installs to / and then makes a swap partition during setup. Consequently your home folder and every application that you have installed is put into the / partition. 

Unless you manually edited the partitions during setup, you could burn then remove any music, movies, or uneeded application packages (tar files, zips) that you may have in your home directory or your desktop.
 
I suggest you stick to media files first. If that frees up enough space then your set, if it doesn't then remove tarballs and zip files until you have enough room. Hope that helps a little. 

Yours . . . 
John

---

### Post by RAOF on 2006-02-28
Clean up your apt-cache by running "sudo aptitude clean".  That'll delete any downloaded .debs from your /var/cache/apt/packages folder.

EDIT: Now that I actually **read** your df output, it's obvious that the above won't clear up anything on your root partition.  If you have more than one kernel installed, you could clear up **some** space by removing the old one(s)?

---

### Post by Iandefor on 2006-03-01
[quote=tinker312]Hi,

From what I understand, Ubuntu by default installs to / and then makes a swap partition during setup. Consequently your home folder and every application that you have installed is put into the / partition. 

Unless you manually edited the partitions during setup, you could burn then remove any music, movies, or uneeded application packages (tar files, zips) that you may have in your home directory or your desktop.
 
I suggest you stick to media files first. If that frees up enough space then your set, if it doesn't then remove tarballs and zip files until you have enough room. Hope that helps a little. 

Yours . . . 
John[/quote] Note how hda9 has been mounted as /home.

---

### Post by RAOF on 2006-03-01
[QUOTE=Iandefor]Note how hda9 has been mounted as /home.[/QUOTE]
And /usr, /tmp, and /var are also on separate partitions.  I'm not sure what he's actually **got** on his / partition ;)

---

### Post by brynjarh on 2006-03-01
[QUOTE=RAOF]Clean up your apt-cache by running "sudo aptitude clean".  That'll delete any downloaded .debs from your /var/cache/apt/packages folder.

EDIT: Now that I actually **read** your df output, it's obvious that the above won't clear up anything on your root partition.  If you have more than one kernel installed, you could clear up **some** space by removing the old one(s)?[/QUOTE]

I had more then one kernel installed, I removed thouse who where not being used and now I have 57% free space. \\:D/ 

So now I can continue working on [http://www.ubuntuforums.org/showthread.php?t=137569]("http://www.ubuntuforums.org/showthread.php?t=137569")

---

### Post by Zeroangel on 2006-03-02
[QUOTE=brynjarh]My root directory is full and I need free space there right now, is there any way to clean it up a bit without damaging anything?

df:
```
**/dev/hda1               270969    270905         0 100% /**
varrun                  112028       104    111924   1% /var/run
varlock                 112028         8    112020   1% /var/lock
udev                    112028       152    111876   1% /dev
devshm                  112028         0    112028   0% /dev/shm
/dev/hda6              2885780    868720   1870472  32% /var
/dev/hda9             66951800   2460888  61089956   4% /home
/dev/hdb1             78145768   3877524  74268244   5% /media/hdb1
/dev/hda8               369000      8349    340991   3% /tmp
/dev/hda5              5763616   1937076   3533760  36% /usr
```

ls
```
bin    dev   initrd          lib         mnt   root  sys  var
boot   etc   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
cdrom  home  initrd.img.old  media       proc  srv   usr  vmlinuz.old
```[/QUOTE]
You could run the command "du | sort -n" to find out which files/folders are taking up the most space.

If you don't plan on removing your secondary hard drives, you could also try symlinking your tmp folder there (if indeed space in /tmp is needed). There are also foreign (ie: chinese, arabic) font sets which take up tens of MB of hard drive space, which you could probably remove.

---

### Post by Iandefor on 2006-03-02
[quote=brynjarh]I had more then one kernel installed, I removed thouse who where not being used and now I have 57% free space. \\:D/ 

So now I can continue working on [http://www.ubuntuforums.org/showthread.php?t=137569]("http://www.ubuntuforums.org/showthread.php?t=137569")[/quote] Are you freaking kidding? It was the *kernels*? How many did you have installed?

---

### Post by Ramses de Norre on 2006-03-02
He has a 270MB root partition, all my installed kernels are like 1.2MB..

---

### Post by engla on 2006-03-02
[QUOTE=Ramses de Norre]He has a 270MB root partition, all my installed kernels are like 1.2MB..[/QUOTE]
No, a kernel is wayy bigger than this, more like
4M kernel
6M ramdisk
30M modules

All 1x per kernel

---

### Post by RAOF on 2006-03-02
My /lib/modules directory (which is on his / partition) is 80MB.  And that's just for the 2.6.15-16-amd64-k8 kernel.

---


---
title: "can not add an iso to software sources"
date: 2010-11-09
forum: General Help
---

### Post by irmtfan on 2010-11-09
i wanted to transfer all "archives" in my home pc to  my work pc. by using APTonCD i created an iso file then use these commands to mount it:
sudo mount /my/image.iso /media/apt -o loop
and use this and add it to repository softwares
sudo apt-cdrom  add

in /etc/apt/sources.list i have the line:
deb cdrom:[description]/ /
everythings seems ok but when i want to use it in synaptic or update manager i always have this error:
```

W: Failed to fetch cdrom:[description]/packages/PACKAGE.deb
  File not found

```how can i fix this?

---

### Post by sidzen on 2010-11-09
Open media
The first step is to put the CD/DVD created by APTonCD in the drive.

Select packages
When the media is read, it's showed a list with all packages available to restore. By default all packages are checked, but you can just uncheck the packages you don't want to restore.

Copy files
The packages selected are copied from the APTonCD media to /var/cache/apt/archives/ directory. This way the packages are available and you can install them using apt-get, aptitude or synaptic without need to download them.

Done this and still does not work?  Check to make certain all typing is 100% correct.  Best wishes!

---

### Post by irmtfan on 2010-11-16
yes of course i can use restore in APTonCD or copy all i needs to archives directory.
but i have low disk space and want to mount an iso or use my flash disk. (any outside storage)
anyway i want to know if its possible to add an iso or a directory other than /var/cache/apt/archives/_[]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CBYQFjAA&url=http%3A%2F%2Fwww.linuxquestions.org%2Fquestions%2Flinux-software-2%2Fvar-cache-apt-archives-lock-error-457486%2F&rct=j&q=var%20cache%20apt%20archives%20lock&ei=aD3jTKvjJ4mChQf9gqzODA&usg=AFQjCNEvzHV7M3kaupdbynZoTQzSCOGEVQ&sig2=SkNOS4V7JfcIjvn1DVX-QQ&cad=rja")_ directory to "software sources"

---

### Post by akademy on 2011-01-13
I mounted an iso then used its path to add it as a source. (It was the maverick ubuntu install CD if you are interested)

deb file:/path/to/mount maverick main

(The path should point to the "dists" folder, but not include it.)

---


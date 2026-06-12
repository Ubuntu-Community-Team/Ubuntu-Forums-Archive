---
title: "packages part of iso image file installation"
date: 2010-02-24
forum: General Help
---

### Post by dln9 on 2010-02-24
When I look in /var/cache/apt/archives/, I see packages I recognize that I downloaded.  But, I also see packages that I know I did not download, but rather were part of the initial installation of the image iso file on the CD.  For example, the package for Abiword is in there.  

I would like to know which packages in this directory I installed, and which were part of the initial installation.  

How do I know which packages are part of the installation from the image iso file on the CD?  Once I know that, I would make a copy of all the other packages in this folder onto a DVD, so if I ever need to reinstall Ubuntu 9.10 I will know which packages to install over and above those part of the initial installation off the iso CD.  

Thanks.

---

### Post by mrhippieguy on 2010-02-24
well, you'd boot ubuntu from the live cd, then check which packages are in there. i seem to remember 9.10 having the option to open a folder as the super-user. if it does, copy those packages(on the cd) to /var/cache/apt/archives, to replace the existing ones, then invert the selction, and copy those to your DVD.

there's probably an easier way, but that's what i got.

---

### Post by dln9 on 2010-02-24
Thanks hippie.  

Do you know which folder on the CD is the one that contains the packages?  When I looked in there, I didn't see a folder like that.  Or did I just overlook it?

---

### Post by mrhippieguy on 2010-02-24
i don't know which folder has them, but maybe you could find out after messing with synaptic for a while. i can't at the moment, somehow i managed to break synaptic on this session. :-othe irony.

---

### Post by dln9 on 2010-02-25
I don't understand your latest response.  

The question is, How can one know the packages installed during the original installation of Ubuntu 9.10 using the image iso file on the CD?  I thought we were saying to look in the directories of the CD to try to find which packages were installed.  Thus, I'm confused that you were thinking to look in Synaptic.  I must be misunderstanding your thinking.  Can you clarify for me your line of thought?  

Anyway, I did look in the directoried on the CD.  It appears that packages are scattered throughout a handful of directories.  So, I don't feel confident that approach will work.

---

### Post by mrhippieguy on 2010-02-27
i mean, synaptic shows every single package installed. i was messing around with it on the live cd to see if it could tell me in a logfile what was installed, but it only told me through itself, and it told me too many.

check your /var/cache/apt/archives, put it in list view, sort by date modified, and anything modified before you installed the OS is probably part of the live cd installation.

---


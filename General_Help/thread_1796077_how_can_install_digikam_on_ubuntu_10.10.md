---
title: "how can install digikam on ubuntu 10.10"
date: 2011-07-03
forum: General Help
---

### Post by Gianmaria on 2011-07-03
hi

i'm happy ubuntu 10.10 users
with macubuntu installed

but again i'm almost a novice 
i would like to install digikam

i read it's the best photo organizer 

under ubuntu software download i type digikam but did not found

in this page there are 6 download
[http://packages.ubuntu.com/search?keywords=digikam&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=digikam&searchon=names&suite=all&section=all)

but i don't know the differents between them

i got 32bit system with 4gb **should i enable the swap** file to run digikam **faser?**

please help me 
cheers

---

### Post by SeijiSensei on 2011-07-03
If this is your first time installing a new package in Ubuntu, I suggest you browse this document first:  [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

The simplest answer to your question is to open the "Terminal" application and type "sudo apt-get install digikam" at the dollar-sign prompt.  You can also use a graphical "package manager" like the Ubuntu Software Center.  The document I linked to will give you more details.

I doubt activating swap will make much of a difference in the performance of digikam, or most other programs, on a machine with 4GB.  I'm running Kubuntu 64-bit on a 4GB machine, and my swap is currently all unused.

---

### Post by Bucky Ball on 2011-07-03
By the looks of your other thread it seems you've solved this problem. If so, could you mark this thread as 'solved' from 'Thread Tools', please. ;)

---

### Post by Gianmaria on 2011-07-04
> **Bucky Ball said:**
> By the looks of your other thread it seems you've solved this problem. If so, could you mark this thread as 'solved' from 'Thread Tools', please. ;)
i almost solved my problem
digikam starts , but all menu are gray
i mean i can 't use it
all the menu , in the edit mode , i can do nothing
:(:(

thanks to all

---

### Post by Gianmaria on 2011-07-04
> **SeijiSensei said:**
> If this is your first time installing a new package in Ubuntu, I suggest you browse this document first:  [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

The simplest answer to your question is to open the "Terminal" application and type "sudo apt-get install digikam" at the dollar-sign prompt.  You can also use a graphical "package manager" like the Ubuntu Software Center.  The document I linked to will give you more details.

I doubt activating swap will make much of a difference in the performance of digikam, or most other programs, on a machine with 4GB.  I'm running Kubuntu 64-bit on a 4GB machine, and my swap is currently all unused.

thanks
but does digikam work under ubuntu ?
i mean all the menu are gray
i can browse my photos
i can tag my photos
but all the menu are gray , and in the edit mode i can do nothing
again everything is gray
:(

---

### Post by SeijiSensei on 2011-07-04
sudo apt-get install kipi-plugins

See if that helps.

If you want a full-featured editor for your photos, I'd recommend installing the [GIMP]("http://www.gimp.org/") (sudo apt-get install gimp).

---

### Post by Bucky Ball on 2011-07-04
Just a wild punt here: are you using KDE? If you are using regular Ubuntu this may not work, you need the KDE dependencies. Install kubuntu-desktop from Synaptics Package Manager and that probably fix.

[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"), think OP is after something to view lots of photos easily en masse as well as edit. Gimp not so good at former but great at latter. ;)

---

### Post by SeijiSensei on 2011-07-04
> **Bucky Ball said:**
> Just a wild punt here: are you using KDE? If you are using regular Ubuntu this may not work, you need the KDE dependencies. Install kubuntu-desktop from Synaptics Package Manager and that probably fix.

Even if you're running GNOME, installing a KDE package will pull in the required libraries without the entire desktop.  The same holds true for running GNOME applications on KDE.  Try installing synaptic on a KDE desktop; you'll see a lot of GTK+ libraries installed as dependencies.

---

### Post by Bucky Ball on 2011-07-04
Tnx for the info.

---

### Post by Gianmaria on 2011-07-04
> **SeijiSensei said:**
> sudo apt-get install kipi-plugins

See if that helps.

If you want a full-featured editor for your photos, I'd recommend installing the [GIMP]("http://www.gimp.org/") (sudo apt-get install gimp).

thanks 
i know the gimp
but digikam is really what i need

sudo apt-get install kipi-plugins
told me every component are update
maybe a clean up , i mean a 100% digikam uninstall


> **Bucky Ball said:**
> Just a wild punt here: are you using KDE? If you are using regular Ubuntu this may not work, you need the KDE dependencies. Install kubuntu-desktop from Synaptics Package Manager and that probably fix.

[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195"), think OP is after something to view lots of photos easily en masse as well as edit. Gimp not so good at former but great at latter. ;)

i use ubuntu 10.10 with macubuntu skin them

---


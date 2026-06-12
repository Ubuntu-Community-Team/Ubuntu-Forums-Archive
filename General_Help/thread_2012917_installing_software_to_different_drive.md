---
title: "installing software to different drive"
date: 2012-06-30
forum: General Help
---

### Post by trentonmichael on 2012-06-30
maybe im not googling the right terms here, but im sure someone else has had this issue. Ubunut is installed to my SSD, and im wanting to install programs (games, etc) to my mechanical HDD. Ubuntu recognizes it, and ive determined the correct partition is /dev/sdb5 but i cant seem to find any information on how to actually specify this directory as an install path.

---

### Post by dcstar on 2012-06-30
> **trentonmichael said:**
> maybe im not googling the right terms here, but im sure someone else has had this issue. Ubunut is installed to my SSD, and im wanting to install programs (games, etc) to my mechanical HDD. Ubuntu recognizes it, and ive determined the correct partition is /dev/sdb5 but i cant seem to find any information on how to actually specify this directory as an install path.

You have no control of where Linux programs are installed. Linux is not Windows.

---

### Post by ubnewbie2 on 2012-06-30
> **trentonmichael said:**
> maybe im not googling the right terms here, but im sure someone else has had this issue. Ubunut is installed to my SSD, and im wanting to install programs (games, etc) to my mechanical HDD. Ubuntu recognizes it, and ive determined the correct partition is /dev/sdb5 but i cant seem to find any information on how to actually specify this directory as an install path.

Have a look at [http://refspecs.linuxfoundation.org/FHS_2.3/fhs-2.3.html](http://refspecs.linuxfoundation.org/FHS_2.3/fhs-2.3.html) to see where different things are put. Bit heavy going though. It's not all in one place, and the install package specifies where it will go, not you.

However, I suppose most of the stuff from an install package for a new program will go in /usr, so read that bit.  If you are really determined, you might set up a copy of /usr in a partition on the mechanical drive and mount that to the /usr directory of your Ubuntu install.  (Not sure what experts might think of doing that.)  

The other thing that is worth doing is mounting a large partition on another drive in place of /home, as /home is where most user data goes and it tends to grow large.

---

### Post by mcduck on 2012-06-30
The correct way is instead of trying to specify the directory where something is installed (which you usually can't do), you specify the drive where the standard directory should be located.

So, for example, instead of trying to make the package manager put some files of a certain package to some other location than /usr, you'd just create the /usr directory on the desired hard drive.

(also keep in mind that packages are not installed into a single location, like in Windows, but instead all the files go to different directories based on each individual file's purpose.)

---

### Post by oldfred on 2012-06-30
If you are going to install programs to the rotating hard drive, why have an SSD?

Unless you are installing some very large games, you can install a lot of applications in Linux in a small / (root) partition. I normally use 25GB for / and put all my data on the rotating drive, but every file need to boot and run system including /home is in a 25GB / partition on my SSD. My / uses about 7GB of the 25GB I allocate.

---

### Post by ethana2 on 2012-08-24
I intend to build a gaming rig at some point with a GeForce GTX 660Ti and an OC'ed 3rd gen i5 under water cooling and whatnot-- I expect to have a small (under 100GB) Vertex 4 and a 7200rpm 2TB HDD. I want to have games that weigh in the gigabytes and already own many, from Humble Bundles mainly, that are in the hundreds of megabytes. I want to use the SSD for the operating system, non-game installed software, and files in my home that aren't in ~/Music, and I intend to be triple booting, on BOTH the SSD and the mechanical hard drive, Windows 7 64, Mac OS 10.8, and the latest Ubuntu.

I was hoping to do most of my gaming under Ubuntu, but if Windows 7 is the only one that's going to let me select where I install my games, looks like I'll have to reevaluate that.

---


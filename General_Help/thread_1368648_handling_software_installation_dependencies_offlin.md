---
title: "handling software installation dependencies offline"
date: 2009-12-30
forum: General Help
---

### Post by MichaelBurns on 2009-12-30
I am so confused by the "instructions" that I've found on "help sites".  In a nutshell, I want to put *.deb files on my usb drive, and then somehow install packages and all of their dependencies from these *.deb files, *WITHOUT ANY INTERNET ACCESS WHATSOEVER* from a default installation of ubuntu (jaunty).  All of the instructions that I can find require internet access at some point in the procedure.

Yes, obviously I *DO* have internet access, or else I wouldn't be having this discussion on an internet forum.  I just would rather rely on my flash drive than my "borrowed" internet access, which can be quite unreliable and slow at times.  Also, since I'm running from a live cd, every time I shut down I lose *ALL* of my installed packages.

For a specific example, we can discuss how I would install the ubuntu-restricted-extras package (for proprietary multimedia content).  I already have the 60 *.deb files on the flash drive.  What do I do now?  I have tried adding downloaded packages in synaptic, but that apparently doesn't work (for instance, it only installs 16 packages this way).  I have tried using dpkg, but the dependencies are too much of a hassle (it tells me what they are, but then I have to hunt them down manually, sometimes for several layers, and I would have to do this every time I boot).

Is there some what to pass the flash drive directory to apt-get install?

---

### Post by USB_NL on 2009-12-30
> **MichaelBurns said:**
> I am so confused by the "instructions" that I've found on "help sites".  In a nutshell, I want to put *.deb files on my usb drive, and then somehow install packages and all of their dependencies from these *.deb files, *WITHOUT ANY INTERNET ACCESS WHATSOEVER* from a default installation of ubuntu (jaunty).  All of the instructions that I can find require internet access at some point in the procedure.

Yes, obviously I *DO* have internet access, or else I wouldn't be having this discussion on an internet forum.  I just would rather rely on my flash drive than my "borrowed" internet access, which can be quite unreliable and slow at times.  Also, since I'm running from a live cd, every time I shut down I lose *ALL* of my installed packages.

For a specific example, we can discuss how I would install the ubuntu-restricted-extras package (for proprietary multimedia content).  I already have the 60 *.deb files on the flash drive.  What do I do now?  I have tried adding downloaded packages in synaptic, but that apparently doesn't work (for instance, it only installs 16 packages this way).  I have tried using dpkg, but the dependencies are too much of a hassle (it tells me what they are, but then I have to hunt them down manually, sometimes for several layers, and I would have to do this every time I boot).

Is there some what to pass the flash drive directory to apt-get install?
Try opening the packages from the correct path in the terminal (maby you need a .deb-installer)

---

### Post by MichaelBurns on 2009-12-30
> **USB_NL said:**
> Try opening the packages from the correct path in the terminal Do you mean to cd to the directory on my flash drive that contains the *.deb files?  OK, I haven't tried that.

> **USB_NL said:**
> (maby you need a .deb-installer)What's it called?  Of course, for my purpose, it would need to be either already on the live cd or downloadable as an executable.

---

### Post by alexfish on 2009-12-31
> **MichaelBurns said:**
> I am so confused by the "instructions" that I've found on "help sites".  In a nutshell, I want to put *.deb files on my usb drive, and then somehow install packages and all of their dependencies from these *.deb files, *WITHOUT ANY INTERNET ACCESS WHATSOEVER* from a default installation of ubuntu (jaunty).  All of the instructions that I can find require internet access at some point in the procedure.

Yes, obviously I *DO* have internet access, or else I wouldn't be having this discussion on an internet forum.  I just would rather rely on my flash drive than my "borrowed" internet access, which can be quite unreliable and slow at times.  Also, since I'm running from a live cd, every time I shut down I lose *ALL* of my installed packages.

For a specific example, we can discuss how I would install the ubuntu-restricted-extras package (for proprietary multimedia content).  I already have the 60 *.deb files on the flash drive.  What do I do now?  I have tried adding downloaded packages in synaptic, but that apparently doesn't work (for instance, it only installs 16 packages this way).  I have tried using dpkg, but the dependencies are too much of a hassle (it tells me what they are, but then I have to hunt them down manually, sometimes for several layers, and I would have to do this every time I boot).

Is there some what to pass the flash drive directory to apt-get install?

Hi

as mentioned change the dir path to your usb stick

Then Try This code

Code:

sudo dpkg -i *.deb

had to think about this , it may help

[How to get USB as apt-get source]("http://ubuntuforums.org/showthread.php?t=281108")

---

### Post by 3rdalbum on 2009-12-31
> **alexfish said:**
> hi

as mentioned change the dir path to your usb stick

then try this code

code:

Sudo dpkg -i *.deb

+1

---

### Post by GeorgeVita on 2009-12-31
Hi to all above!

Read next links for another simpler (GUI) solution:
[http://ubuntuforums.org/showpost.php?p=8559050&postcount=132](http://ubuntuforums.org/showpost.php?p=8559050&postcount=132)
[http://ubuntuforums.org/showpost.php?p=8577295&postcount=163](http://ubuntuforums.org/showpost.php?p=8577295&postcount=163)

Assuming that your system is updated (or you can accept package versions your system already knows) you can use Synaptic!

**System > Administration > Synaptic Package Manager**

select any package you want (ex.supertux) as usual: type in at 'search' field the word supertux and press enter. **Find** it below at '**package**' column, click on box of column **S**, '**mark for installation**', '**Mark**'

>>> Instead of 'Apply' select **File > Generate Package Download Script**
give a **filename** pointing to a USB memory stick. Close Synaptic, Quit (cancels all marks). The **created script** includes dependencies: ```
#!/bin/sh
wget -c http://ubuntu.otenet.gr/pool/universe/libp/libphysfs/libphysfs-1.0-0_1.0.0-5_i386.deb
wget -c http://ubuntu.otenet.gr/pool/main/s/sdl-image1.2/libsdl-image1.2_1.2.6-3_i386.deb
wget -c http://ubuntu.otenet.gr/pool/universe/s/supertux/supertux-data_0.3.1d-0ubuntu2_all.deb
wget -c http://ubuntu.otenet.gr/pool/universe/s/supertux/supertux_0.3.1d-0ubuntu2_i386.deb
``` Use any pc running **linux** (**any distro**, I used puppy) that has **wget** installed. **Connect** to internet and **run script** from USB memory stick. All requested files (including dependencies) will be **downloaded** to the same directory (into USB). 

Return to the 'offline' PC, attach USB stick OR USE A DIRECTORY THAT HAS ALL .deb FILES (possibly just extracted from .iso) and use:

**System > Administration > Synaptic Package Manager**
**File > Add Downloaded Packages** > point to the .deb **directory > Open**
follow instructions, wait for **installation**, **close** Synaptic, [B]done!
[/B]

Regards,
George

---

### Post by mutex023 on 2009-12-31
There's a software called APTonCD, which creates a repository out of the downloaded packages(in /var/cache/apt) and puts them onto a CD.
You could use this CD to install the packages on another machine offline, using Synaptic.

---

### Post by MichaelBurns on 2009-12-31
This almost works:
```

sudo dpkg -i /media/disk/ubuntu-restricted-extras_jaunty_i386/*

```
or, alternatively:
```

cd /media/disk/ubuntu-restricted-extras_jaunty_i386
sudo dpkg -i *

```
To be safe, I suppose I should replace * with *.deb?  Anyway, all of the files in that directory are *.deb files.

I still can't view flash content, and for some video clips the movie player complains about a missing plug-in (e.g. Windows Media Speech decoder and Windows Media Audio 9 decoder).  I get a message that says something like "the flash player couldn't be installed" and a few other seemingly error messages that didn't make any sense to me at all.  I think that I remember reading that dpkg doesn't handle dependencies.

George,
I followed that Synaptic procedure exactly; it was the first method that I tried that didn't work.  More specifically, when I tried the very last step, to "Add downloaded packages", and I navigated to where they are on my flash drive, they were all greyed out, and "open" did nothing.  Next, I tried "open" on the directory that contains the packages, and that "worked", but it only installed 16 out of 60, and the videos would not play.

mutex,
Does APTonCD also work with other kinds of storage, like flash drives?

---

### Post by mutex023 on 2010-01-01
OK I tried AptonCD.
It allows you to create an iso image, which you can theoretically
copy onto a flash drive and mount it on another system. (right click iso image select 'open with archive mounter'in karmic)
But the problem i ran into was installing from this mounted image directly in synaptic.
The Add CDROM option in synaptic checks the physical cd drive, there is no option to point it to the mounted iso.
So if anyone knows how to do this, please advise.

---

### Post by MichaelBurns on 2010-01-03
If I understand correctly, *.iso is a "package-like" file-type, similar in concept to *.tar, except with redundancy.  So, maybe there is some way to convert from *.iso to *.tar.

I am taking a break from exprimenting for a while.

---

### Post by mutex023 on 2010-01-03
An iso image is a standard file type for a cd/dvd image.
It is normally burned to cd's or used to copy the contents of a cd/dvd as is to the hard disk in the form of a .iso file.
However it can also be opened with the archive manager just like a tar file. 
But this won't help you much, since what you need is to add the 'iso image' as a repository in synaptic just like how you add a CD as a repository using the 'Add CDROM' option.

---

### Post by USB_NL on 2010-01-04
i have tried some ubuntu installs on a usb from my winxp (must still try them with wine) and put some debian installer files (.deb files) on it from my backupfolder for ubuntu in winxp
you can then find them back in ubuntu in filesystem /cdrom and just richt click and choose the gdeb (or something) installer

---

### Post by MichaelBurns on 2010-01-04
I finally figured out how to create a proper offline repository (on my usb stick), and then use apt-get to install packages from it.  I'm still ironing out the details to write a minimally interactive script that is "somewhat portable" (although my bash skills are sloppy at best).  The procedure is slightly complicated, and still a bit mysterious to me; when I get it cleaned up into the script, I'll post it.  (Actually, I will have two scripts:  one to handle setting up the repository with the computer online, and the other to handle package installation with the computer offline.)

Anyway, I'm not sure that this more complicated installation procedure using apt-get does anything that the dpkg command doesn't do already.  I still have some missing plugins for the proprietary multimedia stuff even when using apt-get, so perhaps this is an issue with the ubuntu-restricted-extras dependencies themselves.  I noticed that there were many "recommended" packages that don't install (by default) with it.  So, probably the ultimate (i.e. most straightforward and simplest) procedure will be to 1) use apt-get to download the packages (with recommendations) onto the usb stick, and then to 2) install the packages offline using the brute-force dpkg command.

Thanks to all of you for your helpful suggestions.  I'm almost there.

---

### Post by MichaelBurns on 2010-01-08
Here I describe how to do everything from the command line.  The key features are:
- the exclusive use of "apt-get" for package handling,
- the one-time need for an internet connection,
- and the set-up of, and installation from, offline repositories.
I know that I promised a script, but I thought that a description would be better.



************************************************************************
PHASE I:  DOWNLOADING PACKAGES WITHOUT INSTALLING
************************************************************************

The first item of business is to declare the online repositories whence the packages will be initially retrieved while the computer has a reliable internet connection.
Before you do that, backup the original "sources.list" file:

```

ubuntu@ubuntu:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

```

Since I want all packages to be available, this first requires an edit to the "sources.list" file:

```

ubuntu@ubuntu:~$ sudo gedit /etc/apt/sources.list

```

such that it includes (in my case) the uncommented lines:

```

deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb http://archive.ubuntu.com/ubuntu jaunty main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu jaunty main restricted multiverse universe
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted multiverse universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted multiverse universe
deb http://archive.ubuntu.com/ubuntu jaunty-updates main restricted multiverse universe
deb-src http://archive.ubuntu.com/ubuntu jaunty-updates main restricted multiverse universe

```

I believe that the second line is the only important line for my purpose.
Apparently, the key feature is that the word "jaunty" (or the appropriate name of your ubuntu release) is followed by the space-separated four words:

```

main restricted multiverse universe

```

(I believe that, by default, it is only followed by the words "main" and "restricted".)

************************************************************************

Alternatively, this can be done (more safely) by using the software sources tool:

```

System > Administration > Software Sources
   >> Check all of the component boxes.
   >> Close the dialog box.
   >> Reload the repository list.

```

which apparently just edits the "sources.list" file as shown above.
But, one of my goals was strict command-line usage, so I only used this method in order to determine what changes to make to the "sources.list" file.

************************************************************************

In order to download package files without installing them, pass the "d" option to the "apt-get" command:

```

ubuntu@ubuntu:~$ sudo apt-get -d install [short_package_name]

```

where [short_package_name] should, of course, be replaced with the corresponding short name of the package as in a normal online install.
E.g., in order to get the package files for LaTeX:

```

ubuntu@ubuntu:~$ sudo apt-get -d install latex

```

The package files have extension "*.deb", and they are saved to the folder:

```

/var/cache/apt/archives

```

There may (quite likely) be more than one such file that is downloaded to this folder, even if only one short package name is specified (this is part of the dependency issue).
Apparently, all of the "*.deb" files are needed.
Since I am running the live cd, this folder, along with the entire rest of the file system, is volatile (it apparently exists in RAM only).
So I moved my downloaded "*.deb" files onto a usb stick.

Suppose the mount point for the usb stick is

```

/media/disk

```

Then, I have a folder on the usb stick called "debs", and I have a separate [nickname] subfolder for each group of related packages, where [nickname] is an arbitrary folder name that I choose for the package.
E.g., for LaTeX I have a directory:

```

/media/disk/debs/latex

```

So, I moved the downloaded packages to the usb stick:

```

ubuntu@ubuntu:~$ sudo mv /var/cache/apt/archives/*.deb /media/disk/debs/[nickname]

```

E.g., immediately after downloading the LaTeX package files:

```

ubuntu@ubuntu:~$ sudo mv /var/cache/apt/archives/*.deb /media/disk/debs/latex

```



************************************************************************
PHASE II:  LISTING THE PACKAGES FOR DEPENDENCY HANDLING
************************************************************************

In order to handle dependencies, "apt-get" needs a file called "Packages.gz" with certain stuff in it.
This file can be created using the "dpkg-scanpackages" and "gzip" commands.
Unfortunately for some reason, the default live cd installation neglects "dpkg-scanpackages".
So, I installed it as part of the build-essential package:

```

ubuntu@ubuntu:~$ sudo apt-get install build-essential

```

(Apparently "build-essential" could be replaced by "dpkg-dev" with the same result, since they are apparently interdependent.)

Note:  I used the online repositories in order to acquire this package and its handful of dependencies.
I don't think that it is even available on my live cd.

************************************************************************

Then, I created the "Packages.gz" files with the mysterious encantations:

```

cd /media/disk/debs
sudo dpkg-scanpackages [nickname] /dev/null | gzip -9c > [nickname]/Packages.gz

```

where the second line is repeated for each package subfolder, with its appropriate nickname.

Note:  [nickname] occurs in _*two*_ places!

If you opt for a different directory structure, then you must make the appropriate changes in these command lines.



************************************************************************
PHASE III:  OFFLINE INSTALLATION
************************************************************************

Finally, the one-time use of the internet is complete (until you decide that you want another package in your usb stick repository).
The following procedures can be done without an internet connection.
They require that the preceding procedures have been done successfully, and also a "hand-made" "sources.list" file as described below.
The following assumes a fresh boot from a live cd.

************************************************************************

First, I create a backup of the "sources.list" file (which, by default, lists the temporarily undesired online repositories) for later reversion, if desired:

```

ubuntu@ubuntu:~$ sudo mv /etc/apt/sources.list /etc/apt/sources.list.backup

```

Then, I replace it with my custom offline "sources.list" file:

```

ubuntu@ubuntu:~$ sudo cp /media/disk/debs/sources.list /etc/apt/.

```

which I created "by hand" and store on my usb stick.
It contains a line for each of the package group subfolders of the form:

```

deb file:///media/disk/debian_packages [nickname]/

```

e.g.:

```

deb file:///media/disk/debian_packages latex/

```

Next, apt must be made aware of the new "sources.list" file:

```

ubuntu@ubuntu:~$ sudo apt-get update

```

Finally, the offline packages can be installed with the following command, repeated for each package:

```

ubuntu@ubuntu:~$ sudo apt-get install [short_package_name]

```

e.g.:

```

ubuntu@ubuntu:~$ sudo apt-get install latex

```

Note:  I believe that the short package name, rather than the nickname, must be used for this final step.
That is, use the name that you would use for an online installation.
I believe that the "Packages.gz" file is responsible for this.



************************************************************************
PHASE IV:  REVERSION TO ONLINE REPOSITORIES
************************************************************************

If desired, the the online repositories can be made available again after the offline installation.
This just amounts to renaming "sources.list.backup" to "sources.list" again:

```

ubuntu@ubuntu:~$ sudo rm /etc/apt/sources.list
ubuntu@ubuntu:~$ sudo mv /etc/apt/sources.list.backup /etc/apt/sources.list

```

Note:  This will make your offline repositories unavailable.
There is probably a more elegant solution, such as using the "cat" (or even more elegant "sed") command, but I haven't tried.
Anyway, the concept of moving files around is simple enough that even I (think that I) understand it.

---

### Post by mutex023 on 2010-01-08
Great work man !
I might try to write a nice GUI which does the above things
if i get time.

---

### Post by MichaelBurns on 2010-01-09
> **mutex023 said:**
> I might try to write a nice GUI which does the above things ...Wouldn't that be redundant, though?  I mean, isn't Synaptic *supposed to* already do this (for instance, as GeorgeVita suggests several posts ago)?  I'll be interested to see what you come up with.

---

### Post by alexfish on 2010-01-09
Hi

would " zeroinstall-injector " work in a similar instance

[http://0install.net/doc.html](http://0install.net/doc.html)

---

### Post by MichaelBurns on 2010-01-09
> **alexfish said:**
> Hi

would " zeroinstall-injector " work in a similar instance

[http://0install.net/doc.html](http://0install.net/doc.html)I suppose, but the "0launch" command does not install from my live cd.  My goal was to get the simplest bootstrapping method possible.

Here is an example script (as promised) that works on my computer running off of the jaunty live cd without a hard drive.  The script comes in two parts:  1) the part that relies on the internet connection, 2) the part that can be run successfully offline (after part 1 has been run successfully).
```

#!/bin/bash

# Enable all four components of the online repositories, as well as both free and nonfree components of the medibuntu repository.
# Save the necessary deb files for the specified package to the specified local directory.
# Set up a local repository for that package to be installed offline.
# Install the package offline.

# You may get an error along the lines:
#   failed to preserve file ownership/permissions
# This is apparently not a problem, and is only due to the lack of file permissions on a FAT FS.

PKG_NAM="texlive-latex-base"   # name of your desired package to download
PKG_NIC="latex_test"   # your personal nickname for the desired package
DST_NAM="jaunty"   # short name of your distribution, e.g. "jaunty", "karmic", "lucid", etc.
DEB_DIR="/media/disk/debs"   # your main directory for offline repos

OFL_SRC_LST="offline_sources.list"   # repo list file for personal offline repo
MED_SRC_LST="medibuntu.list"   # repo list file for medibuntu online repo
BKP_SRC_LST="/etc/apt/sources.list.backup"   # backup file for "sources.list"

# The following relies on an internet connection.

echo "getting $PKG_NAM from online repo ..."
echo "moving extant repo list to \"${BKP_SRC_LST}1\" ..."
sudo mv /etc/apt/sources.list ${BKP_SRC_LST}1
echo "creating \"sources.list\" to include all four repo components ..."
sudo echo "deb http://archive.ubuntu.com/ubuntu $DST_NAM main restricted universe multiverse" > sources.list
sudo echo "deb-src http://archive.ubuntu.com/ubuntu $DST_NAM main restricted universe multiverse" >> sources.list
sudo mv sources.list /etc/apt/.
echo "creating \"medibuntu\" repo list ..."
sudo echo "deb http://packages.medibuntu.org/ $DST_NAM free non-free" > $MED_SRC_LST
sudo mv $MED_SRC_LST /etc/apt/sources.list.d/.
echo "updating \"apt\" package database (may take a while) ..."
sudo apt-get update
echo "downloading $PKG_NAM package to $DEB_DIR/$PKG_NIC ..."
sudo apt-get -dy --allow-unauthenticated install $PKG_NAM
mkdir $DEB_DIR/$PKG_NIC
sudo mv /var/cache/apt/archives/*.deb $DEB_DIR/$PKG_NIC/.

echo "setting up offline repo ..."
echo "installing build-essential ..."
sudo apt-get -y install build-essential
echo "creating \"Packages.gz\" file ..."
cd $DEB_DIR
sudo dpkg-scanpackages $PKG_NIC /dev/null | gzip -9c > $PKG_NIC/Packages.gz

# The remainder can be done offline.

#echo "setting up offline repo ..."
#echo "moving extant repo list to \"${BKP_SRC_LST}2\" ..."
#sudo mv /etc/apt/sources.list ${BKP_SRC_LST}2
#echo "creating offline repo list ..."
#sudo echo "deb file://$DEB_DIR $PKG_NIC/" >> $OFL_SRC_LST
#sudo mv $OFL_SRC_LST /etc/apt/sources.list.d/.
#echo "updating \"apt\" package database ..."
#sudo apt-get update

#echo "installing $PKG_NAM ..."
#sudo apt-get install $PKG_NAM

```

---

### Post by Bartender on 2010-01-09
> **MichaelBurns said:**
> ...isn't Synaptic *supposed to* already do this (for instance, as GeorgeVita suggests several posts ago)? 

George's links go back to this [thread]("http://ubuntuforums.org/showthread.php?t=1238954"), which started out as a discussion about wvdial, but veered off in several directions before we talked about the Synaptic Package Download Script (PDS).  There are several more posts (mostly by me) about PDS and I'm still learning.

Creating your own scripts, as Michael Burns has done above, is completely beyond me.  I've just been trying to figure out a way to "bring home the data" to our dial-up desktop.  

Seems to me the biggest difference between what the OP wants to do and what PDS does is that to make PDS work as painlessly as possible you need some sort of internet connection at the "target" PC, regardless of how slow it is, so that you can at least update the package lists.  But the OP did mention having some kind of internet connection, and maybe that would be good enough to reload the package lists?

Anyway, I wanted to toss in my 2 cents even though it's a bit off-subject from what the OP is trying to do.  I'll bet someone could figure out how to use PDS even on a completely offline PC.  

In a couple of my posts in the wvdial thread, I mentioned that PDS did not grab all the dependencies for hugin and hplip.  I tried again just now to create a PDS for hugin.  Opened Synaptic, searched for hugin, clicked it for installation, Synaptic asked if I wanted to get other packages and I clicked Yes.  Then marked all for installation, then Created the script.  There are a lot more packages in this second script than there were in the first one, so I'm hopeful that the script will download everything I need to install hugin this time.

---

### Post by MichaelBurns on 2010-01-10
One issue that you will never be able to avoid is that, one way or another, you must get ahold of the deb files.  Using the internet just seems to be the most straightforward (wildly used) way to do it.

The beauty of the script that I propose is that it effectively sets up a repo (all of the debs together with the "Package.gz" file) once and for all on a usb stick that is then available offline.  Also, it only uses standard commands in order to do this ("apt" and "dpkg"), so the understanding is more widely applicable.

Once you have the usb stick set up, you can pressumably plug it into any computer (that has a usb port), and all you need is the "apt" command (which is pressumably available on a most basic installation of ubuntu, e.g. my live cd).

If I were better at bashing and debian in general, I would come up with a more elegant script that would:  1) automatically detect the name of the distribution (e.g. "jaunty" for me), 2) automatically detect the best online repos (instead of the default "archives"), and 3) handle multiple packages in one invocation.  I think that I have an idea how to handle 3).  I have no idea how to handle 1) nor 2), but I suspect that 1) is trivial, and I vaguely remember reading about how to do 2).

---

### Post by Cheesemill on 2010-01-10
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by ptpare on 2010-01-15
I finally found out a almost complete GUI way to get Synaptic to recognise an iso on a usb that I had mounted to a particular folder. 

I needed internet access to make sure that two programs were on my system. These were APTonCD and Gmount-iso. 
I then had to create a folder to use as a mount point. I created isoimage in /media/. This had to be done from nautilus run from the command line with sudo. This was the only place that I had to use the command line.

Code:
sudo nautilus 

Then I had to use use Gmount-iso from the repositories to mount the iso onto isoimage. 
My iso name was aptoncd-20100104-CD1.iso This had been created using APTonCD (can be found at Sysem/Administration/APTonCD.)
I opened up Synaptic from the menus System/administration/Synaptic Package Manager and entered my system password.
I went to Settings/Repositories/Third-Party Software
The I had to press the "+ADD" button. 
A screen appeared "Enter the complete APT line of the repository that you want to add as source". I had to enter the following line.

deb file:///media/isoimage/ /

The important trick was the sequence of characters "/ /". This allowed me to leave the distribution and component blank. For a normal repository this the distribution would have been Hardy or Jaunty etc and the components would have been main free non free. 

If you now edit this entry while still in the "Software Sources" screen you should find that the url is "file:///media/isoimage/"
and the Distribution is "/" It is this backslash in the distribution that is so important.

UnCheck all of the component boxes. Close the box and close the next box which asks you to click on the "Reload" button for your changes to take effect. Then follow the usual instructions and all your programs in your iso should be visible. From now on I used Synaptic in the normal way.

---

### Post by GeorgeVita on 2010-01-15
> **ptpare said:**
> ...This had to be done from nautilus run from the command line with sudo. This was the only place that I had to use the command line.
Code:
sudo nautilus 

Hi **ptpare**, welcome to this forum!
Thanks for the helpful info, many people need 'offline' alternatives.
Just to make it 'all GUI': at Desktop you can press **ALT-F2**, type '**gksudo nautilus**' and click '**Run**'.

Regards,
George

---

### Post by penguinv on 2010-01-20
Hi,

I see you have your work cut out for you, reinstalling all your useful programs every time you boot up. I can assume that of the set of programs installed on the LiveCD that you use some of them and you never use others.

I am going to suggest something: I dont know how to do it and I dont know what it is called but I am sure that a knowledgeable geek can do it and once done, your system will be workable and "turnkey", ie you wont have to reinstall time after time.  

That's insufferable IMHO.

edit comment: I only looked at the first page of replies, more to go.

This can be made: a custom LiveCD with the programs you use installed on it, omitting others you don't use. I can onlyhope that you can get this whole "mess" on one CD so you dont have to resort installing every time you boot up. 

I wish you a more pleasant experience in the future.

---

### Post by MichaelBurns on 2010-01-21
Thanks for the suggestion, penguinv.  Actually, that had occured to me.  But, my reasoning for doing it the way that I (finally figured out how to) do is that the skills that I have learned are more widely applicable, and I don't plan to be running off of the live CD for very long (although I am still running the live CD after how many weeks now).

I must say, the live CD feature is one of, if not the best feature of ubuntu.  I tried the DSL live CD, but I couldn't figure out how to get the wireless internet to work.  With the ubuntu live CD, I just click the little applet icon on the task bar and pick the network.  Actually, the real annoyance to me is having to "fix" firefox every time.  But, default settings can't please everyone.

---

### Post by mutex023 on 2010-01-22
@ptpare, Thanks very much, always found APTonCD unworkable because of the iso image not getting added in synaptic.
Your tip should greatly help others too in a similiar situation.

---

### Post by sandy8925 on 2010-03-12
I have some huge doubts about the howto on page 2:

How do we use Packages.gz in the offline install? You don't even mention what to do with it.

You haven't mentioned how to create the custom entries in sources.list which you've apparently done(but didn't tell us to do earlier and just suddenly mention it in offline install).

Also in the last step you've written:
ubuntu@ubuntu:~$ sudo rm /etc/apt/sources.list /etc/apt/sources.list.backup
ubuntu@ubuntu:~$ sudo mv /etc/apt/sources.list.backup /etc/apt/sources.list

Basically you're removing the sources.list file and it's backup. And then trying to restore the file from the backup you just deleted. ???????
The first command should just be:
ubuntu@ubuntu:~$ sudo rm /etc/apt/sources.list

---

### Post by MichaelBurns on 2010-03-12
sandy, I am sorry that you are suffering so much from my post #14.

> **sandy8925 said:**
> How do we use Packages.gz in the offline install? You don't even mention what to do with it.You don't use it, but rather apt-get uses it (apparently).  The only thing "to do with it" is to create it (as per the instructions in PHASE II of post #14).  However, if you want to do something else with it besides just creating it, you can certainly look inside to see various information about versions and dependencies and such.  Don't let me stop you.

> **sandy8925 said:**
> You haven't mentioned how to create the custom entries in sources.list which you've apparently done(but didn't tell us to do earlier and just suddenly mention it in offline install).As I mentioned in PHASE III of post #14:> **MichaelBurns said:**
> I replace it with my custom offline "sources.list" file:

```

ubuntu@ubuntu:~$ sudo cp /media/disk/debs/sources.list /etc/apt/.

```

which I created "by hand" and store on my usb stick.
It contains a line for each of the package group subfolders of the form:

```

deb file:///media/disk/debian_packages [nickname]/

```

e.g.:

```

deb file:///media/disk/debian_packages latex/

```It's (apparently) just a text file.  I'm assuming that you know how to use a text editor (for example, I used gedit).  I appologize; I should have been more clear.  I just thought that anyone who wanted to go through that horrid procedure that I wrote would be familir with the basic idea of the "sources.list" file.

Please let me know what is specifically unclear so that I can try to clarify it.

> **sandy8925 said:**
> Also in the last step you've written:
ubuntu@ubuntu:~$ sudo rm /etc/apt/sources.list /etc/apt/sources.list.backup
ubuntu@ubuntu:~$ sudo mv /etc/apt/sources.list.backup /etc/apt/sources.list

Basically you're removing the sources.list file and it's backup. And then trying to restore the file from the backup you just deleted. ???????
The first command should just be:
ubuntu@ubuntu:~$ sudo rm /etc/apt/sources.listYou are correct; that was a typo.  I have editted post #14 to correct it.

I actually debated with myself whether to even give explicit commands to revert the "sources.list" file to its backup.  In fact, there is most likely a more elegant way to do it.  Anyway, let that be a lesson for all participants:  **Take advice at your own risk (peril).**  (That applies everywhere, not just ubuntuforums.)

BTW, I hope that I have not misled anyone into thinking that I have some clue what I'm doing.

---


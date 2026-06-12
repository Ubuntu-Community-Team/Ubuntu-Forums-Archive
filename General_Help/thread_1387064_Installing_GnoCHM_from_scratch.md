---
title: "Installing GnoCHM from scratch"
date: 2010-01-21
forum: General Help
---

### Post by captainjackrana on 2010-01-21
I am a new ubuntu user, with v9.04. I want to install GNOCHM to (application to view chm files) view .chm files on ubuntu. Now, as far as from what ive learnt, it isnt available as a complete package on the web and has to be compiled, etc.. I have no idea how its done.. 

So  iwould be really grateful if someone taught me how to start from scratch.. 
For a start, ive downloaded the gnochm-0.9.11.tar.gz from the sourceforge site.

---

### Post by mcduck on 2010-01-21
It's in the repositories, so you can just forget abut the web site and compiling, and use Synaptic/apt-get to install. :)

---

### Post by openxs on 2010-01-21
Hi, GNOchm is in the repositories (where Ubuntu software is stored online). From your desktop you click:
System >> Administration >> Synaptic 
that will open up your software manager. Search for GNOchm, tick the box next to it, then click 'Apply' and it will install it for you. This is the general way to install software on Ubuntu, diferent distro's all have different package managers. I hope this helps you out. 

Of course, if you really want to compile the package from the source code, right click the *.tar.gz file and 'Extract' it like you would a zip file in Windows, there should be a file called README.txt with instructions. Normally it will be a case of opening a 'Terminal': Applications >> Accessories >> Terminal then moving to the folder you extracted from the tar.gz before running the commands: sudo make (once that has finished type) sudo make install. Here is some information on installing things from source: [http://www.tuxfiles.org/linuxhelp/softinstall.html]("http://www.tuxfiles.org/linuxhelp/softinstall.html") If you do install stuff from source you have to make sure any dependencies are installed (other software & libraries that the program relies on to run). Using Synaptic is far easier to start off with.

---

### Post by captainjackrana on 2010-01-21
well, that confirms what i had done bfore.. The point is i couldnt find Gnochm in the Synaptic Manager.. Well, i am using the wubi version of ubuntu ( installed a 10GB size ubuntu inside a windows partition). Could this be the reason the package wasnt included beforehand?

---

### Post by mcduck on 2010-01-21
> **captainjackrana said:**
> well, that confirms what i had done bfore.. The point is i couldnt find Gnochm in the Synaptic Manager.. Well, i am using the wubi version of ubuntu ( installed a 10GB size ubuntu inside a windows partition). Could this be the reason the package wasnt included beforehand?

Make sure you have enabled the Universe repository (community-maintained software). You can do that in System/Administration/Software Sources (or in Synaptic).

---

### Post by kwacka on 2010-05-12
Unfortunately, attempting to enter gnochm using apt-get install gnochm results in:

The following packages have unmet dependencies:
  gnochm: Depends: python-gtkhtml2 but it is not installable

[This has been recorded as a bug]("https://bugs.launchpad.net/ubuntu/+source/gnochm/+bug/538773")

Meanwhile, one user (v1nsai) suggested using a [Debian package]("http://packages.debian.org/sid/python-gtkhtml2") for installation of python-gtkhtml2 - which worked for me.

However the developer of gnochm has not updated sourceforge link since 2008 and in response to a query from a launchpad reporter says that he will not be working on it in the forseeable future.

Alternatives (from repositories) - chmsee, kchmviewer (which requires some KDE libraries), & xchm. 

Alternatively, Archmage will convert these compressed files to HTML.

---

### Post by chika.tambun on 2010-07-29
if u still insist on gnochm then the summary is:

1. sudo apt-get install dctrl-tools
2. sudo grep-aptavail -F"Depends" -F"Recommends" -F"Suggests" -sPackage python-gtkhtml2
3. sudo dpkg -i python-gtkhtml2_2.25.3-3ubuntu1_i386.deb (thank you Savvas radevick for download link)
4. sudo apt-get install -f
5. sudo apt-get install gnochm

then gnochm works

thanks to the previous thread chmsee, n archmage

---


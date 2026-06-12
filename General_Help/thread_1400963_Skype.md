---
title: "Skype"
date: 2010-02-07
forum: General Help
---

### Post by oldtraveler on 2010-02-07
Is it possible to install Skype in Ubuntu 9.10?  I don't find it listed in Synaptic Package Manager.  I did install skysentials, skytools, and skytools-modules-8.3.  That does not apparently install the program itself.  At least I can't find it.

---

### Post by switch10 on 2010-02-07
go [HERE ]("http://www.skype.com/download/skype/linux/choose/") and download the .deb.  The 8.10 version works fine in 9.10, I have it installed in i686 as well as amd64.

---

### Post by Ginsu543 on 2010-02-07
The best way to get Skype before was through Medibuntu. Unfortunately, Medibuntu officially stopped offering Skype after Jaunty. However, I was still able to download their skype packages by going to [http://packages.medibuntu.org/karmic/skype.html](http://packages.medibuntu.org/karmic/skype.html) and [http://packages.medibuntu.org/karmic/skype-common.html](http://packages.medibuntu.org/karmic/skype-common.html) and downloading the skype and skype-common packages appropriate for my setup. While the pages to download the packages appear to have been removed, you might still be able to get them by clicking on the links to automatically install the packages. You should install the skype-common package first, before installing the skype package (skype-common is a required dependency package for skype). If that doesn't work, then the only way to get it would be from the official Skype website as switch10 recommended. I have also tried the official skype .deb package switch10 pointed you to, but I have found that the medibuntu packages work better.

---

### Post by bedlam on 2010-02-07
> **oldtraveler said:**
> Is it possible to install Skype in Ubuntu 9.10?  I don't find it listed in Synaptic Package Manager.  I did install skysentials, skytools, and skytools-modules-8.3.  That does not apparently install the program itself.  At least I can't find it.
You could give Linux Mint A try. Sound, Video, Skype and other good stuff. It all works out of the box and it's virtually the same as Ubuntu.

---

### Post by oldtraveler on 2010-02-07
Thanks for all the suggestions.

I did try the Medibuntu solution, but as you suspected the download file has been removed.

The deb solution did work.  Of course, my Microsoft Life-Cam  and microphone don't so unless I can find drivers for them all I can do is listen.

---

### Post by TheShader on 2010-02-07
> **bedlam said:**
> You could give Linux Mint A try. Sound, Video, Skype and other good stuff. It all works out of the box and it's virtually the same as Ubuntu.

+1. I am on Linux Mint 7(Ubuntu 9.04) and Skype worked out of the box for me. You can even send your desktop while using compiz and all those effects like 3d desktops and flame painting...

---

### Post by oldtraveler on 2010-02-10
Does anyone know where I can find drivers for my Microsoft LifeCam 1.4 that will work with Skype?

---

### Post by drpjkurian on 2010-02-10
> **oldtraveler said:**
> Does anyone know where I can find drivers for my Microsoft LifeCam 1.4 that will work with Skype?

Hi Do this:
Download driver:
[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)
grab the .bz2 file
extract and change directory
in terminal type "make" no quotes take about 5 mins
then type "sudo make install"
reboot

tested working on Intrepid With Cheese, Ekiga, Skype, GyachE, Xawtv


installed xawtv, luvcview, and removed camserv.

I GOT THIS FROM ANOTHER THREAD [http://ubuntuforums.org/showthread.php?t=952392](http://ubuntuforums.org/showthread.php?t=952392)
Thanks to jesterthejedi

---

### Post by oldtraveler on 2010-02-11
I grabbed the .bz2 file and extracted it.

Here is what I see in terminal:

phil@Asus-pc:~$ make
make: *** No targets specified and no makefile found.  Stop.
phil@Asus-pc:~$ sudo make install
[sudo] password for phil: 
make: *** No rule to make target `install'.  Stop.
phil@Asus-pc:~$

---


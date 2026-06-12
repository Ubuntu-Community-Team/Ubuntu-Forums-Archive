---
title: "In General, how to install program that are not listed in software centre?"
date: 2011-10-27
forum: General Help
---

### Post by hhtmp88 on 2011-10-27
Hi all!

In General, how to install program that are not listed in software centre?
-> e.g I have downloaded: firefox-7.0.1.tar.bz2, but how to install without the help of software centre?


Thanks for any kind of help!

---

### Post by haqking on 2011-10-27
> **hhtmp88 said:**
> Hi all!

In General, how to install program that are not listed in software centre?
-> e.g I have downloaded: firefox-7.0.1.tar.bz2, but how to install without the help of software centre?


Thanks for any kind of help!

First of all for firefox better to use a PPA, i dont use FF anymore but see here [https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)
First of all always search in the Software Centre or Synaptic to see if software is already in the repos for easy install or from the developers website where a .deb might be available again for easy install (like a .exe in windows)

If you have to download it as a package it will often come down in a package/archive format such as xxxxx.tar or xxxx.tar.gz etc.

These are analogous to windows .zip files but with varying compression denoted by the .xx after the .tar such as .tar.gz where .gz is the compression. A .tar file means Tape Archive which is legacy from UNIX when things were backed up to tape drives. The 2 or 3 letters after the .tar refer to the type of compression used to pack down the archive.

See here for dealing with these files [https://help.ubuntu.com/community/FileCompression](https://help.ubuntu.com/community/FileCompression)

It is often just a simple case of right clicking in your GUI on the file and choosing extract then it will be unpackaged to a directory.

The contents might simply be a .deb file as i said for easy installation see here:
[http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg21t2.htm)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

If the contents is source code then you need to compile this, this is where people often get stumped and is dependant on the developer and the documentation provided, once unpackaged there is often a README text file or a INSTALL file which you should read as it will often contain clear and concise instructions on what to do.

If not then you need to figure it out, see here for information on compiling from source:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

then you should be set ;-)

Have fun

Regards

haqking

---

### Post by Lars Noodén on 2011-10-27
If you can, stick with the package manager.  That means finding the .deb file and then using [dpkg](http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html) to install it.  That makes tracking versions, upgrading and removal nearly automatic.

---

### Post by oldtimer7777 on 2011-10-27
> **Lars Noodén said:**
> If you can, stick with the package manager.  That means finding the .deb file and then using [dpkg]("http://manpages.ubuntu.com/manpages/oneiric/en/man1/dpkg.1.html") to install it.  That makes tracking versions, upgrading and removal nearly automatic.

That isn't the way to install firefox either..  Use a PPA to install firefox from a list like this:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by dcstar on 2011-10-28
> **oldtimer7777 said:**
> That isn't the way to install firefox either..  Use a PPA to install firefox from a list like this:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

Why force someone to trawl through hundreds of lines for one specific thing?:

[https://launchpad.net/~mozillateam/+archive/firefox-stable](https://launchpad.net/~mozillateam/+archive/firefox-stable)

---

### Post by lovinglinux on 2011-10-28
See [Firefox 7 & Beyond Mega Thread](http://ubuntuforums.org/showthread.php?t=1712247).

---

### Post by s9032g@comcast.net on 2011-10-28
Look into gdebi package installer. It worked for me.

steveg

---

### Post by hhtmp88 on 2011-10-28
Thanks all!
-> will try it out!

---


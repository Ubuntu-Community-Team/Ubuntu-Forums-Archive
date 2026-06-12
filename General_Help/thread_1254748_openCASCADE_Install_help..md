---
title: "openCASCADE Install help."
date: 2009-08-31
forum: General Help
---

### Post by b.jonkers on 2009-08-31
hello.  I am fairly new to ubuntu.

I am having some trouble with installing this program.

I have downloaded it off of the openCASCADE site and extracted it to the desktop.  The folder is called openCASCADE6.3.0

i have read the documentation but i still cant work it out.

I am pretty sure it has something to do with the Makefile.am and the Makefile.in  files ros/adm/make folder.

Any help will be great.

---

### Post by scouser73 on 2009-08-31
Hi b.jonkers, you can learn how to install files with the instructions on this tutorial: [[COLOR="Red"]**Compiling: Easy How To**[/COLOR]]("https://help.ubuntu.com/community/CompilingEasyHowTo")

---

### Post by b.jonkers on 2009-09-01
> **scouser73 said:**
> Hi b.jonkers, you can learn how to install files with the instructions on this tutorial: [[COLOR="Red"]**Compiling: Easy How To**[/COLOR]]("https://help.ubuntu.com/community/CompilingEasyHowTo")

thanks.

I read that last night but i was sleepy.  When i went looking the config file wasn't in the folder the documentation said.  

I got it sorted now its compiled and just finishing the install up.

---

### Post by b.jonkers on 2009-09-01
i ran into an error.

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package


and from the log file this is what i get.

dpkg-deb: parse error, in file `/var/tmp/tmp.EtTGbIgpTg/package/DEBIAN/control' near line 11 package `ros':
 empty value for version
/var/tmp/tmp.EtTGbIgpTg/dpkgbuild.log (END)

any ideas.

---


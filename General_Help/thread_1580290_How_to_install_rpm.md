---
title: "How to install rpm?"
date: 2010-09-23
forum: General Help
---

### Post by lhjoanna on 2010-09-23
I downloaded rpm-4.0.4.tar.gz just now.
Then i run  the instructions  as the readme shows.But when i get to these sentences in Readme(list below),I cannot understand what it means.

> 
These are the things you'll have to do to install this package.
  
  * cd <your-build-directory>
  * tar -xzvf rpm-2.2.9-src.tar.gz
  * cd rpm-2.2.9
  * configure --prefix=/gg
  * make
  * make install
 
****************************From Here*******************************************************
Now it's time to edit the file "gg:lib/rpmrc" to correspond to your
system setup. Change the following entry:
  * topdir: /place/to/store/RPM/packages
Make sure <tmppath> points to a _harddisk_ directory (the ram disk doesn't
allow the use of softlinks):
  * tmppath: /place/on/your/hard/disk
Add the following entry:
  * builddir: /place/where/RPM/will/build/packages

It is recommended to let <topdir> and <builddir> point to two different
partitions.
  
Now create the following directories in <topdir>:
  * RPMS
  * RPMS/m68k
  * SOURCES
  * SRPMS
  * SPECS
  
Create the "rpm" directory in "gg:lib".
  makedir gg:lib/rpm

Now it's time to initialise the rpm database with:
  rpm --initdb




Someone know  what  this means? 
Thanks a lot!!!

---

### Post by klemes on 2010-09-23
To install rpm packages you need 'alien'.You can install it by typing 'sudo aptitude install alien'.:guitar::popcorn:

---

### Post by coffeecat on 2010-09-23
> **lhjoanna said:**
> I downloaded rpm-4.0.4.tar.gz just now.

That would be the source code for the app 'rpm'. If you want to install rpm, simply go to Synaptic and install it from there - it's in the Ubuntu repository. Or, as klemes says, you need alien of you want to install rpm packages.

But why do you want to mess with rpm at all? That's not a package format native to the Debian based Ubuntu.

---

### Post by searchfgold6789 on 2010-09-23
> Now it's time to edit the file "gg:lib/rpmrc" to correspond to your
system setup.  That means there is a file called rpmrc in the folder gg:lib. Search for this file and open it with your favorite text editor.
> 
Change the following entry:
  * topdir: /place/to/store/RPM/packages There will be an entry in the file that looks like this. Change it to where you want the RPM packages to be stored. It can be an empty folder in your home directory.
> 
Make sure <tmppath> points to a _harddisk_ directory (the ram disk doesn't
allow the use of softlinks):
  * tmppath: /place/on/your/hard/disk In the same file, there will be an entry that looks like this. The readme is telling you to make sure that /place/on/your/harddisk points to a directory you know is probably on your harddisk. Change it to the place where your TMP folder is.

> Add the following entry:
  * builddir: /place/where/RPM/will/build/packages Add to the file. At the bottom type builddir: and change the directory it points to to where RPM should be making the RPM's. I think this can also be a blank folder in your home directory.

> It is recommended to let <topdir> and <builddir> point to two different
partitions. If you have two seperate partitions, you may want to make the two above places be on one of these each.
  > 
Now create the following directories in <topdir>:
  * RPMS
  * RPMS/m68k
  * SOURCES
  * SRPMS
  * SPECS Use you file explorer to make folder with those names in the directory you specified before in the beginning.
  > 
Create the "rpm" directory in "gg:lib".
  makedir gg:lib/rpm

Now it's time to initialise the rpm database with:
  rpm --initdbType those in the terminal.
Excuse my bad ubuntuese. I hope this helps.

---

### Post by PriceChild on 2010-09-23
I'd strongly advise you to first look in the Ubuntu repositories whenever you would like new software.

Although going onto the internet and downloading random software is the norm in the Windows world, it isn't here.

All the software in the Ubuntu repository (10s of thousands of apps) is built and tested for the version of Ubuntu that you are using. It is also secured & authenticated to make sure that you are not downloading dodgy, nasty code from an evil person.

Check out [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) for an introduction on how to install software.

I assume you're wanting the 'rpm' package installed so that you can install another .rpm file. STOP! :-) Try and find the 'another .rpm' file in the ubuntu repository, or find a .deb package for it from their website. If not, then sure, get the source of that package. Using alien on the .rpm package should be a last resort.

What is your real 'end result'?

---

### Post by Mark Phelps on 2010-09-23
Having used alien with rpm packages, I can attest that it only works SOME of the time.  It's not a miracle cure, and in my experience, leads to more problems than it solves.

Support the others in saying you should look into Ubuntu-compatible alternatives before resorting to using rpm packages.

---


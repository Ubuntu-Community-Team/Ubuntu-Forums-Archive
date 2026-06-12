---
title: "Java"
date: 2010-11-03
forum: General Help
---

### Post by munaf on 2010-11-03
Hi, I have the following error in 10.04. I've tried several times to uninstall, resolve, install these dependencies and am at my wits end now.
This morning I gave up on OpenJDK and installed Sun JDK, hence the sun versions below. But this error is stopping me from installing anything else.




Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  default-jre-headless: Depends: openjdk-6-jre-headless (>= 6b14) but it is not going to be installed
  icedtea-6-jre-cacao: Depends: openjdk-6-jre-headless (= 6b18-1.8.2-4ubuntu2) but it is not going to be installed
  latexdraw: Depends: libjiu-java but it is not going to be installed
             Depends: libjlibeps-java but it is not going to be installed
  openjdk-6-jre: Depends: openjdk-6-jre-headless (>= 6b18-1.8.2-4ubuntu2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

me@andromeda:~/private$ java -version
java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) Server VM (build 17.1-b03, mixed mode)

me@andromeda:~/private$ javac -version
javac 1.6.0_22

---

### Post by lykeion on 2010-11-03
Have you tried what it suggests:
```
sudo apt-get -f install
```

Also try run Synaptic as it can handle dependency errors.

As to give you any further help, it would be easier if you'd say what you are trying to do here.

---

### Post by munaf on 2010-11-03
Hi, thanks for replying.

I've tried that, also many times, and this is what I get:


sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev libxpp3-java linux-headers-2.6.32-21 x11proto-kb-dev libxdmcp-dev xtrans-dev x11proto-core-dev
  linux-headers-2.6.32-21-generic python-eggtrayicon libxt-dev x11proto-input-dev libpthread-stubs0-dev libxau-dev libpthread-stubs0
  libx11-dev libxcb1-dev libxstream-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  openjdk-6-jre-headless openjdk-6-jre-lib
Suggested packages:
  sun-java6-fonts ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho ttf-telugu-fonts ttf-oriya-fonts
  ttf-kannada-fonts ttf-bengali-fonts
The following NEW packages will be installed:
  openjdk-6-jre-headless openjdk-6-jre-lib
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
Need to get 0B/33.1MB of archives.
After this operation, 88.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 245032 files and directories currently installed.)
Unpacking openjdk-6-jre-lib (from .../openjdk-6-jre-lib_6b18-1.8.2-4ubuntu2_all.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openjdk-6-jre-lib_6b18-1.8.2-4ubuntu2_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/jvm/java-6-openjdk/jre/lib/ext/localedata.jar')
No apport report written because the error message indicates a dpkg I/O error
                                                                             Unpacking openjdk-6-jre-headless (from .../openjdk-6-jre-headless_6b18-1.8.2-4ubuntu2_i386.deb) ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/openjdk-6-jre-headless_6b18-1.8.2-4ubuntu2_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar')
No apport report written because the error message indicates a dpkg I/O error
                                                                             Errors were encountered while processing:
 /var/cache/apt/archives/openjdk-6-jre-lib_6b18-1.8.2-4ubuntu2_all.deb
 /var/cache/apt/archives/openjdk-6-jre-headless_6b18-1.8.2-4ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


And that's where it just falls over.

I'm trying to clean up the dependency problem (without uninstalling Java, which as I said above is sun-java-6) so that I can install other apps too. at the moment it's blocking installation of other apps through apt-get.

---

### Post by lykeion on 2010-11-03
I can't say what's causing your problem. Maybe a more dpkg-savvy user might step in. However I found posters with similar problems as yours, and maybe some solutions.

In [this thread]("http://ubuntuforums.org/showthread.php?t=1598999") solutions suggested are:
[LIST=1]
[*]sudo apt-get clean
[*]delete the failing deb packages from /var/cache/apt/archives/ see [this post]("http://ubuntuforums.org/showpost.php?p=9986439&postcount=4")
[*]using pkill, like described [here]("http://ubuntuforums.org/showpost.php?p=9999947&postcount=9")
[/LIST]

I'd start with 1, then 3, and finally 2

---

### Post by munaf on 2010-11-03
hi, 

I did 1, 3 and then "sudo apt-get -f install", and Voila!

Thanks a dozen.

---

### Post by lykeion on 2010-11-03
Great that it worked out for you. :P
To help others find solutions you might want to tag this thread as SOLVED: [http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---


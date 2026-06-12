---
title: "dependency on libcupsys2"
date: 2010-03-11
forum: General Help
---

### Post by barna on 2010-03-11
Hi,
I tried to install the printer drivers for the Canon PIXMA iP3600 printer, downloaded from here: [http://software.canon-europe.com/software/0031336.asp](http://software.canon-europe.com/software/0031336.asp)
There is a dependency problem of these packages, they depend on libcupsys2. This package has been renamed libcups2 (Canon seems to be slow in updating their packages). Although I have libcups2 installed on my notebook, and libcups2 provides the virtual package libcupsys2 (to satisfy such old dependencies), the canon printer drivers cnijfilter-common_3.00-1_i386.deb and cnijfilter-ip3600series_3.00-1_i386.deb still report a dependency error, and refuse to install. Could somebody explain me, why, and how to overcome this problem? 
I could install them using dpkg -i --ignore-depends=libcupsys2, and they work nicely, but my system has now broken packages, and synaptic refuses to 'Mark All Upgrades', saying that I have broken packages, and I should fix them first.
Thanks

---

### Post by barna on 2010-03-11
Here is a step-by-step solution how to install the drivers for the Canon PIXMA iP3600 printer on Ubuntu 9.10 (should work for all printers as well with their respective drivers, and for later ubuntu releases as well)
The .deb packages from canon need to be modified to replace the dependency on libcupsys2 by libcups2

1) download Canon's driver in .deb format from here:
[http://software.canon-europe.com/software/0031336.asp](http://software.canon-europe.com/software/0031336.asp) and save it to your disk. The file will be ip3600_debian_printer.tar

2) Change to this directory, and untar the archive: 
tar xvf ip3600_debian_printer.tar
It produces the following files:
cnijfilter-ip3600series_3.00-1_i386.deb
cnijfilter-common-3.00-1.tar.gz
cnijfilter-common_3.00-1_i386.deb

3) It is the two .deb files, which need modifications before installation. For both of them do the following (where X.deb stands
for the given .deb file, replace X by the filename)

ar x X.deb   
# this produces debian-binary, data.tar.gz and control.tar.gz 
# in the current working directory)

mkdir tmp; cd tmp
# create and change to the tmp directory

tar xvzf ../control.tar.gz
# this extracts the following files into tmp/: md5sums, control
# (and postinst and postrm in case of cnijfilter-ip3600series_3.00-1_i386.deb)

sed -i 's/libcupsys2/libcups2/g' control
# this replaces libcupsys2 by libcups2 in the file 'control'

rm -f ../control.tar.gz  
# remove the old archive

tar cvzf ../control.tar.gz *
# this re-creates the control.tar.gz archive with all the files

cd ..; rm -rf tmp
# change one directory up, remove tmp/ directory

ar r X.deb control.tar.gz 
# this replaces the control.tar.gz member in the X.deb debian
# package file (which is a standard Unix 'ar' archive)

rm -f control.tar.gz debian-binary data.tar.gz 
# this cleans up temporary files

4) Ready. Install these two packages:
sudo dpkg -i *.deb

Good luck!

---

### Post by Maxtor09 on 2010-06-17
Hello,

 here is a driver  installation for the Canon iP3600 (Lucid Lynx) without changing the  control  file

 - download : [http://security.ubuntu.com/ubuntu/pool/ …  .6_all.deb]("http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.6_all.deb")
 - install the  deb  file, click on it
 - download : [http://software.canon-europe.com/software/0031336.asp](http://software.canon-europe.com/software/0031336.asp)
 - extract the  tar  file
 - install the 2  deb  files (first the "common" then the "ip3600")
 - connect the printer

 base installation is done now

---

### Post by barna on 2010-06-25
I have now a new notebook, where I installed a 64 bit Ubuntu 10.04. The bad news is that the official Canon driver includes only .deb files for 32 bit systems. The semi-good news is that the printer driver collection in Ubuntu 10.04 contains this printer (Canon PIXMA iP3600 - CUPS+Gutenprint v5.2.5), but it simply does not work. I have set up the printer, selected every possible paper source, tried to print a test page - it was reported as successful, but nothing came out...
Any idea, what to check?

```

/var/log/cups/error_log:
 E [25/Jun/2010:14:47:27 +0200] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [25/Jun/2010:14:47:48 +0200] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [25/Jun/2010:14:48:03 +0200] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [25/Jun/2010:15:08:44 +0200] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [25/Jun/2010:15:10:19 +0200] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory

```

---

### Post by barna on 2010-06-25
Ok, one needs to force the architecture to install the i386 .deb packages, and it works:
sudo dpkg -i --force-architecture *.deb

as suggested here: 
[http://ubuntuforums.org/showthread.php?t=948312](http://ubuntuforums.org/showthread.php?t=948312)

---

### Post by ontwowheels on 2011-05-24
> **barna said:**
> Here is a step-by-step solution how to install the drivers for the Canon PIXMA iP3600 printer on Ubuntu 9.10 (should work for all printers as well with their respective drivers, and for later ubuntu releases as well)
The .deb packages from canon need to be modified to replace the dependency on libcupsys2 by libcups2

1) download Canon's driver in .deb format from here:
[http://software.canon-europe.com/software/0031336.asp](http://software.canon-europe.com/software/0031336.asp) and save it to your disk. The file will be ip3600_debian_printer.tar

2) Change to this directory, and untar the archive: 
tar xvf ip3600_debian_printer.tar
It produces the following files:
cnijfilter-ip3600series_3.00-1_i386.deb
cnijfilter-common-3.00-1.tar.gz
cnijfilter-common_3.00-1_i386.deb

3) It is the two .deb files, which need modifications before installation. For both of them do the following (where X.deb stands
for the given .deb file, replace X by the filename)

ar x X.deb   
# this produces debian-binary, data.tar.gz and control.tar.gz 
# in the current working directory)

mkdir tmp; cd tmp
# create and change to the tmp directory

tar xvzf ../control.tar.gz
# this extracts the following files into tmp/: md5sums, control
# (and postinst and postrm in case of cnijfilter-ip3600series_3.00-1_i386.deb)

sed -i 's/libcupsys2/libcups2/g' control
# this replaces libcupsys2 by libcups2 in the file 'control'

rm -f ../control.tar.gz  
# remove the old archive

tar cvzf ../control.tar.gz *
# this re-creates the control.tar.gz archive with all the files

cd ..; rm -rf tmp
# change one directory up, remove tmp/ directory

ar r X.deb control.tar.gz 
# this replaces the control.tar.gz member in the X.deb debian
# package file (which is a standard Unix 'ar' archive)

rm -f control.tar.gz debian-binary data.tar.gz 
# this cleans up temporary files

4) Ready. Install these two packages:
sudo dpkg -i *.deb

Good luck!

This worked for me, MP560 11.04 64 bit.  Only thing is I had to remove the entire Depend line from all .deb files referenced here
[http://ubuntuforums.org/showpost.php?p=10829925&postcount=80](http://ubuntuforums.org/showpost.php?p=10829925&postcount=80)

If I didn't remove the entire Depend I had an error running the install.sh  Both scanning and printing over wireless work!!

---

### Post by demonipuch on 2011-05-26
Hello

I've shared on the french community forum a little script that fix the dependency issue. 
What it does? It modifies the control file in th package to add a dependency with libcups2 which replaces libcupsys2 since 9.10 and rebuilds the package.

You can download the script here : [http://demonipuch.free.fr/download/rebuild_canon.sh](http://demonipuch.free.fr/download/rebuild_canon.sh)

And here is the code :

```
#!/bin/bash
# Fix libcupsys2 dependancy issue with Canon printers and force installation for amd64 computers (ia32-libs required)
#
# ./rebuildeb_canon.sh /path/to/file/cnijfilter-xxxxx_xxxxx_i386.deb

PACKAGE=$1
NAME=`basename $PACKAGE`
TMP_DIR=`echo $PACKAGE | cut -d"_" -f1 | cut -d"-" -f2`
ARCHITECTURE=`uname -m`

read -p "Rebuild this package? $NAME [y/n] " ANSWER
while [[ $ANSWER != "y" ]] && [[ $ANSWER != "n" ]] ; do
    read -p "Rebuild this package? $NAME [y/n] " ANSWER
done 
    if [[ $ANSWER == "n" ]] ; then
        exit 0
    else 
        dpkg-deb -x $PACKAGE $TMP_DIR
        dpkg-deb --control $PACKAGE
        sed -i 's/libcupsys2 (>= 1.2.1)/libcupsys2 (>= 1.2.1) | libcups2/' DEBIAN/control
        mv DEBIAN/ $TMP_DIR
        sudo chown -R root:root $TMP_DIR
        rm $PACKAGE
        dpkg -b $TMP_DIR $PACKAGE
        sudo rm -rf $TMP_DIR
        echo "New package built..."
    fi
read -p "Install new package? [y/n] " ANSWER
while [[ $ANSWER != "y" ]] && [[ $ANSWER != "n" ]] ; do
    read -p "Install new package? [y/n] " ANSWER
done
    if [[ $ANSWER == "n" ]] && [[ $ARCHITECTURE != "x86_64" ]] ; then
        echo -e "To install the package later, run this command :\nsudo dpkg -i $PACKAGE"
        exit 0
    elif [[ $ANSWER == "n" ]] && [[ $ARCHITECTURE == "x86_64" ]] ; then
        echo -e "To install the package later, run this command :\nsudo dpkg -i --force-architecture $PACKAGE"
        exit 0
    elif [[ $ANSWER == "y" ]] && [[ $ARCHITECTURE == "x86_64" ]] ; then
        sudo dpkg -i --force-architecture $PACKAGE
    else
        sudo dpkg -i $PACKAGE
    fi
exit 0

```

---

### Post by johanbove on 2011-06-26
I tried your script Demonipuch on LinuxMint 11 (Ubuntu "Natty" 11.04) with the following result:

```
./rebuild_canon.sh cnijfilter-common_3.00-1_i386.deb 
Rebuild this package? cnijfilter-common_3.00-1_i386.deb [y/n] y
dpkg-deb: building package `cnijfilter-common:i386' in `cnijfilter-common_3.00-1_i386.deb'.
New package built...
Install new package? [y/n] y
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 208039 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.00-1 (using cnijfilter-common_3.00-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2 | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common:i386
```

When i try to update libc6, libcupsys2 and libpopt0 I get the feedback that they are all installed and are the latests versions.

Some system info:

```

uname -a
Linux GiR 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

Funny thing is that the printer is recognized perfectly in the gnome-printer-settings and the "printer debug" wizard couldn't help me as well, with all CUPS tests working fine, yet the printer refuses to react to commands. It does "live" on the USB port, it just doesn't print anything.

---

### Post by yagolf on 2011-07-15
Hi barna,

I tried your step-by-step method (great work, btw, really clear explanation of what's going on) for my canon pixma ip4500 but I didn't get it to work. Here's the last command and its outcome:
> margs@main:~/Desktop/canon$ sudo dpkg -i *.deb
(Reading database ... 170446 files and directories currently installed.)
Preparing to replace cnijfilter-common 2.80-1 (using cnijfilter-common_2.80-1_i386.deb) ...
Unpacking replacement cnijfilter-common ...
Preparing to replace cnijfilter-ip4500series 2.80-1 (using cnijfilter-ip4500series_2.80-1_i386.deb) ...
Unpacking replacement cnijfilter-ip4500series ...
dpkg: dependency problems prevent configuration of cnijfilter-common:
 cnijfilter-common depends on libcupsys2 (>= 1.2.1); however:
  Package libcupsys2 is not installed.
dpkg: error processing cnijfilter-common (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cnijfilter-ip4500series:
 cnijfilter-ip4500series depends on cnijfilter-common (>= 2.80); however:
  Package cnijfilter-common is not configured yet.
dpkg: error processing cnijfilter-ip4500series (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-common
 cnijfilter-ip4500series
margs@main:~/Desktop/canon$
As you can see, I didn't get the libcupsys2 to be substituted by libcups2. I tried it twice paying special attention to each step of the process (all steps went through with no issue whatsoever) and it still didn't do it. Any clues as to why?

I'm using 11.04-32b, if you need more info about my machine, just ask.
And thanks again for the tutorial!

---

### Post by rudiger_wolf on 2011-10-01
[http://ubuntuforums.org/showpost.php?p=10864432&postcount=7](http://ubuntuforums.org/showpost.php?p=10864432&postcount=7)

Worked for me on Ubuntu 11.10 beta 2 32 bit.

---

### Post by demonipuch on 2011-10-01
> **rudiger_wolf said:**
> [http://ubuntuforums.org/showpost.php?p=10864432&postcount=7](http://ubuntuforums.org/showpost.php?p=10864432&postcount=7)

Worked for me on Ubuntu 11.10 beta 2 32 bit.
Thanks for the feedback.
By the way, the script may be downloaded here now : [http://demonipuch.free.fr/rebuildeb_canon.sh](http://demonipuch.free.fr/rebuildeb_canon.sh)

---

### Post by fleming164 on 2011-10-10
Hey I'm quite new to Ubuntu (but loving it) and would like some guidance as to what to do with the script or code, thanks :)

---

### Post by Bob Fletcher on 2012-01-02
Hi,
I am one of these users that visit Ubuntu every couple of years hoping that the current installation  with work with all my hardware, I usually give up.

I am running Ubuntu 11.10

I have a Canon Pixma iP3600 and I followed the step by step instructions. All went well without any errors.

Then went to install the printer. Very fast it found the driver. Status showed printer “Idle”  if I switch it off then the status is “Stopped - Unplugged or turned off” so it sees the printer. But try to print and nothing happens. Try to clean still nothing. The printer queue just flashes the print job too fast for sending to the printer.

I have not tried that script yet need to give it a break for a while. But any ideas of what is happening.

Robert...

---

### Post by barna on 2012-01-03
Hi,
I do not know the answer, but I remember that a long time ago I had a very long struggle, not being able to print. The reason turned out to be that the paper source (tray vs. manual feed) was not correctly set up. Unfortunately I don't remember how I solved it...
There might be a setting for this in the system printer configuration, or try [http://127.0.0.1:631](http://127.0.0.1:631) for cups' native configuration interface (you will need to setup an administrator user - I think it is the 'root' by default, but unfortunately you don't know the root password on ubuntu. You can do the following:
```

sudo sh  (and give your password)
passwd   (and give now the new root password)

```
These are just guesses...

---

### Post by alfefried on 2012-02-01
> 
No more fooling around with making any files.

This site shows you how to do the ppa route and install what you need no matter x86 or x64.

[http://www.ubuntubuzz.com/2011/06/do...er-driver.html]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html")


This may work for you ... hope this helps

---

### Post by demonipuch on 2012-02-01
This ppa is a great help. The only problem is that duplex printing won't work. I had to use the ppd file provided by Canon drivers.

---

### Post by Bryan55 on 2012-02-04
> **alfefried said:**
> This may work for you ... hope this helps

This work so will. It even gives all the resolutions the printer is capable of. 

Thanks for finding this. A big wet kiss from me.

Bryan

PS  Perhaps not a big wet kiss but thanks anyway

---

### Post by sudden8 on 2012-10-21
For my Canon iP3500 printer, I was not able to use the Canon driver on Debian 6.0.6, neither the "deb" or the "rpm" driver, although after running "alien" to create "deb" files from the "rpm" files, I was able to install these files without complaint.  However, the printer remained silent.  I finally removed these drivers and selected the PIXMA MP520-CUPS+Gutenprint v 5.2.6 driver that is provided in Debian 6.0.6 and the printer came to life!

---


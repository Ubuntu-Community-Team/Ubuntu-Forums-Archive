---
title: "ATI drivers - fglrx?"
date: 2010-12-13
forum: General Help
---

### Post by liddell on 2010-12-13
Hi helpful people! I recently installed Maverick on a K52Dr notebook and I'm having some complications in getting the ATI drivers working. So here is where I am at:
I downloaded the latest Linux driver from the [official website]("http://support.amd.com/us/kbarticles/Pages/ATI-Catalyst-driver-Radeon-HD5400.aspx") and after some minor hiccups I started following the instructions given in the Ubuntu-specific readme that came in the file:

> 0.  On your build system, make sure you have the prerequisites
    installed:

    $ sudo apt-get build-dep fglrx-installer

1.  Download the archive file and unpack it to get the .run file

2.  Do a --buildpkg Ubuntu/source, which will build a diff.gz,
    orig.tar.gz and an unsigned dsc.  For example:

    $ bash ./ati-driver-installer-*.run --buildpkg Ubuntu/source

    This might prompt for your password for sudo privs.  It may
    install things to your system it needs for constructing the
    source packages, such as cdbs, libstdc++, etc.  (As of 8.600
    it seems to no longer do this for source pkgs.)

3.  dpkg-source -x that dsc to unpack it into a directory, then
    cd into the resultant directory.

4.  dch -e to update the new changelog entry.
    Make sure to mark out any bugs that get closed with it.

    Also doublecheck that it includes debian/ changes up to the current
    Ubuntu version; if not, some merging may be required.

5.  debuild -S to produce a new .dsc

6.  Verify the new .dsc produces valid .debs by running it through
    pbuilder, sbuild, etc. as usual.

7.  Install and test the .debs, and then dput the .changes file

It's at step 4 that I run into this:

> nate@nate-laptop:~/Desktop/fglrx-8.69$ dch -e fglrx-installer_8.690-0ubuntu1_source.changes 
dch: fatal error at line 478:
Cannot find debian/changelog anywhere!
Are you in the source code tree?
(You could use --create if you wish to create this file.)


I'm stumped! Can anybody shine a light on how to go forward on this?
Thanks!
/L

---

### Post by Niva on 2010-12-13
I'm a bit lost as to why you're going about this the hard way.  Is there a reason why you don't use the fglrx drivers Ubuntu provides.

---

### Post by liddell on 2010-12-13
The one in the repository does not work for me. I can get high resolutions, full colour, and 2D working fine, but nothing 3D.

---


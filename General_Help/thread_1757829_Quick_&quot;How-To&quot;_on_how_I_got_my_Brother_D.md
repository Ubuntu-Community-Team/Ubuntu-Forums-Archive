---
title: "Quick &quot;How-To&quot; on how I got my Brother DCP-7040 printer and scanner working"
date: 2011-05-13
forum: General Help
---

### Post by HookedOnLinux on 2011-05-13
I'm running 64 bit and not sure if this is required for 32 bit.

For anyone struggling to get their Brother printer and/or scanner working in Natty 11.04. These are the steps I've found through here and pieced them together. I have a DCP-7040 printer/scanner but, I think this will work with all models.

First go to Brothers site and download latest drivers...[http://www.brother-usa.com/downloads](http://www.brother-usa.com/downloads) and follow install directions and pre-required procedures.

Then do this for all downloaded .deb files

cd to directory where files are located.

1. sudo dpkg -x [package].deb common
2. sudo dpkg --control [package].deb
3. sudo gedit DEBIAN/control
4. remove the "Dependency: libc... line and save.
5. sudo cp -a DEBIAN/ common/
6. sudo dpkg -b common [package].deb
7. sudo dpkg --force-all -i [package].deb
8. sudo rm -rf common DEBIAN

Do this after installing printer/scanner driver:

1. sudo gedit /lib/udev/rules.d/40-libsane.rules
2. add the 2 lines below, save and reboot.

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

This worked for me and hope it does for you!! Enjoy!

---

### Post by Jim_in_Omaha on 2011-08-10
This worked for me too. Had some problems and reinstalled 11.04. Using the DCP-7020 did not work anymore.

I had to also install the 'brdcp7040lpr-2.0.2-1.i386.deb' using the same technique.

Delete what ever DCP-7040 ubuntu tried to put in the printer setup, then reinstall it. 

required files from Brother for this:
cupswrapperDCP7040-2.0.2-1.i386.deb
brdcp7040lpr-2.0.2-1.i386.deb

I also uninstalled the synaptic brother related items before doing this.

---


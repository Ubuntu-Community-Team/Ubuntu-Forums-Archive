---
title: "Issues switching from Nvidia to ATI"
date: 2010-12-30
forum: General Help
---

### Post by cooljimy84 on 2010-12-30
After removing the Nvidia bits and bobs i then booted up fine (using the built in drivers for my ATI 5970 HD)

However i wanted openCL, so i followed some guides.. (as none of them seemed to helped) i'm now rather stuck, fglrx won't install/uninstall i issue "sudo apt-get install -f"
and get the output below...
> james@merc-srv:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 111MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 277889 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
Now i've removed and installed the ATI catalist a few times and am now stuck with this.. after this i've got another fun one, as when i do get ATI installed i can't startx using fglrx....

I'm running ubuntu 64bit 10.04 LTS server ed

---

### Post by cooljimy84 on 2010-12-30
SOLVED.....

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1579437](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1579437)

just incase

> t seems that the uninstall process is attempting to remove a package  diversion, but isn't finding the diversion it's expecting to remove.  To  fix it, I changed the diversion to what it was "expecting" to remove.   I'm sure there's a way to do this using dpkg-divert, but I decided to  manually tweak the diversion myself.  In order to do this you need to  edit the file "/var/lib/dpkg/diversions".  Back up the file, and then  open it in a text editor.

     Code:
     # first, make a backup
sudo cp /var/lib/dpkg/diversions /var/lib/dpkg/diversions.bak
# open and edit
sudo gedit /var/lib/dpkg/diversions 
Somewhere in the file you should find three consecutive lines that look like this:

     Code:
     /usr/lib/libGL.so.1.2
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
xorg-driver-fglrx 
Change the last line from "xorg-driver-fglrx" to "fglrx".  The three lines should now look like this:

     Code:
     /usr/lib/libGL.so.1.2
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
fglrx 
Save the file, now apt-get should be able to remove fglrx.  It worked for me.

---


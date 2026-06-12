---
title: "Alien-generated .deb file not there"
date: 2011-03-09
forum: General Help
---

### Post by llanitedave on 2011-03-09
I'm trying to install an epson scanner driver that's available as an .rpm.

This is what I get for output:

llanitedave@llanitedave-desktop:~/Downloads$ sudo alien -k iscan-2.10.0-1.c2.i386.rpm
[sudo] password for llanitedave: 
Warning: Skipping conversion of scripts in package iscan: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
iscan_2.10.0-1.c2_i386.deb generated

So the last line says the .deb file is generated, but it's not in any directory.  I used -v to show all the commands, and there was nothing in there that gave me a new directory location.

So, where do Alienized files go?

---

### Post by dtrosset on 2011-03-17
Same result here. The output says [FONT=Courier New][COLOR=RoyalBlue]generated xxx.deb[/COLOR][/FONT]. But a [FONT=Courier New][COLOR=SeaGreen]find /[/COLOR][/FONT] does not find it!

Where is this generated .deb package?

---

### Post by dtrosset on 2011-03-17
I got a hint on this page [http://askubuntu.com/questions/24437/alien-deletes-the-deb-generated-before-i-can-install-it](http://askubuntu.com/questions/24437/alien-deletes-the-deb-generated-before-i-can-install-it)

I was trying to alien an rpm made for i386 architecture on an amd64 (x86_64) system.

The solution, is to alien the file on an i386 (32 bits) system.

Note that the final .deb cannot be installed on the amd64 system, although installing it on the i386 system and copying the files to the amd64 system is OK.

---


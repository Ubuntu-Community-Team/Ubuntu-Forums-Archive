---
title: "Tcl library not found!"
date: 2010-03-02
forum: General Help
---

### Post by Elya on 2010-03-02
Dear All, 

Could you please help me with my trouble? 
I try to install simulation package Espresso. 
When I configure I have following error message. 

checking for libtcl8.5... no
checking for libtcl8.4... no
checking for libtcl8.3... no
checking for libtcl8.2... no
checking for libtcl... no
configure: error: Tcl library not found!

I do have Tcl installed. 

sudo apt-get install tcl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tcl is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenipmi0 python-pexpect diffstat x11proto-gl-dev libnet-snmp-perl libopenais2 corosync quilt snmp
  libdrm-dev openipmi openais libxxf86vm-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I tryed 

configure CPPFLAGS="-I /usr/share/tcltk" LDFLAGS="-L /usr/lib"

I have same error message.


Please, help!

---

### Post by giammy on 2010-03-02
Hi,

you probably haven't the development libraries:
try installing tcl-dev.

bye
giammy

---


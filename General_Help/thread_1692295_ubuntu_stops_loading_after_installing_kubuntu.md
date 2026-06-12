---
title: "ubuntu stops loading after installing kubuntu"
date: 2011-02-21
forum: General Help
---

### Post by skynoc on 2011-02-21
hello 

i couldnt run ubuntu after installing kubuntu desktop , it stops on the last step before opening the login screen i clicked ctrl+alt+F1 and login in terminal i typed xinit the result is as follow :

x.org x server 1.9.0
release date: 2010-08-20
x protocol version 11, Revision 0
build operating system: linux 2.6.24-28-server i686 ubuntu
current operating system: linux skynoc-laptop 2.6.35-25-generic #44-ubuntu smp fri jan 21 17:40:4 utc 2011 i686
kernel command line: boot_image=/boot/vmlinuz-2.6.35-25-generic root=uuid=91416621-f5d3-4c4c-9933-9387a548f29f ro quiet splash
build date: 09 january 2011 12:14:58pm
xorg-server 2:1.9.0-0ubuntu7.3 (for technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
current version of pixman: 0.18.4
before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line , (!!) notice, (II) not implemented, (??) unknown
(==) log file: "/var/log/xorg.0.log", time: mon feb 21 14:37:40 2011
(==) using system config directory "/usr/share/x11/xorg.conf.d"
parse error on line 1 of section inputclass in file /usr/share/x11/xorg.conf.d/50-synaptics.conf
"jm@" is not a valid keyword in this section.
(EE) problem parsing the config file
(EE) error parsing the config file
fatal server error :
no screens found 
please consult the The X.Org Foundation support at [http://wiki.x.org](http://wiki.x.org) for help
please also check the log file at "/var/log/xorg.0.log" for additional information.

ddxsigGiveUp: Closing log
giving up 
xinit: no such file or directory (error 2): unable to connect to x server
xinit: no such process (error 3): server error

any idea ?

---

### Post by skynoc on 2011-02-21
i searched google i found this command may help me sudo dpkg-reconfigure -phigh xserver-xorg but looks like i have a previous error that making the system unstable the error might be in perl package 
after executing the command the result is as follow :

unrecognized character \xAA in column 1 at /usr/share/perl/5.10/strict.pm line 1
compilation failed in require at /usr/sbin/dpkg-reconfigure line 8
begin failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 8

any idea ?

---


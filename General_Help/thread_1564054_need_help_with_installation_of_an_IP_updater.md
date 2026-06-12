---
title: "need help with installation of an IP updater"
date: 2010-08-30
forum: General Help
---

### Post by mobius55 on 2010-08-30
So i recently begun the process of turning an old PC into a personal web server. So far i have installed ubuntu, gotten apache on it, and registered a domain. Im having problems with the installation of the IP updater, ill refer you to the web page ([http://www.dnsexit.com/Direct.sv?cmd=userIpClients](http://www.dnsexit.com/Direct.sv?cmd=userIpClients)) How can I get that up and running on ubuntu and set it to start automatically when the comp turns on? im not too familiar with the command line of ubuntu so any detailed help is much appreciated. thanks!

---

### Post by lmarmisa on 2010-08-30
This page shows you the instructions to follow:

[http://www.dnsexit.com/Direct.sv?cmd=ipClients](http://www.dnsexit.com/Direct.sv?cmd=ipClients)

You have to download and install the Debian package ipUdtate-1.6-3.deb, configure it and reboot the system.

These comments of the page seem interesting too:

> 
[SIZE=-1]The Debian package that works on Debian Linux                    distribution. To install: 
                  >> dpkg -i ipUpdate-1.6-2.deb
                  >> /usr/sbin/dnsexit-setup.pl      #                   to setup (please choose daemon mode)
                  >> /etc/init.d/ipUpdate start      #                   to start the program 
                  Refer to "file /usr/share/ipUpdate-1.6/doc/README.txt"                   for instructions. [/SIZE]

Tips for the Linux script:                   
[LIST]
[*]To start the program automatically after reboot. You need to run command 
                      >> **chkconfig ipUpdate on** ( for linux distribution including Fedora/RHEL/CentOS) 
                        >>** insserv ipUpdate** ( for Suse linux)
[*]File "/tmp/dnsexit-ip.txt" will cache the ip address of                       the last successful IP update to our system. For next update,                       if the IP stays the same, the update request won't be sent                       to our server. You can simply change the IP at dnsexit-ip.txt                       file to force the update to DNSEXIT.
[*]File "/var/log/dnsexit.log" contains the update history                       for your IP.
[/LIST]
 You will need to open a terminal ( Applications -> Accesories -> Terminal ) for running the proposal commands.

---

### Post by mobius55 on 2010-09-01
Debian? does this work with ubuntu? should I not use the .rpm?

---


---
title: "post-installation script returned error exit status 1"
date: 2010-04-27
forum: General Help
---

### Post by Rastlosen on 2010-04-27
[COLOR=Red]I have been having the worst time trying to get sametime messenger from IBM to install properly. I had it working fine for the last 6 months and yesterday I accidently updated and it all went to {1134}. I seem to have found dkms to be the source of the problem. 

I get an exit 0 regardless of whether or not its install or uninstall. I have managed to get pidgin to work for now, but it is no means ideal for my purposes. [/COLOR]

[COLOR=Red]I kept getting this...[/COLOR]
rastlosen@rastlosen-laptop:~$ sudo apt-get install sametime-connect
[sudo] password for rastlosen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  sametime-connect
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
[COLOR=Red]
I figured I would try to fix the broken install that is shown by the "1 not fully installed or removed" and got this....[/COLOR]

rastlosen@rastlosen-laptop:~$ sudo apt-get --fix-broken install
[sudo] password for rastlosen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
[INFO - 27.Apr.10 05:17:28]: Heartbeat URL: [http://**********](http://**********)
Setting up openclient-savap-modules-dkms-source (0.18) ...
ln: creating symbolic link `/usr/src/openclient-savap-modules-dkms-0.18/openclient-savap-modules-dkms': File exists
dpkg: error processing openclient-savap-modules-dkms-source (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 openclient-savap-modules-dkms-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

[COLOR=Red]Not sure where to go from there I cleaned.
[COLOR=Black]
rastlosen@rastlosen-laptop:~$ sudo apt-get clean
[/COLOR]
I figured Id try instalation of sametime again and got a different result... kindof.[/COLOR]

rastlosen@rastlosen-laptop:~$ sudo apt-get install sametime-connect
[sudo] password for rastlosen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  sametime-connect
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
rastlosen@rastlosen-laptop:~$ sudo apt-get install sametime-blue
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  sametime-blue
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 72.0MB of archives.
After this operation, 136MB of additional disk space will be used.
Get:1 [http://watc4eb2.watson.ibm.com](http://watc4eb2.watson.ibm.com) safe/ibm-core sametime-blue 7.5.1.20070416-7 [72.0MB]
Fetched 72.0MB in 29s (2,436kB/s)                                              
[INFO - 27.Apr.10 05:48:13]: Heartbeat URL: [http://********](http://********)
Selecting previously deselected package sametime-blue.
(Reading database ... 392526 files and directories currently installed.)
Unpacking sametime-blue (from .../sametime-blue_7.5.1.20070416-7_i386.deb) ...
Processing triggers for desktop-file-utils ...
Setting up openclient-savap-modules-dkms-source (0.18) ...
ln: creating symbolic link `/usr/src/openclient-savap-modules-dkms-0.18/openclient-savap-modules-dkms': File exists
dpkg: error processing openclient-savap-modules-dkms-source (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up sametime-blue (7.5.1.20070416-7) ...
Errors were encountered while processing:
 openclient-savap-modules-dkms-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
[COLOR=Red]

Any help to get this resolved would be greatly appreciated.

Thanks![/COLOR]

---

### Post by Brandon Williams on 2010-04-27
Your attempt with --fix-broken indicates that /usr/src/openclient-savap-modules-dkms-0.18/openclient-savap-modules-dkms already exists when the post install script attempts to create a symbolic link. Is that file a regular file or a symbolic link? If it's a symbolic link, just delete it and --fix-broken again. That may be enough to clear up the problem.

---


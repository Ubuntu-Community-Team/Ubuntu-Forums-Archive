---
title: "install freenx on ubuntu 11.10"
date: 2011-09-08
forum: General Help
---

### Post by odror on 2011-09-08
I was not able to find the deb freenx package for 11.10

I was try to install the 10.10 package. I got the following error:

> # apt-get install freenx
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 freenx : Depends: esound-clients but it is not installable or
                   arts but it is not installable
E: Unable to correct problems, you have held broken packages.


any ideas how to fix it or where to find the 11.10 version.

Thanks

---

### Post by odror on 2011-09-26
Any news on that subject? I was able to compile it and have it work on 11.10, but it stopped working in the last 2 days. I do not know why. I get a cryptic connection. error.

---

### Post by kylewhittington on 2011-10-28
I'm having the same issue on newly upgraded 11.10. Following the guide on installation for 11.04 doesn't work now. When running the apt-get install freenx I'm getting the same error as odror re: esound or arts, as above.

Any help, much appreciated.

---

### Post by odror on 2011-10-28
> **kylewhittington said:**
> I'm having the same issue on newly upgraded 11.10. Following the guide on installation for 11.04 doesn't work now. When running the apt-get install freenx I'm getting the same error as odror re: esound or arts, as above.

Any help, much appreciated.
I had to install the tar files from NO Machines web. The problem is now solved until someone fix the deb files.

---

### Post by snaky on 2011-10-28
can you write a little guide how to install freenx? that you can also use a unity-desktop?
here is the only solution i found.
thanks

---

### Post by odror on 2011-10-29
> **snaky said:**
> can you write a little guide how to install freenx? that you can also use a unity-desktop?
here is the only solution i found.
thanks
Using the tar files is self explanatory. I was not able to use with freenx unity or gnome3. only kde is working for me.I have not used kde in years since version 3.x. Now kde is the most stable desktop in ubuntu. Even without freenx. On my server at home neither Unity nor gnome3 are stable. I had to switch to kde.

---

### Post by uniomni on 2011-11-01
The best instructions I have seen are
[http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html](http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html)

and I verified they work for 11.04
However, on 11.10 I get the same problem as everyone else.

Installing from NoMachine is not an option for us because they limit the number of simultaneous logins to 2

Can someone please fix the deb files or let us know how to work around the broken packages?

Thanks
Ole Nielsen

---

### Post by albatros78 on 2011-11-03
> **uniomni said:**
> The best instructions I have seen are
[http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html](http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html)

and I verified they work for 11.04
However, on 11.10 I get the same problem as everyone else.

Installing from NoMachine is not an option for us because they limit the number of simultaneous logins to 2

Can someone please fix the deb files or let us know how to work around the broken packages?

Thanks
Ole Nielsen

I solved!:P
 The procedure is very twisted to 11.10 of ubuntu, then:
 => Need to install the 'arts' package as I searched the internet:
 'debian arts' (install the latest version)
 => But in order to install arts, it was necessary to first install the other 2 libraries
 I do not remember the exact name but it began with 'libart',

 Once you managed to install the arts, you can proceed with the installation of freenx;)

 However freeenx works badly with unity, I had to install kde4.

---

### Post by smrm on 2011-11-10
Hello,
Anyone has solved the installation problem with FreeNX? If so, it is possible a step-by-step help? I wish avoid the passage to NX-server free and leave it as last chance.
THX!!!

---

### Post by dieseyer on 2011-11-15
[COLOR=#000000][FONT=Arial]After this steps on Ubuntu Server 10.11 (without KDE/Gnome) I can open a terminal-session with [/FONT][/COLOR]'NX Client for Windows v3.5.0-7'.
[COLOR=#000000][FONT=Arial]
~$ sudo apt-get install python-software-properties[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo add-apt-repository ppa:freenx-team[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo sed -i 's/oneiric/lucid/g' /etc/apt/sources.list.d/freenx-team-ppa-oneiric.list[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo apt-get update && sudo apt-get upgrade[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ wget [http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-common_0.2.41-8_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-common_0.2.41-8_all.deb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i esound-common_0.2.41-8_all.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ wget [http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd0_0.2.41-8_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd0_0.2.41-8_amd64.deb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i libesd0_0.2.41-8_amd64.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# error in previous line [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo apt-get -f install[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# repeat[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i esound-common_0.2.41-8_all.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i libesd0_0.2.41-8_amd64.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ wget [http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-clients_0.2.41-8_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-clients_0.2.41-8_amd64.deb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i esound-clients_0.2.41-8_amd64.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo apt-get install freenx[/FONT][/COLOR]

I'm not Linux-Guru an I don't write good english, but I hop this is helpful.

---

### Post by Mahelita on 2011-11-25
> **dieseyer said:**
> [COLOR=#000000][FONT=Arial]After this steps on Ubuntu Server 10.11 (without KDE/Gnome) I can open a terminal-session with [/FONT][/COLOR]'NX Client for Windows v3.5.0-7'.
[COLOR=#000000][FONT=Arial]
~$ sudo apt-get install python-software-properties[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo add-apt-repository ppa:freenx-team[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo sed -i 's/oneiric/lucid/g' /etc/apt/sources.list.d/freenx-team-ppa-oneiric.list[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo apt-get update && sudo apt-get upgrade[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ wget [http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-common_0.2.41-8_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-common_0.2.41-8_all.deb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i esound-common_0.2.41-8_all.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ wget [http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd0_0.2.41-8_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd0_0.2.41-8_amd64.deb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i libesd0_0.2.41-8_amd64.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# error in previous line [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo apt-get -f install[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# repeat[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i esound-common_0.2.41-8_all.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i libesd0_0.2.41-8_amd64.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ wget [http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-clients_0.2.41-8_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-clients_0.2.41-8_amd64.deb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i esound-clients_0.2.41-8_amd64.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo apt-get install freenx[/FONT][/COLOR]

I'm not Linux-Guru an I don't write good english, but I hop this is helpful.

Works fine for terminal session but connection is lost as soon as one tries to start GNOME/KDE!!

---

### Post by RENOO on 2011-11-28
Hello there,

The technic looked fine to me . good job.

Unfortunatly, it didn't work for me.
Here is my error message, while I tried the last line


```

..
Setting up xvnc4viewer (4.1.1+xorg4.3.0-37ubuntu3) ...
update-alternatives: using /usr/bin/xvnc4viewer to provide /usr/bin/vncviewer (vncviewer) in auto mode.
Setting up freenx-server (0.7.3.git110520.3884279-0ubuntu1ppa4) ...
dpkg: error processing freenx-server (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of freenx-rdp:
 freenx-rdp depends on freenx-server; however:
  Package freenx-server is not configured yet.
dpkg: error processing freenx-rdp (--configure):
 dependency problems - leaving unconfigured
Setting up freenx-smb (0.7.3.git110520.3884279-0ubuntu1ppa4) ...
dpkg: dependency problems prevent configuration of freenx-session-launcher:
 freenx-session-launcher depends on freenx-server | nxnode; however:
  Package freenx-server is not configured yet.
  Package nxnode is not installed.
dpkg: error processing freenx-session-launcher (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of freenx:
 freenx depends on freenx-server; however:
  Package freenx-server is not configured yet.
 freenx depends on freenx-rdp; however:
  Package freenx-rdp is not configured yet.
 freenx depends on freenx-session-launcher; however:
  Package freenx-session-launcher is not configured yet.
dpkg: error prNo apport report written because the error message indicates its a followup error from a previous failure.
                                        No apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              ocessing freenx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of freenx-vnc:
 freenx-vnc depends on freenx-server; however:
  Package freenx-server is not configured yet.
dpkg: error processing freenx-vnc (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 freenx-server
 freenx-rdp
 freenx-session-launcher
 freenx
 freenx-vnc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

TOo bad

---

### Post by JamesGeddes on 2011-12-02
Has anyone managed to make any progress on this?

Here is the error message I receive;

```
james@ubuntu:~$ sudo apt-get install freenx
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 freenx : Depends: esound-clients but it is not installable or
                   arts but it is not installable
E: Unable to correct problems, you have held broken packages.

```

I've also started a _[thread listing my other problems]("http://ubuntuforums.org/showthread.php?p=11506497#post11506497")_, so if anyone can help it would be most appreciated! :guitar:

Thanks everyone!


James

---

### Post by syborfical on 2011-12-03
I use upgraded my sever now free NX wont work not happy.

Anyone know how to get headless resumalbe VNC sessions working?

---

### Post by JamesGeddes on 2011-12-03
VNC isn't really secure, which is why I want to get NX working

I've no managed to (I think) install it, however get the following messages returned when I try and connect with the NX client;

**First Message**
```
Xsession: unable to launch "gnome-session" X session --- "gnome-session" not 
found; falling back to default session.

```

**Second Message**
```
Xsession: unable to start X session --- no "/home/james/.xsession" file, no 
"/home/james/.Xsession" file, no session managers, no window managers, and no 
terminal emulators found; aborting.
```

What is going wrong there?

Thanks everyone!

James

---

### Post by claudiuceus on 2012-03-12
If you want to install Free NX on Intel based PCs, you will have to rename amd for i386, for instance:

wget [COLOR=#000000][FONT=Arial][http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd0_0.2.41-8_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd0_0.2.41-8_amd64.deb)
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo dpkg -i libesd0_0.2.41-8_amd64.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo dpkg -i libesd0_0.2.41-8_amd64.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]wget [http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-clients_0.2.41-8_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-clients_0.2.41-8_amd64.deb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo dpkg -i esound-clients_0.2.41-8_amd64.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
will be

wget [/FONT][/COLOR][COLOR=#000000][FONT=Arial][http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd0_0.2.41-8_i386.deb]("http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd0_0.2.41-8_amd64.deb")[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo dpkg -i libesd0_0.2.41-8_i386.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]sudo dpkg -i libesd0_0.2.41-8_i386.deb

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]wget [http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-clients_0.2.41-8_i386.deb]("http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-clients_0.2.41-8_amd64.deb")[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]sudo dpkg -i esound-clients_0.2.41-8_i386.deb[/FONT][/COLOR]

I hope this help you guys!

> **dieseyer said:**
> [COLOR=#000000][FONT=Arial]After this steps on Ubuntu Server 10.11 (without KDE/Gnome) I can open a terminal-session with [/FONT][/COLOR]'NX Client for Windows v3.5.0-7'.
[COLOR=#000000][FONT=Arial]
~$ sudo apt-get install python-software-properties[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo add-apt-repository ppa:freenx-team[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo sed -i 's/oneiric/lucid/g' /etc/apt/sources.list.d/freenx-team-ppa-oneiric.list[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo apt-get update && sudo apt-get upgrade[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ wget [http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-common_0.2.41-8_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-common_0.2.41-8_all.deb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i esound-common_0.2.41-8_all.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ wget [http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd0_0.2.41-8_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd0_0.2.41-8_amd64.deb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i libesd0_0.2.41-8_amd64.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# error in previous line [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo apt-get -f install[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# repeat[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i esound-common_0.2.41-8_all.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i libesd0_0.2.41-8_amd64.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ wget [http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-clients_0.2.41-8_amd64.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-clients_0.2.41-8_amd64.deb)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]~$ sudo dpkg -i esound-clients_0.2.41-8_amd64.deb[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]~$ sudo apt-get install freenx[/FONT][/COLOR]

I'm not Linux-Guru an I don't write good english, but I hop this is helpful.

---

### Post by andrew.hou68 on 2012-03-14
I have the same problem, too.
The fix seems not works for GNOME/KDE.
Does Fedora work?

---

### Post by wwlliiuu2009 on 2012-04-20
Hi, Guys,

I have developed a shell script, which compile and install the freenx server on Ubuntu 11.10. 

Please take a look at my blog: [http://notepad2.blogspot.com.au/2012/04/install-freenx-server-on-ubuntu-1110.html]("http://notepad2.blogspot.com.au/2012/04/install-freenx-server-on-ubuntu-1110.html")

You can just download and run the script on your Ubuntu Linux 11.10. It does everything for you. Tested.

---

### Post by wwlliiuu2009 on 2012-04-20
> **uniomni said:**
> The best instructions I have seen are
[http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html](http://notepad2.blogspot.com/2011/05/install-freenx-server-on-ubuntu-1004.html)

and I verified they work for 11.04
However, on 11.10 I get the same problem as everyone else.

Installing from NoMachine is not an option for us because they limit the number of simultaneous logins to 2

Can someone please fix the deb files or let us know how to work around the broken packages?

Thanks
Ole Nielsen

Hi, I am the author of the instructions for 11.04. 

I have now developed a shell script, which compile and install the freenx server on Ubuntu 11.10. 

You can take a look at my blog: [http://notepad2.blogspot.com.au/2012/04/install-freenx-server-on-ubuntu-1110.html]("http://notepad2.blogspot.com.au/2012/04/install-freenx-server-on-ubuntu-1110.html")

---


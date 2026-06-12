---
title: "Easiest way to setup Home FTP server"
date: 2011-11-04
forum: General Help
---

### Post by snipestech on 2011-11-04
I would like to learn how to setup and ftp server at my home that I can access from anywhere.

Running Ubuntu Studio
2x Dual core Opterons
2 Gb ddr2 
500 Gb HDD
Gforce 5200 Gpu 

Any help or being pointed in the right direction would be greatly appreciated.

Tx in advance

---

### Post by jonobr on 2011-11-04
I use vsftpd you can get it in the repos
Its configured using config files in /etc/vsftp

there are also other gui based ones such as proftpd

---

### Post by snipestech on 2011-11-04
Okay thank you very much do you know of any tutorials or howto I am totally new to this.I have an Ubuntu bible but all I see is how to configure wed mail dhcp dns printnfs and samba server.
can you recommend anything source of info on this.
Thanks again

---

### Post by jonobr on 2011-11-04
Hello


To start , you need to install the package,

You can do that by going to the synaptic package manger and searching for vsftpd

or by going to the command line terminal
applications-> accessories -> terminal


and typing sudo apt-get install vsftpd
It will ask if you want to proceed,

say yes
and it should install.

You now need to configure vsftpd to suit your needs.

If you
> gedit /etc/vsftpd/vsftpd.conf

this file is where you make changes, there are notes in there on what each field is and does

You can start stop and restart from the terimanl using

```

sudo /etc/init.d/vsftpf start
sudo /etc/init.d/vsftpf stop
sudo /etc/init.d/vsftpf restart

```

You can test if its working by doing 
ftp 127.0.0.1
in the terimal

hopefully it will look for the login

you could also open firefox and eneter 
[ftp://127.0.0.1](ftp://127.0.0.1)

From another machine  do the same
except put in the ip address of the ftp server

---

### Post by snipestech on 2011-11-04
Cool will try that and get back 
Tx

---

### Post by snipestech on 2011-11-04
I did it and got this 
wesley@ubuntu:~$ sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  proftpd-basic
The following NEW packages will be installed:
  vsftpd
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/117kB of archives.
After this operation, 1,761kB disk space will be freed.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 178933 files and directories currently installed.)
Removing proftpd-basic ...
ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Selecting previously deselected package vsftpd.
(Reading database ... 178861 files and directories currently installed.)
Unpacking vsftpd (from .../vsftpd_2.3.0~pre2-4ubuntu2.2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up vsftpd (2.3.0~pre2-4ubuntu2.2) ...
vsftpd user (ftp) already exists, doing nothing.
Adding user ftp to group ftp
vsftpd start/running, process 2401

Then entered gedit /etc/vsftpd/vsftpd.con and got a blank page

---

### Post by azmyth on 2011-11-04
Try

sudo gedit /etc/vsftpd.conf

---

### Post by jonobr on 2011-11-04
Or else if that doesnt work

sudo find / -name vsftpd.conf 

but it should be there somewhere!

---

### Post by Hatsune Miku on 2011-11-04
> **snipestech said:**
> I would like to learn how to setup and ftp server at my home that I can access from anywhere.

Running Ubuntu Studio
2x Dual core Opterons
2 Gb ddr2 
500 Gb HDD
Gforce 5200 Gpu 

Any help or being pointed in the right direction would be greatly appreciated.

Tx in advance

Save yourself some time hun, proftpd. It automatically sets itself up, all you need to do is install it and open the ports up. Its already configured to lock itself down, also it has some pretty good transfer speeds as well.

P.S. Make sure to open ports 20/21 on your firewall ;)

---

### Post by jonobr on 2011-11-04
Hey there
Hatsune Miku advice is good but just fyi, if you decide to change,
remove vsftpd first as the thing will try use the same ports.

```
sudo apt-get remove vsftpd
```
or remove using package manager, which ever suits you!

---

### Post by Hatsune Miku on 2011-11-04
> **jonobr said:**
> Hey there
Hatsune Miku advice is good but just fyi, if you decide to change,
remove vsftpd first as the thing will try use the same ports.

```
sudo apt-get remove vsftpd
```
or remove using package manager, which ever suits you!

Yes, make sure you have vsftpd turn off first!

```
sudo service vsftpd stop
```

And then remove it 

```
sudo apt-get remove vsftpd
```(Thanks jonobr)

Then install proftpd

```
sudo apt-get install proftpd
```

Then to be a little tidy! Clean/remove any unused packages :)

```
sudo apt-get autoremove && sudo apt-get autoclean
```

Good luck :3

---

### Post by snipestech on 2011-11-05
Thank you so much for your help.I just got in from work and tried the suggestion and heres what I got

The home directory `/home/ftp' already exists.  Not copying from `/etc/skel'.
`/usr/share/proftpd/templates/welcome.msg' -> `/home/ftp/welcome.msg.proftpd-new'
ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.
I do not have any firewalls unless this has one by default.If so how would I know?
Also I am behind a router and cable modem.Do i have to port forward to my router swtch ?

---

### Post by Hatsune Miku on 2011-11-05
> **snipestech said:**
> Thank you so much for your help.I just got in from work and tried the suggestion and heres what I got

The home directory `/home/ftp' already exists.  Not copying from `/etc/skel'.
`/usr/share/proftpd/templates/welcome.msg' -> `/home/ftp/welcome.msg.proftpd-new'
ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.
I do not have any firewalls unless this has one by default.If so how would I know?
Also I am behind a router and cable modem.Do i have to port forward to my router swtch ?

vsftpd left its configuration crap everywhere... your going to need to find it and delete it :/

---

### Post by snipestech on 2011-11-06
O well! 
I guess i have a new project!

---

### Post by Lars Noodén on 2011-11-06
> **snipestech said:**
> O well! 
I guess i have a new project!

If you want to do it the easy way, just install [OpenSSH-server](http://packages.ubuntu.com/oneiric/openssh-server).  SFTP works out of the box and you have built-in clients like Nautilus.

---

### Post by snipestech on 2011-11-08
> **Hatsune Miku said:**
> vsftpd left its configuration crap everywhere... your going to need to find it and delete it :/
Ok so now it seems to have installed but also seems like there is an error at the end:

wesley@ubuntu:~$ sudo apt-get install proftpd
[sudo] password for wesley: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'proftpd-basic' instead of 'proftpd'
Suggested packages:
  proftpd-doc proftpd-mod-mysql proftpd-mod-pgsql proftpd-mod-ldap
  proftpd-mod-odbc proftpd-mod-sqlite openbsd-inetd inet-superserver
The following NEW packages will be installed:
  proftpd-basic
0 upgraded, 1 newly installed, 0 to remove and 329 not upgraded.
Need to get 880kB of archives.
After this operation, 2,204kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe proftpd-basic i386 1.3.2e-4ubuntu0.1 [880kB]
Fetched 880kB in 1s (512kB/s)        
Preconfiguring packages ...
Selecting previously deselected package proftpd-basic.
(Reading database ... 154875 files and directories currently installed.)
Unpacking proftpd-basic (from .../proftpd-basic_1.3.2e-4ubuntu0.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up proftpd-basic (1.3.2e-4ubuntu0.1) ...
grep: /etc/inetd.conf: No such file or directory
Warning: The home dir /var/run/proftpd you specified can't be accessed: No such file or directory
Adding system user `proftpd' (UID 113) ...
Adding new user `proftpd' (UID 113) with group `nogroup' ...
Not creating home directory `/var/run/proftpd'.
Adding system user `ftp' (UID 114) ...
Adding new user `ftp' (UID 114) with group `nogroup' ...
Creating home directory `/home/ftp' ...
`/usr/share/proftpd/templates/welcome.msg' -> `/home/ftp/welcome.msg.proftpd-new'
ProFTPd warning: cannot start neither in standalone nor in inetd/xinetd mode. Check your configuration.
wesley@ubuntu:~$

---

### Post by snipestech on 2011-11-08
> **Lars Noodén said:**
> If you want to do it the easy way, just install [OpenSSH-server]("http://packages.ubuntu.com/oneiric/openssh-server").  SFTP works out of the box and you have built-in clients like Nautilus.
Okay finally got this one running Thanks a bunch !
Now how do I access it from within my network and from the web 
Thanks in advance!

---

### Post by jonobr on 2011-11-08
Hey There

Im late to the party.

Sometimes when you remove an application it will leave configuration files around the place.

You can do a 

```
sudo apt-get --purge -remove <program-name>
```

this should remove different configs associated with the program.

Sorry I didnt get back to you sooner, but its good to know as you will run into this again,when you try to reinstall programs and wonder why its holding old config files

Cheers

JB

---

### Post by snipestech on 2011-11-08
> **jonobr said:**
> Hey There

Im late to the party.

Sometimes when you remove an application it will leave configuration files around the place.

You can do a 

```
sudo apt-get --purge -remove <program-name>
```this should remove different configs associated with the program.

Sorry I didnt get back to you sooner, but its good to know as you will run into this again,when you try to reinstall programs and wonder why its holding old config files

Cheers

JB
Thanks I got it to work and can access it.Now how would I go about accessing from the web what do i need to do.I want to set this up as my own personal server.
I am with comcast and I have a modem then a wifi router.

Thanks again to all who have helped you guys are great!

---

### Post by jonobr on 2011-11-08
Hello

Theres 3 things that need to be done for this.
1- the internal ip address of your server needs to be known.
2- You need to be able to connect to your home network via its real IP address.
3- Port mapping on your router

For point 1 - The address needs to remain the same or you need to be able to track it. You can do this by assigning a static Internal Ip address on your server or assigning the same dynamic IP from your router. Each time the server comes up, it will have the same address

For point 2 you need to know the public IP address/name of your router.

The addresses handed out internally on your network will be 192.168.1.x or something like that,
however your internet connection will have an external IP.

In most cases this IP address will change over time, unless you asked your ISP to have a static IP address.

If you had a static IP address you would be able to connect to your machine no problem, however, if its dynamic you will need a service that will track the changed IP address

Something like [No-ip]("http://www.no-ip.com/") offer a free service to have a name associated with your IP and track it.

That way you can always connect to your home network,

For point 3 it requires you to (once you know where to connect to) modify your router to accept connections from external networks and map them to internal ones.

Therefore if a session comes in for port 22 from outside, you would redirect or map that session to an internal IP.
That internal IP address should be the one defined in point 1.
If you look at your router manual it should tell you how to map ports on your device

Cheers

Jonobr

---

### Post by snipestech on 2011-11-09
Thanks just got in from work but will follow through with that thanks for the detailed info

---


---
title: "what is the secret to make folder sharing work between ubuntu machines?"
date: 2011-08-09
forum: General Help
---

### Post by sdowney717 on 2011-08-09
[https://help.ubuntu.com/8.04/internet/C/networking-shares.html](https://help.ubuntu.com/8.04/internet/C/networking-shares.html)

Found that makes it seem so easy.

I rightclicker folder said to share it installed files samba etc... I logged out and in on both machines.
When I goto network, all I see is my own machine. I am on the same router!

I wish to move a 1gb folder, If I have to use a thumb drive so be it!
but it would be nice to just use the sharing.

this procedure also is dead
[http://www.jonathanmoeller.com/screed/?p=1590](http://www.jonathanmoeller.com/screed/?p=1590)

what I need is some troubleshoot guide, not some flake site that says click this that and its so easy your done. I have rarely ever seen unusual linux things just work without in depth detailed painstaking analysis and some hair pulling to go along.

---

### Post by sdowney717 on 2011-08-09
I gave up trying to do it and used the always trustworthy usb drive.

---

### Post by omelette on 2011-08-09
Damn, I find Ubuntu without a doubt the easiest of all the OS's I've tried to share files/folders on - at least on a wireless network, don't have much call for the wired variety.  Or at least to share files from/to an Ubuntu PC, I don't have Ubuntu on both my machines.  Plus setting it up is pretty much automated.  You want a really crap OS the share files on, try Fedora 15.  I wrote a long tedious rant today about this very thing on the Fedora forum...

Just for laughs, I'll boot up my laptop with the Ubuntu LiveCD and give it a go.

Edit:  Well I've just tried it, Ubuntu LiveCD <-> Ubuntu 11.04, folder & filesharing worked perfectly first time!  Although it did need to install all the Samba stuff from the repository in order to do so.  But then not a problem as Wireless-sharing also worked without a hitch which was nice to see!  On the other hand, none of this 'automation' takes place on Fedora 15 - it's a tedious slog to have to install all the Samba stuff (once you've circumvented crap like Selinux) and even then, installing 'Samba' doesn't automatically include everything necessary, just the required Samba dependencies, you still have to try and figure out what else is needed.  And even then, it still doesn't work - you get a 'password-refused' error when you are prompted to enter you password.....

Ubuntu is sheer bliss (imo) in comparasion when it comes to filesharing.

---

### Post by Synoc on 2011-08-09
just to be clear... you need to  share files between two Linux machines right?

if that is the case, you CAN use samba and it will work. OR you can use NFS which is what Linux uses natively as its Network File Sharing technology. Samba is to make it talk to Windows.

---

### Post by Clayton7510 on 2011-08-09
+1 on using NFS for file sharing with Ubuntu.

---

### Post by 3rdalbum on 2011-08-09
I never got that particular method to work, but the Ubuntu help documentation now says to use the shares-admin program:

```
gksudo shares-admin
```

which **has** worked for me, and it's not much more difficult than the Nautilus method.

Remember, you're attempting to follow instructions from Ubuntu 8.04 on what's presumably a later version of Ubuntu; that never works out well :)  Shares-admin is preinstalled on Ubuntu 8.04 and above, I believe.

Another method I used to use was the system-config-samba program; also quite easy, and more powerful.

---

### Post by sdowney717 on 2011-08-10
I had tried shares-admin, nothing

I just ran the samba config
this is what is there

which is odd because in Nautilus I am sharing maps
and it does not show there
I would think it should, see what I mean about weird unusual incomprehensible stuff.
so whatever they do, they dont communicate to each other?

---

### Post by sdowney717 on 2011-08-10
here is what the machine sees for network places
This and the other PC are both running 11.04
both only show there own PC name in this place

---

### Post by sdowney717 on 2011-08-10
here is what the other pc shows in network, also just itself

so if the machines are not visible to each other, then no folders will be

---

### Post by sdowney717 on 2011-08-10
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

still no go with NFS, likely because the instructions are leaving out steps needed to make this work. It is giving trouble with /files? So I tried making a folder called 'files'
I went thru his example and go stopped on 'files'
obviously I have no idea what I am doing. And people cant write good enough instructions.

> For Full Read Write Permissions allowing any computer from 192.168.1.1 through 192.168.1.255

/files 192.168.1.1/24(rw,no_root_squash,async)

Or for Read Only from a single machine

/files 192.168.1.2 (ro,async)

save this file and exit

A client can be specified either by name or IP address. Wildcards (*) are allowed in names, as are netmasks (e.g. /24) following IP addresses, but should usually be avoided for security reasons.

A client specification may be followed by a set of options, in parenthesis. It is important not to leave any space between the last client specification character and the opening parenthesis, since spaces are intrepreted as client seperators.

Now you need to restart NFS server using the following command

sudo /etc/init.d/nfs-kernel-server restart

ok did that and get an error

```
scott@scott-P5QC:~$ sudo /etc/init.d/nfs-kernel-server restart
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.1.1/24:/files".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

**exportfs: Warning: /files does not exist**
                                                                         [ OK ]
 * Starting NFS kernel daemon                                            [ OK ] 
scott@scott-P5QC:~$ 

```

---

### Post by YesWeCan on 2011-08-10
Hi. What version of Ubuntu are you using?
Since 10.04 (maybe earlier) I have always shared files using the "Places/Connect to Server..." and then chosen SSH.
On the other machine (the one I am trying to connect to) I run SSH server.
I get a normal file browsing window on my machine and can navigate it and copy and paste to and from it.
Is this what you are trying to do?

---

### Post by sdowney717 on 2011-08-11
both are running 11.04

I shared using nautilus
All I am doing is clicking network and not seeing the computers.

---

### Post by YesWeCan on 2011-08-11
Folder sharing? You may be trying to do this using the Windows networking method. I don't use this myself so I cannot comment.

I am using an SSH (secure shell) connection. I just make one computer an SSH server and connect to it from the other. It's super easy.

On the computer that will act as a server,
[COLOR="Navy"]sudo apt-get install ssh[/COLOR]
[COLOR="Navy"]ifconfig[/COLOR] to find the IP address of this computer
and make sure, if you have a firewall, that it allows port 22 access

On the client computer, Places/Connect To Server...
select Service Type SSH
enter the IP address in the Server: field
enter your User name on the server
tick "add bookmark" so you get a handy shortcut in your Places menu
Click "connect" and enter your password and say OK to the security warning.

Then you should get a new file browser window which shows files on the server.

---

### Post by sdowney717 on 2011-08-21
Thanks, I just tried this and it works really well.
I was able to copy and paste files.
Does the folder sharing settings on the 'server' mean anything using ssh?

---

### Post by XEtedBear on 2011-11-26
> **YesWeCan said:**
> 
Then you should get a new file browser window which shows files on the server.


Aaah - the  fatal word '..should...'

What if it doesn't? Do I shout at the computer saying that it should do this - or what?

---


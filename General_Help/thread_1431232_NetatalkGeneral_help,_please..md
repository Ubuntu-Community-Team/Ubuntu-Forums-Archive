---
title: "Netatalk/General help, please."
date: 2010-03-16
forum: General Help
---

### Post by ChazzR on 2010-03-16
Hi to anyone and everyone who is willing to read this and offer help. I am brand new to ubuntu (suggested to me by my brother-in-law). Again, let me stress that I am brand new to using ubuntu/netatalk etc so any help would be greatly appreciated. 

Goal:
My desire is to create a simple home server (printer/file sharing/itunes). 

Machine(s):
1 HP Pavillion 8495 P3 550mhz, 19GB hard drive (OS drive), 82GB maxtor drive (file sharing drive), 500gb WD drive (file sharing drive). Ubuntu 9.10 downloaded and running on machine newest version

2 MacBook Pros running latest version of Snow Leopard

1 iphone connected to network

1 HP printer - currently a usb hookup to one of the MBPs

History:
Installed ubuntu 9.10 last night (3.15.10) and have it up and running with no issues. All updates are downloaded and installed. I have tried to download and run Netatalk after doing some research online and identifying that it is designed to work with macs.

I have followed [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/) as guide to run the setup but have not been successful. 

As I try to install I can only get so far before the terminal commands fail. It gives me error and cannot find netatalk to proceed. Here is what the terminal shows:

comroot@StorageServer:/home/charlie/netatalk/netatalk# sudo aptitude install devscripts dpkg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

root@StorageServer:/home/charlie/netatalk/netatalk# sudo su
root@StorageServer:/home/charlie/netatalk/netatalk# apt-get build-dep netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@StorageServer:/home/charlie/netatalk/netatalk# DEB_BUILD_OPTIONS=ssl debuild -i -us -uc -b
debuild: fatal error at line 630:
cannot find readable debian/changelog anywhere!
Are you in the source code tree?
root@StorageServer:/home/charlie/netatalk/netatalk# cd netatalk
bash: cd: netatalk: No such file or directory
root@StorageServer:/home/charlie/netatalk/netatalk# dir
netatalk-2.0.4~beta2  netatalk_2.0.4~beta2-5ubuntu2.diff.gz  netatalk_2.0.4~beta2-5ubuntu2.dsc    netatalk_2.0.4~beta2.orig.tar.gz
[COLOR=#888888]
[COLOR=Black]As I stated above, I really have no clue on a lot of this. I was simply following the instructions step by step and got stuck. I appreciate any and all feedback/help

Thanks:D
[/COLOR][/COLOR]

---

### Post by srs5694 on 2010-03-16
Netatalk implements AppleTalk, which was used by Mac OS Classic (that is, Mac OS 9 and earlier). Mac OS X is Unix-based, and it supports SMB/CIFS (Samba) and NFS in addition to AppleTalk. Since Samba and NFS are both fairly popular and easily implemented with Ubuntu, you'll probably find it easier, and at least as effective, to use one of them rather than Netatalk to provide file-sharing between your systems. If you want printer sharing, Samba will work, but NFS won't; but the better option is to use CUPS, which is the default printing tool on Ubuntu. OS X directly supports CUPS.

If there's a specific reason you want to use Netatalk rather than Samba, NFS, or CUPS, please post details. It could be there's an easier way to accomplish your goals.

FWIW, I used to run Netatalk on my home office network, but I haven't bothered for at least two or three years. It's just not worth it to me any more. I've got a couple of OS X systems, and they work fine with Samba and CUPS. I've also got an old iMac that can still boot OS 9, but I seldom bother to do so.

---

### Post by ChazzR on 2010-03-21
Still no luck. Is there a simple guide somewhere that someone would be willing to point me to that has STEP by STEP instructions. I've found a few but always manage to get stuck. I'm looking for obnoxiously simple instructions, think paint by number. I need to know from start to finish exactly every step, screen shots would be great. 

I'm beginning to wish I never started this, can someone ANYONE renew my faith?

Thanks

---

### Post by a.walker on 2010-03-21
I've found that ebox is really easy to set up. (It is a special version of Ubuntu Server). Google "ebox".

It is also dead simple to set up a file server with FreeNAS.

Both of them have a web interface so that you can administer the computer through another computer's web browser.

---

### Post by soltanis on 2010-03-21
It is my understanding you want to run a file server for your Macs, with good built-in support (i.e. Finder support). In this case, I suggest Samba (SMB) as opposed to Netatalk (AFP); Samba is easier to set up.

(1)
**Install Samba server (if not already installed).**
In a terminal:
```

sudo apt-get install samba smbfs

```

(2)
**Figure out where your external disks are mounted.**

You mentioned you have one or two external disks you want to serve files from. I assume you have them formatted correctly, and they're plugged in, mounted, and ready to use.

If not, please let me know.

Otherwise, in a terminal:
```

cd /media
ls

```

The directories in this folder should correspond to your external disks. If you have other external media plugged in, they will also show up here. Write down or remember the names of these directories. For example, if I had a disk named "External", and I did:

```

$ cd /media && ls
External

```

Then the path to your disk is /media/External (uppercase counts).

(3)
**Configure your Samba install.**

I suggest you ignore the default configuration file and write your own. This is how:

In the terminal:
```

sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.old
sudo gedit /etc/samba/smb.conf

```

This will pop up gedit with a blank, new file, the samba configuration file. Don't close the terminal window (or gedit will close too).

Set some general configuration options for your file. I suggest the following layout:

```

[global]
netbios name = <Set the name of your computer here>
workgroup = WORKGROUP # this always works
security = user

[<file share name>]
path = /media/<your drive(s)>
browseable = yes
read only = no
valid users = <your username here>
force user = <your username here>
force group = <your username here>

```

REPLACE:
<your computer name> with the NetBIOS name you want (not that important)
<file share name> with a name you want the share to have
<your drive(s)> with the correct path to your drives
<your username here> with the username you want people to log in under

NOTE:
On your disks, you should make sure that the root directory is owned by and is writable by YOUR user. This is to make sure that when your Macs log in they will have appropriate permissions.

If you have permissions problems, I'll help you solve them. Otherwise, next is

(4)
**Give your samba user a password**

Your username exists on your computer but to Samba it has no password. To solve this, do this in a terminal:

```

sudo smbpasswd -a <your username>

```

Enter a password. It does not have to be the same password that you log in to the computer with.

(5)
**Restart the service**

```

sudo /etc/init.d/smb restart

```

Once this is done your Mac computers should be able to access your server.
In Finder, do Apple+K to bring up the Connect to server dialog. Type:

```

smb://your.server.ip.address/

```
Replace with your server's IP address, obviously.

You should get a username/password dialog, enter the appropriate credentials (you might want to store them). Mac will then make it's little "mount" noise and you should have access to the drive. From there drag+drop etc all works out well.

If the connect dialog is stuck on the progress bar for connecting, chances are your firewall is blocking the Samba port.

If you get something in Finder that says "Connection Failed" then Mac isn't using the right user. On that bar there will be a button labeled "Connect As" which will take you to the username/password dialog.

If something doesn't work I'll be willing to help. That's what these forums are for.

---

### Post by readme-txt on 2010-03-27
Hi,
I am new to Ubuntu as well as to Unix in general. Also, I am trying to do the same as ChazzR.
I have a PC running Ubuntu 9.1, a MacBook Pro as well as another PC running Vista (yes, I know it sucks, but hopefully in the next couple of weeks I'll say goodbye to Windows altogether... hate Windows!!)

Anyway, I have managed to do the following, interestingly out of the box without typing any commands in Ubuntu: (Is it because I'm using a newer version of Ubuntu I don't have to type all of those commands in Terminal??)
1. I managed to remote control from Mac to Ubuntu using the command: "vnc://<ip-address>" from the Finder's Go>Connect to Server.

2. Ubuntu was able to view all the shared drives in my Windows PC and Windows was able to view Ubuntu's shared files.

Now, here is where I'm stuck. I can't share any files either from my Mac to Ubuntu or from Ubuntu to my Mac. Soltanis (thanks for the great instructions!) was saying that this problem could be due to my firewall, but if this was the case, I wouldn't be able to VNC Ubuntu from my Mac. I tried to follow these instructions: [http://www.kremalicious.com/2008/06/...achine-volume/](http://www.kremalicious.com/2008/06/...achine-volume/) but I only got error after error. I think it's because I got a newer version of Ubuntu?

Anyway, when I type the following command on my Mac "smb://<ip-address>" it asks me for a password, but I get an incorrect password or username error. I only have 1 username and password and I'm sure it's the correct one.

I then tried to follow Soltanis instructions, when you say to configure Samba (change the smb.conf file and then to change it's password. Did it, but I got the same error.

I will appreciate if someone could help me. The sonner I get this working, the sonner I will start my next project: "Getting rid off Windows!!!"

---

### Post by timhees on 2010-03-27
I am doing this also. I am able to see the shared folder on my Mac and am able to transfer files from the Mac to the Ubuntu machine.

my problem is that I have 8 drives in the Ubuntu box and can not see them on the Mac.

in this file,I did it like this but am not sure how to list the internal drives path. Do I just put them 
path = /media/drive1,drive2,etc

or do they need to be listed separately with a different path = /for each one? 

I will try this but want to get it right

```

[global]
netbios name = <Set the name of your computer here>
workgroup = WORKGROUP # this always works
security = user

[<file share name>]
path = /media/<your drive(s)>
browseable = yes
read only = no
valid users = <your username here>
force user = <your username here>
force group = <your username here>
```

---

### Post by readme-txt on 2010-03-31
GOT IT WORKING!!!!!
I spent countless hours trying to figure this out.
Now, the following tutorial is for the "BEGINNER", "NEW TO UBUNTU" so there might be a few things many people will think its obvious, but this is for the beginner...
Big thanks to Soltanis! (this is based on his tutorial)

Best if you do a clean install of Ubuntu (I'm using version 9.1)
When setting up Ubuntu, make sure the computer name is less than 15 characters.
After installation is complete, install all updates.

Setup Ubuntu to be shared with Mac and Windows
Goto System>Preferences>Remote Desktop
Tick on Sharing (and any other options you may want.

Install and Setup Samba
Install Samba from Applications>Ubuntu Software Center, click on Get Free Software and search for Samba
Install Samba

Editing Samba’s smb.conf file
First, rename original file and then open a new file using gedit

sudo mv /etc/samba/smb.conf etc/samba/smb.conf.old
sudo gedit /etc/samba/smb.conf

Copy and Paste the following command:

[global]
netbios name = <Set the name of your computer here>
workgroup = WORKGROUP # this always works
security = user

[<file share name>]
path = /media/<your drive(s)>
browseable = yes
read only = no
valid users = <your username here>
force user = <your username here>
force group = <your username here>


Replace:
<your computer name> with the NetBIOS name you want (very important)
<file share name> with a name you want the share to have
<your drive(s)> with the correct path to your drives
<your username here> with the username you want people to log in under

If you’re sharing more than 1 share folder, do the following:

[<file share name A>]
path = /media/<your drive A>
browseable = yes
read only = no
valid users = <your username here>
force user = <your username here>
force group = <your username here>

[<file share name B>]
path = /media/<your drive B>
browseable = yes
read only = no
valid users = <your username here>
force user = <your username here>
force group = <your username here>

Give Samba a username and password:
sudo smbpasswd -a <your username>

Enter password (I used the same password as Ubuntu)

Restart Samba services:
sudo /etc/init.d/smb restart

On a Mac:
Under Finder click on Go>Connect to Server

To open shared folders type:
smb://<name of server>.local (ie. “smb://ubuntu.local”)

To remote desktop type:
vnc://<name of server>.local (ie. vnc://ubuntu.local”)

On Windows:
To VNC:
Install VNC and then type the server name or IP address (including .local at the end)

To open shared folders:
Click on Start>Run \\<name of server>.local (ie. \\ubuntu.local”) or IP address

And that's it!!!
As I said before, this is pretty much the same as what Soltanis wrote...
Hope this helps to all new Ubuntu users :)

---

### Post by uin9112037 on 2010-05-02
[QUOTE=ChazzR]comroot@StorageServer:/home/charlie/netatalk/netatalk# sudo aptitude install devscripts dpkg-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done

root@StorageServer:/home/charlie/netatalk/netatalk# sudo su
root@StorageServer:/home/charlie/netatalk/netatalk# apt-get build-dep netatalk
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
root@StorageServer:/home/charlie/netatalk/netatalk# DEB_BUILD_OPTIONS=ssl debuild -i -us -uc -b
debuild: fatal error at line 630:
cannot find readable debian/changelog anywhere!
Are you in the source code tree?
root@StorageServer:/home/charlie/netatalk/netatalk# cd netatalk
bash: cd: netatalk: No such file or directory
root@StorageServer:/home/charlie/netatalk/netatalk# dir
netatalk-2.0.4~beta2 netatalk_2.0.4~beta2-5ubuntu2.diff.gz netatalk_2.0.4~beta2-5ubuntu2.dsc netatalk_2.0.4~beta2.orig.tar.gz

As I stated above, I really have no clue on a lot of this. I was simply following the instructions step by step and got stuck. I appreciate any and all feedback/help

Thanks
[/QUOTE]I am also a beginner, but I've spent probably 20 or so hours in the last few days installing and configuring both Samba and Netatalk.  Anyone who has used both can confidently say that Netatalk is infinitely faster, and I find it easier to get set up as well.

I used the kremalicious guide which you cite, ChazzR, and maybe I see your problem: here are the kremalicious instructions for this part:
> sudo apt-get build-dep netatalk
sudo apt-get install cracklib2-dev fakeroot libssl-dev
sudo apt-get source netatalk
cd netatalk-2*
[...]
sudo DEB_BUILD_OPTIONS=ssl dpkg-buildpackage -rfakeroot

the first line tells apt-get to "build the dependencies" for netatalk, which (as I understand it) means "identify what other packages netatalk needs in order to run (its 'dependencies'), and install the ones that aren't already installed."  you appear to have done this part successfully:
> root@StorageServer:/home/charlie/netatalk/netatalk# apt-get build-dep netatalk

the second line installs some packages that will be invoked in the dpkg-buildpackage command (I don't know if the instructions changed since you posted, ChazzR, but the current instructions differ from what you told the machine to do:
> sudo aptitude install devscripts dpkg-dev
maybe this command includes those packages, I don't know--but just run the other command to be sure, since nothing will be installed unless you don't already have it.

but after this is where you run into trouble:[quote=ChazzR]root@StorageServer:/home/charlie/netatalk/netatalk# DEB_BUILD_OPTIONS=ssl debuild -i -us -uc -b
debuild: fatal error at line 630:
cannot find readable debian/changelog anywhere!
Are you in the source code tree?
root@StorageServer:/home/charlie/netatalk/netatalk# cd netatalk
bash: cd: netatalk: No such file or directory
root@StorageServer:/home/charlie/netatalk/neta[/quote]  the instructions say:> cd netatalk-2*which means "in the current (working) directory, look for a directory that begins with "netatalk-2"(plus zero or more characters in the dirname afterward--the asterisk is a "wildcard", and not taken literally) and put me there...
but you say> root@StorageServer:/home/charlie/netatalk/netatalk# cd netatalkwhich bash takes to mean "go to the directory named (exactly literally) "netatalk" in the current directory", and bash is saying "I can't there isn't one" > bash: cd: netatalk: No such file or directory (note though, you are in *a* directory called netatalk)  the reason you're going into a different directory in the first place is to be in the same directory as the source when you run the dpkg command, because it's going to look for source files and directories in the current directory when you run it.  so if you still have those netatalk files inside of /home/charlie/netatalk/netatalk, go there, then go one folder further, into /home/charlie/netatalk/netatalk/netatalk-2.0.4~beta2 and that directory should probably contain the source files.

I hope that helps.  it's worth it!  AFP is SOOOO MUCH faster and nicer to use than Samba if you're lucky enough to have be sharing to a Mac.

cheers!

---

### Post by timhees on 2010-05-02
Thanks, I will try this

---

### Post by ChazzR on 2010-06-06
Ok so a long delay on this project, but I've finally carved out some time to finish what I started. I decided to go with Samba. After updating to Lucid and removing all the old Samba and Netatalk files I started over from scratch and followed the guide above (for Samba). 

As I walked through the steps everything seemed to be working. I was able to configure and mount both of my media drives to the Lucid desktop. Once all these steps were completed I turned to my primary mac to try and access the lucid box. 

I went to Finder and followed the steps exactly. Entered smb://StorageServer.local and then clicked connect. Once it started it prompted me to enter as a guest or registered user. I selected registered user and then entered my username and password. 

Once I entered in this info I get this response: There was an error connecting to the server “StorageServer.local”. Check the server name or IP address, and then try again. If you are unable to resolve the problem contact your system administrator.

I can however go to vnc://StorageServer.local and remote into the machine without issue. 

Any idea as to why I can vnc in but not smb? Any help would be appreciated. 

Thanks.

---


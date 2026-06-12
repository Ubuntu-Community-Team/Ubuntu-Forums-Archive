---
title: "Setting up freenx on Ubuntu as server and client on Windows"
date: 2010-01-14
forum: General Help
---

### Post by meharts on 2010-01-14
Hi guys and girls!

I have been messing around with freenx to see if I can support my customer via remote desktop...

I have installed the server on Ubuntu Karmic and the client on Windows 7. I love linux but need the windows computer for customer work and that is why I chose to install the client on windows.

I setup the server the best I could and created custom keys which I then copied to windows and imported them to the freenx client.

I am looking for security for my customer and that is why I chose custom keys...

There are several issues to deal with but I want to just get started to see where it takes me.

I added the test server computers ip address to the freenx client configuration and tried to connect to Ubuntu... I have left the port as 22 at the moment

Desktop setting on the client...I chose vnc which seems to be a good choice according to all the material I have been reading....Other settings I have left alone at the moment to see how things work....

All that said - I have the login window asking for information... I have the password asking for information....and I have the session wanting information....?

Obviously I understand that login info can be set on the server and the password...but I haven't seen how to set up that?

Is there anyone who can spare me sometime to go through all the general stuff on this....

Of course I am testing the server from a client on my home network at the moment - but the customer has his own router as do I so those settings will need to be looked at as well.

I use logmein in usual windows related remote desktop and that hasn't let me down yet ....just never done it from windows to linux before and need some help..

Sorry, for waffling on...my age....LOL

meharts

---

### Post by pricetech on 2010-01-14
I can't help you with freenx, but I can make another recommendation;

nomachine.com.  Get the NX Client for winders and the Client, Node, Server for Linux.

Works for me and a piece of cake to set up.

---

### Post by meharts on 2010-01-14
Hi pricetech:)

Thanks for dropping in... I have looked at the link you gave me and it looks interesting but not sure which one I should down load...

They have an nx free edition for Linux which should work with karmic koala...?

meharts

---

### Post by meharts on 2010-01-14
Hi again......

Sorry, been a long day...I saw that all three packages were available, so I installed them ...but the server came with install fault

Can you take a gander and see what you think

meharts

---

### Post by meharts on 2010-01-15
Hi again

Has no one had this problem? I followed the readme from no machine if it doesn't install.....i.e. remove all packages and start again. 
Tried that a couple of times now and nothing gives?!

OK! Perhaps this isn't that easy to install....

meharts

---

### Post by meharts on 2010-01-15
Hi again

Well, just tried the advice given [here]("http://ubuntuforums.org/showthread.php?t=784880") by sperlyjinx but that doesn't seen to work on Karmic Koala...

meharts

---

### Post by pricetech on 2010-01-15
Never had that, or any problem installing NX, so it's new to me.  The error seems to indicate that, for whatever reason, the user NX is already there and NX doesn't like it being there in advance of its installation.

Try removing freenx, along with the NX stuff, then install NX Client, Node, Server, in that order.

You may have to manually delete the NX user.

---

### Post by meharts on 2010-01-19
Hi again:)

Sorry, been busy of late...thanks for getting back to me pricetech....will remove everything and will try to remember....purge command......senile....LOL

Will get back to you on this as soon as I can!

Thanks!

meharts

---

### Post by meharts on 2010-01-19
Hi again!

I removed and purged the files with freenx...then made sure I did the same with nx, but I get exactly the same error on installing the server....and I don't know where else to look for files to remove a user that doesn't exist?!!

Is there any light at the end of the tunnel with this or should I just give up?

meharts

---

### Post by meharts on 2010-01-19
Hi again!

It would seem that the server is in fact installing even though I am getting error....

Assuming that everything is installed how do we connect from windows to Ubuntu?

meharts

---

### Post by meharts on 2010-01-19
Hi again!

Don't worry about replying to this thread.....give up with nx.....got better things to do with my time!!

I will find something that works...I can set up logmein in about ten minutes...why does linux always have to take six months....

meharts

---

### Post by pricetech on 2010-01-19
I hate to see you give up.  The client for winders just works for me.  Point it to the IP of your Linux box and it should connect just fine.  You will have to forward port 22 (default) on the routers you need to pass through in order to use it over the Internet.

---

### Post by meharts on 2010-01-19
Hi again!

Sorry, don't usually give up just a little stressed at the mo....
will give your info a try and let you know...

meharts

---

### Post by meharts on 2010-01-20
Hi again:(

Nope...couldn't get that to work...but I used the system - settings - remote desktop built into Ubuntu and set it up with password etc...

I then downloaded tightvnc viewer and entered the details of the computer I wanted to login to....

I was prompted for the password I had setup on Ubuntu and then I clicked on connect....

OK! this is on my home network and I know I must set up routers etc when outside of my network...

anyway, I got access to Ubuntu from windows....good screen resolution etc.. I could see I could open menus etc on ubuntu but nothing showed on my windows computer?

Any ideas?

meharts

---

### Post by pricetech on 2010-01-21
I can't help you with VNC since I don't use it that way.  Security is a big issue with VNC so you should tunnel it through SSH to secure it.  A search should find you one or more good tutorials on the subject.

Let me do some more research and see if I can find out why your NX isn't working.

---

### Post by pricetech on 2010-01-21
> **meharts said:**
> I don't know where else to look for files to remove a user that doesn't exist?!!

The nx user is listed in /etc/passwd.  You need to use sudo to edit it.

I found it with the help of a friend who is much more knowledgeable than I and is generous enough with his knowledge to pass it along.

---

### Post by meharts on 2010-01-22
Hi Pricetech:D

I have tested so many things and there are so many files roaming around...going to do a reinstall for my customer. Although he is Swedish - he would like the English version because most help files are in English ....makes it easier..

I will let you know when I have reinstalled and got openfoam working and then we can concentrate on nx....

I do thank you for your reply!

meharts

---

### Post by pricetech on 2010-01-22
No problem.  Glad to help in any way I can.

---

### Post by meharts on 2010-01-25
Hi pricetech:)

OK! Now I am back to square one or two...LOL

I am adding this info to develop the thread for others looking in and would like more up to date info as being supplied here....

OK! nuff said. I reinstalled Ubunutu Karmic Koala 64 bit. I updated everything that came up and then rebooted as requested.

I then downloaded as discussed previously [EMAIL="http://www.nomachine.com/download-package.php?Prod_Id=1349"]NoMachine[/EMAIL] for Linux.

I have installed in the order as stated before....client,node and server.

Each install of the above gave out its own error/what you need to do..

For the client install:

```


ruben@ruben-desktop:~/Downloads$ sudo dpkg -i nxclient_3.4.0-5_x86_64.deb 
Selecting previously deselected package nxclient.
(Reading database ... 147517 files and directories currently installed.)
Unpacking nxclient (from nxclient_3.4.0-5_x86_64.deb) ...
Setting up nxclient (3.4.0-5) ...
Showing file: /usr/NX/share/documents/client/cups-info

 CUPS Printing Backend

 The NX Client set-up procedure detected that your "IPP CUPS" printing
 backend doesn't allow printing from the NX session. In order to have
 printing support in your NX system, you need to set proper permissions
 on the IPP backend. Please execute:

   chmod 755 /usr/lib/cups/backend/ipp



```]


After the node install:

```


ruben@ruben-desktop:~/Downloads$ sudo dpkg -i nxnode_3.4.0-6_x86_64.deb
Selecting previously deselected package nxnode.
(Reading database ... 147731 files and directories currently installed.)
Unpacking nxnode (from nxnode_3.4.0-6_x86_64.deb) ...
Setting up nxnode (3.4.0-6) ...
NX> 700 Starting: install node operation at: Mon Jan 25 08:11:50 2010.
NX> 700 Autodetected system 'debian'.
NX> 700 Install log is '/usr/NX/var/log/install'.
NX> 700 Creating configuration in /usr/NX/etc/node.cfg.
NX> 700 Inspecting local CUPS environment.
NX> 700 Generating CUPS entries in: /usr/NX/etc/node.cfg.
NX> 700 WARNING: Cannot find file: printers.conf.
NX> 700 WARNING: Please verify your CUPS configuration.
NX> 700 Installation of NX node was completed with warnings..
NX> 700 Please review the install log '/usr/NX/var/log/install'.
NX> 700 for further details..
NX> 700 Showing file: /usr/NX/share/documents/node/cups-info

 CUPS Printing Backend

 The NX Node setup procedure could not detect your "CUPS"
 installation: either CUPS  is not installed on your system
 or it was installed in a non-standard path. CUPS is needed
 in order to enable printing support in your NX system.
 Please note that you can enable  printing support for your
 NX system at any time; to do this make sure  that you have
 CUPS installed then run:

   /usr/NX/scripts/setup/nxnode --nxprintsetup <pathname>

 to specify the location of the CUPS root path. 
NX> 700 Bye.


```


And finally after the server install:


```


ruben@ruben-desktop:~/Downloads$ sudo dpkg -i nxserver_3.4.0-8_x86_64.deb
Selecting previously deselected package nxserver.
(Reading database ... 147912 files and directories currently installed.)
Unpacking nxserver (from nxserver_3.4.0-8_x86_64.deb) ...
Setting up nxserver (3.4.0-8) ...
NX> 700 Installing: server at: Mon Jan 25 08:13:18 2010.
NX> 700 Autodetected system: debian.
NX> 700 Install log is: /usr/NX/var/log/install.
NX> 700 Creating configuration file: /usr/NX/etc/server.cfg.
NX> 723 Cannot start NX statistics:
NX> 709 NX statistics are disabled for this server.
NX> 700 WARNING: Error when trying to connect to NX server. Error is:
NX> 700 WARNING: ssh: connect to host 127.0.0.1 port 22: Connection refused
NX> 700 WARNING: NX has been configured to use the SSH server on default port
NX> 700 WARNING: 22 but no SSH daemon is listening on this port. When the
NX> 700 WARNING: installation completes, please ensure that SSHD is installed
NX> 700 WARNING: and is up and running. If you want to contact SSHD daemon on
NX> 700 WARNING: a port different from 22, you need to configure NX Server and
NX> 700 WARNING: Node accordingly. More information is available on the NoMachine
NX> 700 WARNING: Knowledge Base at: http://www.nomachine.com/kb/index.php
NX> 700 Installation of NX server was completed with warnings.
NX> 700 Please review the install log '/usr/NX/var/log/install'
NX> 700 for further details.
NX> 700 Showing file: /usr/NX/share/documents/server/install-notices

Server keys

The initial login between client and server happens through a DSA key 
pair, i.e. a couple of specially generated cryptographic keys, called 
the private key and the public key, which allow you to establish a 
secure connection, by means of SSL encryption, between NX client and 
NX server. 

The public part of the key-pair is provided during the installation 
of the server, while the private part of the key-pair is distributed 
together with the NX Client. This ensures that each NX client is able 
to authenticate to the server and to start the procedure for autho-
rizing the user and negotiating the session. 

If you want to create a virtual private network (VPN) instead, you 
need to generate a new DSA key-pair and distribute the private part 
of the key-pair to those NX clients you want authenticated to the NX 
server. More information on how to generate and distribute a new DSA 
key-pair is available at:  

http://www.nomachine.com/ar/view.php?ar_id=AR01C00126

Creating Users

NX is configured to allow access from any system user, as long as 
valid credentials are given to the user for the SSH login. NX pro-
vides an alternative authorization method, allowing system admin-
istrators to determine which users are given access to the NX fun-
ctionalities. This works by implementing a separation between the 
system password and the NX password, so that, for example, it is 
possible to forbid remote access to the system by any other means 
except via NX and use the NX tools to implement effective accounting 
of the system resources used by the user, or to share NX passwords in 
an external database.

To activate the NX user and password DBs, you will have to edit the
NX server configuration file by hand or use the NX Server Manager 
Web tool available for download on the NoMachine Web site at:

http://www.nomachine.com/download-manager.php

Session Shadowing and Desktop Sharing

The session shadowing functionality allows you to share NX sessions 
running on the node. The desktop sharing functionality instead, gives 
access to the native display of the X server as if you were in front 
of the monitor. By default you can access sessions in interactive mode 
and upon authorization of the session owner. You can modify this beha-
viour by tuning the server configuration according to your needs, for 
example by allowing access to sessions in view-only mode, or connecting
to either a suspended session or the local display via the Desktop 
Manager login window.

Load Balancing

NX Advanced Server provides support for multi-node capabilities and 
load balancing. In its current implementation, NX server can only 
manage accounts on the host machine, so to grant access to the node 
running remotely, you will need to create the user account directly 
on the remote node host by issuing the NX node commands as root user.
You will also need to add the NX Server public DSA Key to the node to 
allow this server to connect to the node running on the remote host. 

Documentation

For further information on how to manage the configuration of your 
NX system, please refer to the System Administrator's Guide available 
on the NoMachine Web site at:

http://www.nomachine.com/documentation/admin-guide.php

The NoMachine Team.


NX> 700 Bye.


```

OK! Sorry, for all the code....doing this for myself and my customer who is very interested in Linux. 

I hope he isn't to peeved at me for giving away his name in the code....LOL.

Can we address each install in turn so that we get as detailed info as possible for further installs;)

I would be grateful for all the help we can get on this matter.


meharts

---

### Post by meharts on 2010-01-25
Hi again!

OK! I am putting a lot of info here to try and make this idiot proof....because I am an idiot.....in case you were wondering...LOL

OK! Downloaded the client for windows and installed it. I am on my home network at the moment, so not thinking about getting passed routers at the moment....

nomachine client has its stages for configuration and I did as follows:

For session:

I called my session after my customer Ruben.....now I have really let the cat out of the bag.....sorry Ruben!
For my host settings i chose the local ip address being provided by running # sudo ifconfig
I also chose LAN for my internet connection....being on my network.
I left it on port 22

For my desktop:

You can choose unix,windows,vnc, and shadow for your desktop environment. I chose "Unix" and Gnome. pricetech mentioned about security with vnc, so I thought I would try other avenues first!
For display I chose Fullscreen.....might as well have the full Monty.

Nuff said. I tried to connect. The first thing I am prompted for is password. I hadn't set up any password, so for this attempt I chose login as guest and "Login"

The process seemed to work for a few moments and then I got a "can't initialise the display service" .

Now this didn't happen before but needs to be looked at....the graphics card in this computer is a Zotac GTX260 Amp2 896MB DDR3.

Just wondering if anyone can shed some light on that for me?

I will, of course, be checking out settings etc myself but would appreciate some help.

meharts

---

### Post by pricetech on 2010-01-25
The username and password should be an account that is on the Linux box you are connecting to.  Any account should work.  You'll probably have an account of your own on the machine for remote support anyway, so I'd just use that one.

I've never had the display error, but I don't use full screen.  Maybe that's it ??

While LAN should work, the documentation suggested just leaving it at ADSL (the default) which has always worked for me.  I'm not suggesting that as a cause, just mentioning it.

Unix, Gnome should work as long as the Gnome window manager is installed, which it will be with Ubuntu.  That's the only prerequisite there is that the chosen window manager actually exist.

Also, the first time you log in to the machine, you'll be asked to accept the key for the host.  Since you know it's valid, go ahead and accept it.

One other note;  I tried "shadow" with mine and I was able to control the Linux box, but not able to see the changes reflected back to my client on the winders box.  (the two I tested with are side by side)  I didn't pursue it though, so I don't have an answer for why it was that way.

---

### Post by meharts on 2010-01-25
Hi pricetech:)

Thanks for the update! Getting a bit late here....been a long day. Will, have a look tomorrow.....Tuesday my time here in Sweden!

Thanks again!

meharts

---

### Post by meharts on 2010-01-26
Hi pricetech:)

OK! tried to connect now and I get the following:

> 

NX> 203 NXSSH running with pid: 5460
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
ssh: connect to host 85.230.149.58 port 22: Connection refused



OK I have put his computer outside my router, so I have some settings to deal with....just wondered if you have seen this before?

meharts

---

### Post by meharts on 2010-01-26
Hi again;)

Ok the first thing was the ssh....not installed....LOL

Next...when I tried to connect I had to accept the key as you pointed out but the connection was refused for me:

Authentication failed for user......
Ok I have added password to remote desktop settings on Ubuntu and the is OK...just need to include my name as a user trying to login to my customer's computer.....

meharts

---

### Post by meharts on 2010-01-26
Hi again!

Sorry, putting up this info ...as much for me as others in the same boat...

OK after installing ssh I tried to reconnect and got this info:



> 

NX> 203 NXSSH running with pid: 5052
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 85.230.149.58 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.4.0-8 - LFE
NX> 105 Hello NXCLIENT - Version 3.4.0
NX> 134 Accepted protocol: 3.4.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: NX guest user
NX> 553 Login as guest disabled on this server.
NX> 553 Support for guest users is not allowed on this server.
NX> 553 Please check the terms and conditions of your subscription.
NX> 999 Bye.
NX> 280 Exiting on signal: 15




Seems to me I need to go in and configure nx so that I can get access.

meharts

---

### Post by meharts on 2010-01-27
Hi again!

Well, I have tried to login as guest and user but no dice. As guest I commented out the GuestName = "guest".....nada

I have tried to find where I can add my name as user to my customers computer, so that it recognises me when I try to login......nada

I think after all this I will just call it a Dodo.....

Thanks for all your help but I give up!

meharts

---

### Post by meharts on 2010-01-27
Hi again...

Stubbornness is getting the better of me...

I found a add user post:

```


$ sudo nxserver --adduser <xxxxxxx>



```

no nxserver command found....

God! Is there anything that works?

meharts

---

### Post by meharts on 2010-01-27
Hi again...

Like I said I am stubborn idiot......or something like that...LOL

OK I have tried to use the web based nx server manager to see if that would help me get going....nada.

Followed many threads and did the following:

Installed apache2 and then added the following to httpd.conf

```


# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

#Use for nxserver manager
Include /usr/NX/etc/manager.conf


```

OK! That done I checked my manager.conf:

```


Alias /nxmanager/ "/usr/NX/share/htdocs/nxmanager/"

ScriptAlias "/nx/nxmanager" "/usr/NX/bin/nxmanager"

<Directory "/usr/NX/">
    AllowOverride None
    Options None
    Order allow,deny
### ADDRESS RESTRICTIONS START ###
    Allow from all
### ADDRESS RESTRICTIONS STOP  ###
</Directory>	


```

I then checked the manager.cfg file to see how that looked:


```


#/**************************************************************************/
#/*                                                                        */
#/* Copyright (c) 2001, 2009 NoMachine, http://www.nomachine.com/.         */
#/*                                                                        */
#/* NXMANAGER, NX protocol compression and NX extensions to this software  */
#/* are copyright of NoMachine. Redistribution and use of the present      */
#/* software is allowed according to terms specified in the file LICENSE   */
#/* which comes in the source distribution.                                */
#/*                                                                        */
#/* Check http://www.nomachine.com/licensing.html for applicability.       */
#/*                                                                        */
#/* NX and NoMachine are trademarks of Medialogic S.p.A.                   */
#/*                                                                        */
#/* All rights reserved.                                                   */
#/*                                                                        */
#/**************************************************************************/

#
# Set config file format version.
#
ConfigFileVersion = "2.0"

#
# Set the log level of NX Server Manager. NX Server Manager logs to
# the syslog all the events that are <= to the level specified below.
# Level can be ERROR | WARNING | INFO | DEBUG
#
SessionLogLevel = "INFO"

#
# Specify user name of Apache owner.
# 
ApacheUname = "nobody"

#
# Specify group name of Apache owner.
# 
ApacheGname = "nogroup"

#
# Specify the Apache reload command.
#
ApacheHTTPDReloadCommand = "/etc/init.d/apache2 graceful"

#
# Specify the location of the NX Server Manager configuration file to 
# be included in the Apache configuration file.
#
NXManagerConfPath = "/usr/NX/etc/manager.conf"

#
# Specify the directory on the filesystem where the statistics images
# have to be placed.
# 
StatPathTempFs = "/usr/NX/share/htdocs/nxmanager/images/stats/tmp"

#
# Specify the URL where the NX Server Manager has to look for the
# statistics images. This path needs to correspond to the path set in 
# the Alias and ScriptAlias directives specified in the manager.conf
# file.
# 
StatPathTempWeb = "/nxmanager/images/stats/tmp"

#
# Specify the location of the nxssh binary.
#
NXSSHPathBinary = "/usr/NX/bin/nxssh"

#
# Specify the location and file name of the DSA key.
#
NXSSHPathIdentity = "/usr/NX/share/keys/server.id_dsa.key"

#
# Specify the location of the NX libraries required by nxssh.
#
NXSSHPathLib = "/usr/NX/lib"

#
# Specify the absolute path and name of the NX Server Manager DB.
#
NXManagerPathDB = "/usr/NX/var/db/manager/nxmanager_conf.db"

#
# Specify the absolute path for the NX Server Manager templates used 
# to visualize NX server data.
#
TemplatePath = "/usr/NX/share/htdocs/nxmanager/templates"  

#
# Specify the number of items to be visualized in the templates.
#
TemplateItemsPerPage = "10"



```

Couldn't see anything to worry about there so I updated:

```


$ sudo /usr/NX/scripts/setup/nxmanager --update


```

And then I tried to connect to the web based server: [http://localhost/nx/nxmanager/](http://localhost/nx/nxmanager/)

BUT!!! I got the following error:

```


Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.2.12 (Ubuntu) Server at localhost Port 80




```


Am I just destined to remain an idiot? Why is this giving me faults and is there any info that is up to date that actually works?

meharts

---

### Post by pricetech on 2010-01-27
I've been out of pocket for a few days, so I'm a little late checking the post.

You'll need to make sure you have an account on the Linux box you are attempting to administer.  NX will automagically pick up the user once it's added to the machine.

You can use the GUI to add yourself.  NX should authenticate you then.

---

### Post by meharts on 2010-01-28
Hi again....

If it could be so simple......nada! I created an account for me as administrator on my customers Ubuntu and then tried to connect....

It doesnt matter what I do now it comes up with the following error from the client on windows:

> 

The NX service is not available or the NX access was disabled on host.....



I haven't disabled anything!!

I ran the following on ubuntu


```


ruben@ruben-desktop:~$ sudo /usr/NX/bin/nxserver --status 
NX> 900 Connecting to server ...
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.
ruben@ruben-desktop:~$ 


```



After trying to start the server:

```


ruben@ruben-desktop:~$ sudo /usr/NX/bin/nxserver --start
NX> 500 Service already running.
NX> 999 Bye.


```


???????? I tried to find out the status again:


```


ruben@ruben-desktop:~$ sudo /usr/NX/bin/nxserver --status 
NX> 900 Connecting to server ...
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.


```

OK! Can someone tell me how a service can be running and not running at the same time:)

I really am losing it here....

meharts

---

### Post by pricetech on 2010-01-28
Can you connect to the server via SSH ??  NX runs on SSH, so it has to work for NX to work.

---

### Post by meharts on 2010-01-29
Hi again:)

OK! As user martyn...me..LOL I can get in with ssh...but the same problem is causing me error with "nomachine" client on windows?

---

### Post by meharts on 2010-01-29
Hi again..

Sorry, should have said that with nomachine it is a no go...but I could via ssh by using winscp on windows.

meharts

---

### Post by meharts on 2010-01-29
Hi again...
Just tested putty and that let me login as martyn aswell but not ruben?

meharts

---

### Post by meharts on 2010-01-29
Hi again:D

Now we are getting somewhere!!! OK Steve1961 in this [thread]("http://ubuntuforums.org/showthread.php?t=941530") gave me the answer....I had looked at the dsa key before and then put it to the back of my mind.....long way back....LOL

OK! he used the following to generate new keys:

```


sudo su
/usr/NX/scripts/setup/nxserver --keygen
chown nx:root /usr/NX/home/nx/.ssh/authorized_keys2
chmod 0644 /usr/NX/home/nx/.ssh/authorized_keys2
chown nx:root /usr/NX/home/nx/.ssh/default.id_dsa.pub
chmod 0644 /usr/NX/home/nx/.ssh/default.id_dsa.pub


```

I generated the keys and then made a copy via my usb and transferred that to my windows machine...and imported it to "nomachine"

I then checked both me and ruben to see if I could take login to his desktop.....YES!!

OK! to the next bit.....I can work on his computer making changes etc....but I can see what I am doing on his desktop screen....sorry, on windows I can see menu lists and work as if I am sitting infront of his computer....

But I can't see anything on his computer screen. He has control and can affect changes which is well and good in situations of me showing him stuff.....but why can't I see what is happening on his screen?

Pricetech
I wouldn't mind your input on this...if you haven't abandoned me....LOL...

meharts

---

### Post by pricetech on 2010-02-01
I haven't abandoned you, just been tied up the last few days.

The "herd of winders boxen" I tend is due for updates, so that's where I've been.

When you log in via SSH, ans subsequently NX, you get a unique session, even if you log in as him and he's already logged in.

You'll have to use Shadow to be able to watch him / show him stuff.

I tried Shadow on my winders box and while I could connect and see the desktop, and even control it, the changes weren't reflected to my client on winders.  (the two boxen I was using to test with are side by side)

I haven't had a chance to look into it and probably won't get a chance for several more days.

You might check the documentation from nomchine and see if there's anything in the FAQ about the problem, or maybe even start another thread about it specifically.

Good luck with it and sorry I won't be much help for a while.

---

### Post by sailorxyz on 2010-02-01
Hi,

The below is how I configure NoMachine. It has always worked for me to date. What I still need to figure out is the printing to a local printer via NoMachine. That I have not got working yet. Also check with the NoMachine website for the latest downloads.

******************************    Install NoMachine    *********************************
 -----------------------
    Step 1 - Download
    -----------------------

mkdir /usr/src/NoMachine
scp -r pjt@192.168.1.222:/home/pjt/NoMachine /home/brent/NoMachine

    OR

    Download "NX Client DEB for Linux" from:
    wget [http://64.34.161.181/download/3.4.0/Linux/nxclient_3.4.0-5_x86_64.deb](http://64.34.161.181/download/3.4.0/Linux/nxclient_3.4.0-5_x86_64.deb)


    Download "NX Node DEB for Linux" from:
    wget [http://64.34.161.181/download/3.4.0/Linux/nxnode_3.4.0-6_x86_64.deb](http://64.34.161.181/download/3.4.0/Linux/nxnode_3.4.0-6_x86_64.deb)

    Download "NX Desktop Server DEB for Linux" from:
    wget [http://64.34.161.181/download/3.4.0/Linux/FE/nxserver_3.4.0-8_x86_64.deb](http://64.34.161.181/download/3.4.0/Linux/FE/nxserver_3.4.0-8_x86_64.deb)




    -----------------------
    Step 2 - Install
    -----------------------

    Install the DEB files in this order:

    nxclient - sudo dpkg -i nxclient_3.4.0-5_x86_64.deb
    chmod 755 /usr/lib/cups/backend/ipp
    nxnode   - sudo dpkg -i nxnode_3.4.0-6_x86_64.deb
    /usr/NX/scripts/setup/nxnode --nxprintsetup <pathname to CUPS> to enable remote printing (CUPS must be installed)
    nxserver - sudo dpkg -i nxserver_3.4.0-8_x86_64.deb

    To be able to use VNC:

    sudo aptitude install xvnc4viewer vnc4-common

    -----------------------
    Step 3 - Configure
    -----------------------

sudo nano /etc/ssh/sshd_config

    Add the following line & save the file
    AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

sudo /etc/init.d/ssh restart
sudo /usr/NX/bin/nxserver --status

---

### Post by fish-hawk on 2010-02-04
You may have to add the "nx" user to the SSHD config file as well. It took me three months of tinkering to finally get NX working, and that was the key piece for me. 

NX is much much faster than the VNC via Putty tunnel I was using before.

My sshd_config file was located in /etc/ssh directory. Running Ubuntu Karmic

---

### Post by linux-beginner on 2010-02-08
Hello,
I do not have "/usr/NX/etc/server.cfg" on my ubuntu 9.10. Actually I do not have directory /user/NX.
Any ideas?

---

### Post by pungki on 2010-03-16
I want to setup Ubuntu 8.04 as Nomachine server. I will have 5 simultaneous connections to the server using nxclient. Does anyone know how much GPU RAM that I need? I've searched in Nomachine website, but no luck. My thought, virtual desktop will use much of GPU RAM.

Thanks in advance.

---


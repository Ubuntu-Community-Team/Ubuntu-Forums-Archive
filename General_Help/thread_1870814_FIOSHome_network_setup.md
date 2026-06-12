---
title: "FIOS/Home network setup"
date: 2011-10-27
forum: General Help
---

### Post by kcpilotguy on 2011-10-27
Hi,

So I recently acquired an old computer which I put in a second harddrive and I am wanting to use it as a storage server that I can access from within my home and eventually from the internet.  This is what I have figured out so far:

Installed Ubuntu Server 10.4
Installed harddrive and got it mounted
Set static IP on my FIOS router as 192.168.1.6 for the linux server
Installed SAMBA


Problems I am having:

Have no clue what to do from here...
I can't see my server from my windows machine, but when I type in the static IP address on my windows machine, it gives me the default SAMBA webpage saying it is working.

I set up a "homegroup" on the @#%$# windows machine and set the same homegroup name on the SAMBA server, not sure what this accomplishes, if anything.  I still can not see the linux server on the network page on windows.

How do i browse the server?
How do i set it up so i can drop files on the 1.5TB HD i installed?

I can NOT find a step by step guide to anything that uses recent versions of SAMBA/Ubuntu...

If anyone can please point me in the correct direction it would be much appreciated because at this point the linux server is about to suffer the "office space" fate.
PLEASE HELP!

---

### Post by Derek Karpinski on 2011-10-28
Are you sharing any folders?  You have to set up folders to share. Two ways to do things:

1. In nautilus (the file manager), right click on the folder you wish to share, and click on 'sharing options', and fill in the blanks/check boxes.

2. Install 'system-config-samba' found in the software center.  It makes setting up shared folders and samba passwords fairly easy via GUI.

---

### Post by kcpilotguy on 2011-10-28
> **Derek Karpinski said:**
> Are you sharing any folders?  You have to set up folders to share. Two ways to do things:

1. In nautilus (the file manager), right click on the folder you wish to share, and click on 'sharing options', and fill in the blanks/check boxes.

2. Install 'system-config-samba' found in the software center.  It makes setting up shared folders and samba passwords fairly easy via GUI.

So I have done both of those things and still can't see the sever on the network or my computers from the server.  I think its the FIOS router that is the culprit, but not sure.  And I have gadmin-samba, which i think does the same thing.  

Any other insights?

---

### Post by SeijiSensei on 2011-10-28
Take a look at [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2583597](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2583597).  Oftentimes making the Samba box a "WINS server" solves the browsing problem.

[This document](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch10_:_Windows,_Linux,_and_Samba) might be an easier read.  Take a look at the section entitled "Creating a Starter Configuration."

---

### Post by capscrew on 2011-10-28
> **kcpilotguy said:**
> So I have done both of those things and still can't see the sever on the network or my computers from the server.  I think its the FIOS router that is the culprit, but not sure.  And I have gadmin-samba, which i think does the same thing.  
Any other insights?

Almost all of these "helper programs" are idiosyncratic.  In particular gadmin-samba.  In the end they will not work together happily.

FWIW - I find [**_[COLOR="Blue"]this description[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=1590") to be the simplest method.  It uses nothing but the basic Samba server install.  

At this point you may have to un-install most of these helper programs to be successful in the end.

---

### Post by capscrew on 2011-10-28
> **SeijiSensei said:**
> Take a look at [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2583597](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2583597).  Oftentimes making the Samba box a "WINS server" solves the browsing problem.

it might be helpfull to take the reference to WINS in context.  The section you are referring to is on ADVANCED configuration.  More appropriate to the thread might be this statement from the basic Samba docs available [here]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html") ```

wins support (G)

    This boolean controls if the nmbd(8) process in Samba will act 
as a WINS server. [B][I][COLOR="Blue"]You should not set this to yes
unless you have a multi-subnetted network and you wish a particular 
nmbd to be your WINS server.[/COLOR][/I][/B] Note that you should NEVER 
set this to yes on more than one machine in your network.

    Default: wins support = no 

 
```

---

### Post by kcpilotguy on 2011-10-28
> **capscrew said:**
> Almost all of these "helper programs" are idiosyncratic.  In particular gadmin-samba.  In the end they will not work together happily.

FWIW - I find [**_[COLOR="Blue"]this description[/COLOR]_**]("http://www.jonathanmoeller.com/screed/?p=1590") to be the simplest method.  It uses nothing but the basic Samba server install.  

At this point you may have to un-install most of these helper programs to be successful in the end.

Thanks...let's see if I can do this and get it to work.  I agree that some of these helper programs may be screwing me up more than helping.  

GADMIN for example has GUI's in it that don't seem to work at all.

---

### Post by kcpilotguy on 2011-10-28
f-it, this crap still isn't working.  Switching to fedora and amahi server to get this done...thanks for the attempts, but something isn't right with samba and this f-ing router

---

### Post by capscrew on 2011-10-28
> **kcpilotguy said:**
> f-it, this crap still isn't working.  Switching to fedora and amahi server to get this done...thanks for the attempts, but something isn't right with samba and this f-ing router

Samba is Samba.  The distro doesn't really matter.  The tools on Fedora and Amahi are the same as on Ubuntu.  

Samba doesn't route anything so the problem isn't your router.  One thing I would recommend is; if you have a host based firewall that you turn it off until you have Samba installed.

---

### Post by kcpilotguy on 2011-10-29
> **capscrew said:**
> Samba is Samba.  The distro doesn't really matter.  The tools on Fedora and Amahi are the same as on Ubuntu.  

Samba doesn't route anything so the problem isn't your router.  One thing I would recommend is; if you have a host based firewall that you turn it off until you have Samba installed.

So I have set up everything and checked it about 5 times, and i have even reinstalled ubuntu 5 times to make sure it's clean and I haven't screwed up something.  

Anyway, the reason I keep going back to the router being the culprit is because I can't see anything on the stupid "my network" except my own laptop.  

I am almost 100% sure that if i switched over to a linksys that I would see all the computers on there.

Anyway, my fedora try came up empty also.  Can't get past the "select a driver" part on the install so its back to ubuntu and samba again.  

This is so frustrating...I just want to have someway to put stupid files on a backup server without having to pay amazon for cloud storage.  

Tomorrow i'll try the other router and setting up the file share in samba again with a clean install of ubuntu.  Not much else i can do

---

### Post by oldtimer7777 on 2011-10-29
What you really should do is buy a NAS External IDE/SATA Enclosure. Hook that directly to your router/switch, and you will have a true File Server that can be accessed by any OS. When I have a client that has different platforms running, and they want it to just work (always on - no hassle) I install a NAS File Server.  It is essentially just a external hard drive enclosure but instead of a USB connection, its hooked up via Ethernet directly to the back of your router switch.  You can find them pretty cheap on Ebay.  If you need streaming video you will need a Gigabit router and gigabit adapters for your systems too.

Search for [Network NAS External IDE Hard Drive Case]("http://www.ebay.com/itm/NetDisk-USB-Network-NAS-External-IDE-Hard-Drive-Case-/200604406717?pt=PCC_Drives_Storage_Internal&hash=item2eb4f453bd")

Your OS is free, the rest is hardware.


> **kcpilotguy said:**
> Hi,

So I recently acquired an old computer which I put in a second harddrive and I am wanting to use it as a storage server that I can access from within my home and eventually from the internet.  This is what I have figured out so far:

Installed Ubuntu Server 10.4
Installed harddrive and got it mounted
Set static IP on my FIOS router as 192.168.1.6 for the linux server
Installed SAMBA


Problems I am having:

Have no clue what to do from here...
I can't see my server from my windows machine, but when I type in the static IP address on my windows machine, it gives me the default SAMBA webpage saying it is working.

I set up a "homegroup" on the @#%$# windows machine and set the same homegroup name on the SAMBA server, not sure what this accomplishes, if anything.  I still can not see the linux server on the network page on windows.

How do i browse the server?
How do i set it up so i can drop files on the 1.5TB HD i installed?

I can NOT find a step by step guide to anything that uses recent versions of SAMBA/Ubuntu...

If anyone can please point me in the correct direction it would be much appreciated because at this point the linux server is about to suffer the "office space" fate.
PLEASE HELP!

---

### Post by kcpilotguy on 2011-10-29
> **oldtimer7777 said:**
> What you really should do is buy a NAS External IDE/SATA Enclosure. Hook that directly to your router/switch, and you will have a true File Server that can be accessed by any OS. When I have a client that has different platforms running, and they want it to just work (always on - no hassle) I install a NAS File Server.  It is essentially just a external hard drive enclosure but instead of a USB connection, its hooked up via Ethernet directly to the back of your router switch.  You can find them pretty cheap on Ebay.  If you need streaming video you will need a Gigabit router and gigabit adapters for your systems too.

Search for [Network NAS External IDE Hard Drive Case]("http://www.ebay.com/itm/NetDisk-USB-Network-NAS-External-IDE-Hard-Drive-Case-/200604406717?pt=PCC_Drives_Storage_Internal&hash=item2eb4f453bd")

Your OS is free, the rest is hardware.
That is probably the sane thing to do...to fry's i'll go tomorrow to figure out what type of NAS will fit the bill.

Thanks for the info.

---

### Post by capscrew on 2011-10-29
@kcpilotguy,

Let's go back to the beginning.  No need to spend any more $$$ for more hardware.  I have an old P3 1.0 GHz with 512 RAM and a 1TB HDD running off a SATA card via a PCI slot.  It has worked for me for the last 5 years a a NAS device.  

> 
So I recently acquired an old computer which I put in a second harddrive and I am wanting to use it as a storage server that I can access from within my home and eventually from the internet.  This is what I have figured out so far:

Installed Ubuntu Server 10.4
Installed harddrive and got it mounted
Set static IP on my FIOS router as 192.168.1.6 for the linux server
Installed SAMBA

What Samba packages did you install?  Did you install a GUI desktop on this host?

Post the output of the following terminal commands```

testparm -s

net usershare info --long

cat /etc/network/interfaces

cat /etc/hosts

Cat /etc/resolv.conf
```
> 

I can't see my server from my windows machine, but when I type in the static IP address on my windows machine, ***it gives me the default SAMBA webpage saying it is working***.
What did you mean by this?  Is it still the same?> 


I set up a "homegroup" on the @#%$# windows machine and set the same homegroup name on the SAMBA server, not sure what this accomplishes, if anything.  I still can not see the linux server on the network page on windows.
I'm assuming that you are referring to setting up a WORKGROUP here.  This just associates shares by a common group.  You can have as many WORKGROUPS as you like.> 

How do i browse the server?
...
Setting up Samba shares is only part of the deal.  Browsing Samba requires that you have functioning nameservice on the LAN.  This can be as simple as defining the hostname to IP address in the /etc/hosts file or as complex as running a DNS server on the LAN.  one other way is to explicitly declare a NETBIOS NAME for your Samba server.  

Ultimately Samba needs to ID the server by NETBIOS name.   It's pretty easy to configure this once you understand the process.  But first I need to see what you actually have setup at this point.   

> ...I have set up everything and checked it about 5 times, and i have even reinstalled ubuntu 5 times to make sure it's clean and I haven't screwed up something.
Let's see what you have done.  Post the info that I requested.> 
Anyway, the reason I keep going back to the router being the culprit is because I can't see anything on the stupid "my network" except my own laptop.
[QUOTE]I believe the router does not have a functioning LAN DNS setup.  That's okay.  We can setup the Samba server to operate just like the laptop does.[QUOTE]

I am almost 100% sure that if i switched over to a linksys that I would see all the computers on there.
I doubt it.> 
Anyway, my fedora try came up empty also. Can't get past the "select a driver" part on the install so its back to ubuntu and samba again.

This is so frustrating...I just want to have someway to put stupid files on a backup server without having to pay amazon for cloud storage.

Tomorrow i'll try the other router and setting up the file share in samba again with a clean install of ubuntu. Not much else i can do 
I think at this point you need to take a deep breath, calm down, and post the info requested.  Then we can advise you on what to do next.

Yes I am being vague about what to do.  Samba can be setup many ways.  This flexibility can be both a blessing and a curse.  The setup can be complex or very simple.  Understanding just what you have setup will help in advising you on what to do.

---

### Post by kcpilotguy on 2011-10-29
@capscrew

The setup is a Intel P4 w/ 768MB Ram, 2 NIC cards (motherboard and PCI slot), 2 hardrives (IDE 40GB which ubuntu 10.4 desktop installed & 1.5Tb via PCI SATA controller).

**Output of code:**

zserver@zserver:~$ **testparm -s**
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[test]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[COLOR="Red"][test]
	path = /media/zserver_sto/zlaptop
	valid users = zserver
	read only = No
	guest ok = Yes[/COLOR]
 Path in red is where i need my laptops to be able to see.  It is a file on the 1.5TB harddrive.

**Next Command**

[B]zserver@zserver:~$ net usershare info --long
[/B]
info_fn: file /var/lib/samba/usershares/farakh's backup is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/test is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/rebecca's backup is not a well formed usershare file.
info_fn: Error was Path is not a directory.

**Next Command**
[B]
zserver@zserver:~$ cat /etc/network/interfaces[/B]
auto lo
iface lo inet loopback


**Next Command**
[B]zserver@zserver:~$ cat /etc/hosts
[/B]
127.0.0.1	localhost
127.0.1.1	zserver

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

**Next Command**
[B]zserver@zserver:~$ cat /etc/resolv.conf
[/B]
# Generated by NetworkManager
domain home
search home
nameserver 192.168.1.1

**Your next question**

[B]Quote:

I can't see my server from my windows machine, but when I type in the static IP address on my windows machine, it gives me the default SAMBA webpage saying it is working.
What did you mean by this? Is it still the same?[/B]

I believe what happened here is on a previous install of Ubuntu, I had setup a LAMP server and I was getting the basic page by browsing to the IP address of the server.  This no longer applies or happens since I reinstalled 10.4 desktop edition.

[B]Quote:


I set up a "homegroup" on the @#%$# windows machine and set the same homegroup name on the SAMBA server, not sure what this accomplishes, if anything. I still can not see the linux server on the network page on windows.
I'm assuming that you are referring to setting up a WORKGROUP here. This just associates shares by a common group. You can have as many WORKGROUPS as you like.[/B]

In windows 7, there are these idiotic things called homegroups which are supposed to be simplified workgroups i believe.  

I got rid of this last night and I think was part of the problem of not being able to see the server.

I think I have provided all the info you requested.  I was very frustrated last night after having tried to get this to work for over a week and not getting anywhere.  Bit off a little more than i realized in this project.  

I really appreciate all the help you have provided thus far and hope you can understand what I have done enough to get me back to sanity.

Thanks again.

---

### Post by Derek Karpinski on 2011-10-29
Make sure your windows computer belongs to the right workgroup. Somewhere in control panel, you can rename your windows computer, and change it's workgroup name.  Change it to something simple like 'WORKGROUP'.

Try changing the line in /etc/samba/smb.conf:

```
sudo nano /etc/samba/smb.conf
```The find the section that talks about WINS support:

```

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
    wins support = yes
```And make sure that wins support is marked 'yes', and it is not commented out with a '#' or a ';'.

Find the section about workgroups:

```
# Change this to the workgroup/NT-domain name your Samba server will part of
    workgroup = WORKGROUP
```

Change it to match your windows workgroup. 

Ctrl-X to exit, save the file.

Then in terminal type:

```
sudo service smbd restart
```Then see if you can see your server.

---

### Post by capscrew on 2011-10-29
I have replied outside of your quotes, but I have annotated (like this [COLOR="Blue"]<--comment[/COLOR]) in the data output.

FYI -- If you put your data inside of ```
 blocks (the # tab above) it is easier to read.  :-)

> **kcpilotguy said:**
> @capscrew

The setup is a Intel P4 w/ 768MB Ram, 2 NIC cards (motherboard and PCI slot), 2 hardrives (IDE 40GB which ubuntu 10.4 desktop installed & 1.5Tb via PCI SATA controller).


**Output of code:**

[CODE]zserver@zserver:~$ **testparm -s**
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[test]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	[COLOR="Purple"]netbios name = zserver
        name resolve order = bcast hosts[/COLOR]
        map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[COLOR="Red"][test]
	path = /media/zserver_sto/zlaptop
	valid users = zserver
	read only = No
	guest ok = Yes[/COLOR]
```
Path in red is where i need my laptops to be able to see.  It is a file on the 1.5TB harddrive. [COLOR="Blue"]<-- do you mean a folder(directory)?  You share folders of files not individual files.[/COLOR]

**Next Command**

```
[B]zserver@zserver:~$ net usershare info --long
[/B]
info_fn: file /var/lib/samba/usershares/farakh's backup is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/test is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/rebecca's backup is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[COLOR="Blue"]<-- These were created via the GUI (right click etc)
We can delete them later. [/COLOR]

```
**Next Command**

```
zserver@zserver:~$ cat /etc/network/interfaces[/B]
auto lo
iface lo inet loopback
<-- It appears that the eth0 interface is managed by Network Manager. 

```

**Next Command**
```
[B]zserver@zserver:~$ cat /etc/hosts
[/B]
127.0.0.1	localhost
127.0.1.1	zserver

[COLOR="Blue"]<-- And here is where name services (DNS or hosts) 
fails you.  Samba can resolve your hostname to the NETBIOS NAME to the 
IP address of the NIC (eth0 of some such)[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
**Next Command**
```
[B]zserver@zserver:~$ cat /etc/resolv.conf
[/B]
# Generated by NetworkManager
domain home
search home
nameserver 192.168.1.1 [COLOR="Blue"]<-- Does this nameserver resolve LAN hostnames?[/COLOR]

```
**Your next question**

[B]Quote:
I can't see my server from my windows machine, but when I type in the static IP address on my windows machine, it gives me the default SAMBA webpage saying it is working.
What did you mean by this? Is it still the same?[/B]

I believe what happened here is on a previous install of Ubuntu, I had setup a LAMP server and I was getting the basic page by browsing to the IP address of the server.  This no longer applies or happens since I reinstalled 10.4 desktop edition.
That's what I thought, but needed to confirm> 

[B]Quote:

I set up a "homegroup" on the @#%$# windows machine and set the same homegroup name on the SAMBA server, not sure what this accomplishes, if anything. I still can not see the linux server on the network page on windows.

I'm assuming that you are referring to setting up a WORKGROUP here. This just associates shares by a common group. You can have as many WORKGROUPS as you like.[/B]

In windows 7, there are these idiotic things called homegroups which are supposed to be simplified workgroups i believe.  
They're not the same thing.> 
I got rid of this last night and I think was part of the problem of not being able to see the server.

I think I have provided all the info you requested.  I was very frustrated last night after having tried to get this to work for over a week and not getting anywhere.  Bit off a little more than i realized in this project. 

I really appreciate all the help you have provided thus far and hope you can understand what I have done enough to get me back to sanity.

Thanks again.

It looks the problem can be cured very simply.  I think you should add these lines to the [global] section /etc/samba/smb.conf file```
netbios name = zserver
name resolve order = bcast hosts
```

You will need to edit the file as root.  To do that you can use this command from the command line ```
gksudo gedit /etc/samba/smb.conf
```

See the lines in the [global] section above in [COLOR="Purple"]Purple[/COLOR]

---

### Post by kcpilotguy on 2011-10-30
@capscrew

Thanks for the guidance.  I have made all the changes you stated and this is where I am at now.  Here is what my smb.conf files now looks like:

```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = ZWORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

netbios name = zserver
name resolve order = bcast hosts

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[COLOR="SeaGreen"][test]
path = /home/zserver/test
available = yes
valid users = zserver
read only = no
browsable = yes
public = yes
writable = yes[/COLOR][COLOR="Blue"]<----This is the part that I can see on my windows 7 machine.  I got this bit from the simplified samba instructions posted earlier in the forum[/COLOR]

[COLOR="Magenta"]#[test]
#path = /media/zserver_sto/zlaptop
#available = yes
#valid users = zserver
#read only = no
#browsable = yes
#public = yes
#writable = yes[/COLOR] [COLOR="Blue"]<----This is the part I am trying to get to work and having issues.  The path is for my second harddrive which I have put in a screen shot[/COLOR]


```

I wanted to provide screen shots so you have an idea of where I am talking about in case it isn't clear from the verbiage.
If you look at the attachments, you can see a bit more.

Also, I was able to connect to my new printer over the network and can see it via the windows 7 laptop on the network so that is a win for today.

Thanks again.

kc:)

---

### Post by capscrew on 2011-10-30
> **kcpilotguy said:**
> @capscrew

Thanks for the guidance.  I have made all the changes you stated and this is where I am at now.  
It appears the you now can see the the host *zserver* while browsing.  At this point you just need to create proper shares.> 

Here is what my smb.conf files now looks like:

```

...

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = ZWORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)
[COLOR="Red"]# Allows a host to broadcast the NETBIOS name [/COLOR]
netbios name = zserver
name resolve order = bcast hosts

...

[COLOR="black"][test]
path = /home/zserver/test
available = yes

valid users = zserver [COLOR="Red"]|[/COLOR]
public = yes          [COLOR="Red"]| If this is to be public then you can't use *valid users*[/COLOR]

browsable = yes

read only = no [COLOR="Red"]|[/COLOR]
writable = yes [COLOR="Red"]| These provide the same results[/COLOR]

[COLOR="black"]#[test]
#path = /media/zserver_sto/zlaptop
#available = yes [COLOR="Red"]<-- This is the default -- no need to declare it.[/COLOR]
#valid users = zserver [COLOR="Red"]<-- This denies other users access -- Is that what you want?[/COLOR]
#read only = no [COLOR="Red"]<-- <-- This grants the user the ability to create or modify files.[/COLOR]
#browsable = yes [COLOR="Red"]<--This is the default -- if you say no the share is invisable.[/COLOR]
#public = yes [COLOR="Red"]<-- This parameter is a synonym for guest ok.[/COLOR] More below!

#writable = yes[COLOR="Blue"]<--This is the part I am trying to get to work and having issues.  
The path is for my second harddrive which I have put in a screen shot[/COLOR]
[COLOR="Red"]# This is an inverted synonym for ***read only = no** *you only need to declare one or 
the other.  I use ***writable = yes***.[/COLOR]


```

See my notes above in red.

If you  are having access problems then we should look at the file systems permissions.  It is important to understand that Samba provides: a) *authentication* (who you are) and b) *authorization* (you can do that) only to the point of that the underlying filesystem allows.  In other words Linux is the final arbiter of file and directory permissions.

If you want users to be able to view and read files then you should first allow them permission with the Linux file system and then allow them access via Samba.  I created a user named smbguest and declared that in the smb.conf file. I also have a group called smbusers that all Samba users belong to.  I control read and write permissions with this group.

I can help you setup the Linux permissions if you want.

As you have already seen you can mount the 1.5TB HDD (partition) on any empty directory.  I believe /media is for removable media such as floppy drives, USB drives and CD/DVD players.  When these are mounted they should show up on the *local hosts* desktop.  Not what you need for a Samba share on a server.

I have two (2) 1.0TB HDD.  I create a directory off of /.  It looks like this /smb.  Then I make 2 subdirectories.  One is /smb/backup and the other is /smb/public.  In fact you will find there is a /srv directory already and it was for server services, but I never use it.  It is not mnemonic enough for me.

I would not use the root directory on your HDD as a share.  It's not flexible enough.  Once you share it the whole drive is shared.  I recommend subdirectories such as /smb/backup or /smb/movies or /smb/pictures for the share points.  This separates the data.  The division allows you to control the access to the various parts of the file system.

Let me know if you need more help.

---

### Post by kcpilotguy on 2011-11-04
@capscrew

Thanks for the continued support.  I am at a point where I require some additional help. 

What I have done so far is:

-Mount the 1.5TB HD at /smb like you suggested
-Edited smb.conf file to correct as you suggested (see red changes/blue comments below)

```


#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = ZWORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

netbios name = zserver
name resolve order = bcast hosts

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

[COLOR="red"]usershare owner only = false[/COLOR][COLOR="Blue"]<---saw this and implemented so everyone can see files (think this is correct/ADVISE?[/COLOR]

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[COLOR="Red"][ZServer_Sto][COLOR="blue"]<---Figured out this is what shows up as the name of the shared directory so happy with this[/COLOR]
path = /smb
available = yes
browsable = yes
public = yes
writable = yes
;valid users = zserver [COLOR="blue"]<---commented out per your suggesteion[/COLOR]
;read only = no[COLOR="blue"]<commented out per your suggestion[/COLOR][/COLOR]


```

At this point I can see the /smb directory from all my laptops.  I also created subdirectories in the /smb folder, but for some reason I can not write to them.  I also had to be root to create the sub directories in /smb and do it from the terminal. 

I am sure there is a simple thing I am missing, but any pointers are appreciated.

Once we get this last fix, I think I am at the point where I want to be with being able to browse/create etc.  My next question is making users.  Right now the primary user on this server is "zserver" and that is the username/password combination I have been using to access folders, etc.  I want to create usernames for my  laptop and wife's laptop so that they can browse to all subdirectories in /smb, but only read/write/delete to the specific ones they are assigned and the "zserver" user act as admin and be able to do anything to all files in /smb.

Again, I am sure the implementation is simple but just need some pointing in the right direction.

Thanks for the continued support @capscrew.

Really appreciate all the help and could not have got this up and running without you.

kc

---

### Post by capscrew on 2011-11-05
> **kcpilotguy said:**
> @capscrew

Thanks for the continued support.  I am at a point where I require some additional help. 

What I have done so far is:

-Mount the 1.5TB HD at /smb like you suggested
-Edited smb.conf file to correct as you suggested (see red changes/blue comments below)

```


#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = ZWORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

netbios name = zserver
name resolve order = bcast hosts

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

[COLOR="red"]usershare owner only = false[/COLOR][COLOR="Blue"]<---saw this and implemented so everyone can see files (think this is correct/ADVISE?[/COLOR]

```



It's important to note what a usershare really is

```
Starting with Samba version 3.0.23 the capability for ***[COLOR="Red"]non-root users[/COLOR]*** [I]to add,
modify, and delete their own share definitions[/I] has been added. This capability is 
called usershares and is controlled by a set of parameters in the [global] section 
of the smb.conf. 
```

As the administrator of my home network.  I have setup all the shares via the smb.conf file.  If you want to allow other users (non-root) to create shares, at least make it so that they can only share what they own and not everything that they can see.  Strong stuff I know, but a good habit to be in.
 
The default is ```
usershare owner only = true
```
This parameter is to control whether *non-root users *have the right to create shares that they are not the owner of the directory they are attempting to share.  What your configuration is allowing is: *[COLOR="Red"]**Any** user can share **any** directory (folder) regardless of whether he/she owns it.[/COLOR]* 

> 

...

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes



Hmmmmmm, what are the implications of this???

> 
#======================= Share Definitions =======================
```

...

[COLOR="Red"][ZServer_Sto][COLOR="blue"]<---Figured out this is what shows up as the name of the shared directory so happy with this[/COLOR]
path = /smb
available = yes
browsable = yes
public = yes
writable = yes
;valid users = zserver [COLOR="blue"]<---commented out per your suggesteion[/COLOR]
;read only = no[COLOR="blue"]<commented out per your suggestion[/COLOR][/COLOR]


```
At this point I can see the /smb directory from all my laptops.  I also created subdirectories in the /smb folder, but for some reason I can not write to them.  I also had to be root to create the sub directories in /smb and do it from the terminal. 

I am sure there is a simple thing I am missing, but any pointers are appreciated.


File and directory (folder) permissions are the root of this problem.  I assume that the owner:group of the directory /smb is root:root.  

You can do 1 of 2 things; a) change the owner of the group to your user.  This will help you but not other users or b) assign a group that all samba users will be part of and change the permissions for the group to rwx.  This will help all Samba users and is my recommendation.

Earlier I suggested creating a group named smbusers, but you can use the already created group sambashare if you like.  To confirm that this user group exists try this ```
getent group | grep samba
```

This is what I get: ```
 getent group|grep samba
sambashare:x:122:capscrew,pam,rita,george,roy,adam,guest

```
This lists all the users in the group sambashare.
> 

Once we get this last fix, I think I am at the point where I want to be with being able to browse/create etc.  

I think you need to reconsider sharing the entire partition at one time.  Mounting the partition at /smb is one thing.  Sharing the entire partition in one share is something very different.  Consider the implications of sharing the entire space at one time.  Everyone has access by default.  You now have to work to keep all users (including guests) away from anything that you deem private.  I like do it the other way; Add users to data I want them to see.

I would do this ```

/smb <--------This is the mount point only -- no share defined
/smb/data1 <--first share -- users user1 and user 2 allowed (valid users)
/smb/zserver <--second share -- only user 1 allowed (valid users)
/smb/public <--third share -- Public share -- anyone allowed (guest = ok
```

A simple **public** share could be 

```

[Public]
	comment = Public Share
	path = /smb/public
	browseable = yes
	guest ok = yes
	writeable = yes
```

A private share might be this
```
[Private]
	comment = zserver only Share
	path = /smb/zserver
        valid users = zserver
	browseable = yes
	guest ok = no
	writeable = yes
```
As you can see, both of these shares have differing roots (/smb/public vs /smb/zserver).  In the long run you have more flexibility.
> 

My next question is making users.  Right now the primary user on this server is "zserver" and that is the username/password combination I have been using to access folders, etc.  

I want to create usernames for my  laptop and wife's laptop so that they can browse to all subdirectories in /smb, but only read/write/delete to the specific ones they are assigned and the "zserver" user act as admin and be able to do anything to all files in /smb.
These questions are what I was referring to just above.  In addition it is also important to understand that you create usernames for the Unbuntu server and also a Samba User.  I would suggest that the username/pass on the laptop be the same as is used on the Samba server.  For example the hostname (NETBIOS NAME) of samba server is rincon and the hostname of desktop is malibu.  The user name and password is the same on both (i.e capscrew).  In this way I have simplified the permissions problems and login problems.

If you have a login on the laptop then create a user on the Samba server with the same name. Then create a Samba user with the same name and password like this ```
smbpasswd -a <laptop_user_name>
```

You can confirm the creation with this ```
sudo pdbedit -L
```> 

Again, I am sure the implementation is simple but just need some pointing in the right direction.
I don't know how much I can assume you know, so I add all that I can to the mix.  :D

FYI -- The default permissions at creation for files is 0644 and for directories it is 0755.  For sharing it is best set to 0664 and 0775.  This can be set using umask.  The default is 022. Set it to 002 to change the defaults.  If you need to know how to do this ask me.> 

Thanks for the continued support @capscrew.

Really appreciate all the help and could not have got this up and running without you.

kc
At this point we are in the process of the ***design of the file system and permissions***.  I want this to be as simple and scalable as possible, so I'm pushing for correctness here.

---

### Post by kcpilotguy on 2012-02-04
hey @capscrew,

Haven't been on here is a long while. Have been on travel for the past several months and finally back to working on this thing.

I was reading back through our troubleshooting and where we left off was setting up the server so that multiple users have access to various directories as you stated here:

> 

 think you need to reconsider sharing the entire partition at one time. Mounting the partition at /smb is one thing. Sharing the entire partition in one share is something very different. Consider the implications of sharing the entire space at one time. Everyone has access by default. You now have to work to keep all users (including guests) away from anything that you deem private. I like do it the other way; Add users to data I want them to see.

I would do this
```
Code:
/smb <--------This is the mount point only -- no share defined
/smb/data1 <--first share -- users user1 and user 2 allowed (valid users)
/smb/zserver <--second share -- only user 1 allowed (valid users)
/smb/public <--third share -- Public share -- anyone allowed (guest = ok
```
A simple public share could be 

```
Code:
[Public]
	comment = Public Share
	path = /smb/public
	browseable = yes
	guest ok = yes
	writeable = yes

```
A private share might be this
```
Code:
[Private]
	comment = zserver only Share
	path = /smb/zserver
        valid users = zserver
	browseable = yes
	guest ok = no
	writeable = yes
```
As you can see, both of these shares have differing roots (/smb/public vs /smb/zserver). In the long run you have more flexibility.





So I have implemented those changes but still do not have a handle on the implementation of permissions in these directories.
I can see all the directories I create on the sever as well as from our laptops on the network, but can not do anything in them from the server or the laptops.

Need help with the next step where you said:

> These questions are what I was referring to just above. In addition it is also important to understand that you create usernames for the Unbuntu server and also a Samba User. I would suggest that the username/pass on the laptop be the same as is used on the Samba server. For example the hostname (NETBIOS NAME) of samba server is rincon and the hostname of desktop is malibu. The user name and password is the same on both (i.e capscrew). In this way I have simplified the permissions problems and login problems.

If you have a login on the laptop then create a user on the Samba server with the same name. Then create a Samba user with the same name and password like this
```
Code:
smbpasswd -a <laptop_user_name>
You can confirm the creation with this
Code:
sudo pdbedit -L
```

I don't know how much I can assume you know, so I add all that I can to the mix.  

FYI -- The default permissions at creation for files is 0644 and for directories it is 0755. For sharing it is best set to 0664 and 0775. This can be set using umask. The default is 022. Set it to 002 to change the defaults. If you need to know how to do this ask me.

kc
At this point we are in the process of the design of the file system and permissions. I want this to be as simple and scalable as possible, so I'm pushing for correctness here.

I am a bit slow on the uptake and this part did not make sense to me.  Tried creating a user but didn't seem to work.  Could you please walk me through this part step by step.

Thanks again for the help.

KC

---


---
title: "samba 11.10 &quot;Unable to mount location.....&quot;"
date: 2012-02-26
forum: General Help
---

### Post by dln9 on 2012-02-26
(I did some searching, I'm surprised that no one else has this same problem.)  

I'm running Ubuntu 11.10 on the problem computer in question.  

I have a network set up at home, all the computers run either Ubuntu or Linux Mint, one of which (the problem computer) is running Ubuntu 11.10.  

On this network, using Samba, all the other computers are seeing each others' folders just fine.  And, they can see the folders on the 11.10 computer.  But, the 11.10 computer can't see the folders on the other computers.  When, using the 11.10 computer, I click on "Browse Network" in the Nautilus file manager, after a very long wait, I get this message:  

"Unable to Mount Location.  
Failed to retrieve share list from server."  

Well, I haven't been able to figure out what that means, and what I ought to do.  

Thanks in advance for any help.

---

### Post by rowbird on 2012-02-26
Hi There, Check /var/log/samba logs on the server. This directory keeps a log of all the machines that connect, or attempt to connect to it.

---

### Post by dln9 on 2012-02-27
Thanks.  

Well, here's what in the log file you asked about, I hope you can tell me what it means:  

[2012/02/26 20:37:07,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2012/02/26 20:37:07,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.

---

### Post by bab1 on 2012-02-27
> **dln9 said:**
> Thanks.  

Well, here's what in the log file you asked about, I hope you can tell me what it means:  

[2012/02/26 20:37:07,  0] lib/util_sock.c:539(read_fd_with_timeout)
[2012/02/26 20:37:07,  0] lib/util_sock.c:1498(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection reset by peer.

This is one of the most common errors with Samba.  The "computer in question" cant find the rest of the network (i.e getpeername failed).

From the terminal, please post the output of```
testparm -s
```

Put the text between the [code] [/code ] blocks.  You can also use the # icon button at the top of the editing page to set the code blocks if you want.

---

### Post by dln9 on 2012-02-27
Ok, thanks again for helping.  

Here you go:  

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shared_stuff]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[shared_stuff]
	path = /home/main4/shared_stuff
	valid users = main4
	read only = No

```

---

### Post by bab1 on 2012-02-27
> **dln9 said:**
> Ok, thanks again for helping.  

Here you go:  

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[shared_stuff]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[shared_stuff]
	path = /home/main4/shared_stuff
	valid users = main4
	read only = No

```

I think what I would do is edit the smb.conf file.  You can open the file to edit like this```
gksudo gedit /etc/samba/smb.conf
```

Locate (in the [global] section) the line that starts with this```
; name resolve order = 
```

Delete the ; at the far left and add the parameter bcast just to the right of the = sign.  It will look something like this```
name resolve order = bcast host lmhosts 
```

This will cause the host to broadcast its name and look for others the same way.

Let us know how it works out.

---

### Post by dln9 on 2012-02-27
It did not work - still the same error messaage.  

I also noticed that on the server the log file for the 11.10 computer attempting to connect is not being updated.  If that matters.

---

### Post by bab1 on 2012-02-27
> **dln9 said:**
> It did not work - still the same error messaage.  

I also noticed that on the server the log file for the 11.10 computer attempting to connect is not being updated.  If that matters.

Lets see some debug.

Provide the output of ```
smbtree -d3
```

---

### Post by dln9 on 2012-02-27
Ok, here it is:  

```

main4@lappy4:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::21c:bfff:fe23:abc8%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.65 bcast=192.168.0.255 netmask=255.255.255.0
Enter main4's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to host=192.168.0.4
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to host=192.168.0.4
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
resolve_lmhosts: Attempting lmhosts lookup for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to host=192.168.0.4
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WDTVLIVEHUB    		WDTV LIVE
Connecting to host=WDTVLIVEHUB
resolve_lmhosts: Attempting lmhosts lookup for name WDTVLIVEHUB<0x20>
resolve_wins: Attempting wins lookup for name WDTVLIVEHUB<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name WDTVLIVEHUB<0x20>
Connecting to 66.152.109.24 at port 445
Connecting to 66.152.109.24 at port 139
Error connecting to 66.152.109.24 (Success)
Connecting to 184.106.31.170 at port 445
Connecting to 184.106.31.170 at port 139
Error connecting to 184.106.31.170 (Success)
cli_start_connection: failed to connect to WDTVLIVEHUB<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\SYSTEM1        		system1 server (Samba, Ubuntu)
Connecting to host=SYSTEM1
resolve_lmhosts: Attempting lmhosts lookup for name SYSTEM1<0x20>
resolve_wins: Attempting wins lookup for name SYSTEM1<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SYSTEM1<0x20>
Connecting to 66.152.109.24 at port 445
Connecting to 66.152.109.24 at port 139
Error connecting to 66.152.109.24 (Success)
Connecting to 184.106.31.170 at port 445
Connecting to 184.106.31.170 at port 139
Error connecting to 184.106.31.170 (Success)
cli_start_connection: failed to connect to SYSTEM1<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\LAPPY7         		lappy7 server (Samba, LinuxMint)
Connecting to host=LAPPY7
resolve_lmhosts: Attempting lmhosts lookup for name LAPPY7<0x20>
resolve_wins: Attempting wins lookup for name LAPPY7<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LAPPY7<0x20>
Connecting to 66.152.109.24 at port 445
Connecting to 66.152.109.24 at port 139
Error connecting to 66.152.109.24 (Success)
Connecting to 184.106.31.170 at port 445
Connecting to 184.106.31.170 at port 139
Error connecting to 184.106.31.170 (Success)
cli_start_connection: failed to connect to LAPPY7<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\LAPPY4         		lappy4 server (Samba, Ubuntu)
Connecting to host=LAPPY4
resolve_lmhosts: Attempting lmhosts lookup for name LAPPY4<0x20>
resolve_wins: Attempting wins lookup for name LAPPY4<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LAPPY4<0x20>
Connecting to 127.0.1.1 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LAPPY4\IPC$           	IPC Service (lappy4 server (Samba, Ubuntu))
		\\LAPPY4\shared_stuff   	
		\\LAPPY4\print$         	Printer Drivers
main4@lappy4:~$ 

```

---

### Post by bab1 on 2012-02-27
> **dln9 said:**
> Ok, here it is:  

```

main4@lappy4:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::21c:bfff:fe23:abc8%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.65 bcast=192.168.0.255 netmask=255.255.255.0
Enter main4's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
**[COLOR="Red"]resolve_lmhosts: Attempting lmhosts lookup[/COLOR]** for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to host=192.168.0.4
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
**[COLOR="Red"]resolve_lmhosts: Attempting lmhosts lookup[/COLOR]** for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to host=192.168.0.4
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
**[COLOR="Red"]resolve_lmhosts: Attempting lmhosts lookup[/COLOR]** for name WORKGROUP<0x1d>
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Connecting to host=192.168.0.4
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WDTVLIVEHUB    		WDTV LIVE
Connecting to host=WDTVLIVEHUB
[B][COLOR="Red"]resolve_lmhosts: Attempting lmhosts lookup for name WDTVLIVEHUB<0x20>
resolve_wins: Attempting wins lookup for name WDTVLIVEHUB<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name WDTVLIVEHUB<0x20>
Connecting to 66.152.109.24 at port 445
Connecting to 66.152.109.24 at port 139
Error connecting to 66.152.109.24 (Success)
Connecting to 184.106.31.170 at port 445
Connecting to 184.106.31.170 at port 139
Error connecting to 184.106.31.170 (Success)
cli_start_connection: failed to connect to WDTVLIVEHUB<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL[/COLOR][/B]
	\\SYSTEM1        		system1 server (Samba, Ubuntu)
Connecting to host=SYSTEM1
[B][COLOR="Red"]resolve_lmhosts: Attempting lmhosts lookup for name SYSTEM1<0x20>
resolve_wins: Attempting wins lookup for name SYSTEM1<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name SYSTEM1<0x20>
Connecting to 66.152.109.24 at port 445
Connecting to 66.152.109.24 at port 139
Error connecting to 66.152.109.24 (Success)
Connecting to 184.106.31.170 at port 445
Connecting to 184.106.31.170 at port 139
Error connecting to 184.106.31.170 (Success)
cli_start_connection: failed to connect to SYSTEM1<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL[/COLOR][/B]
	\\LAPPY7         		lappy7 server (Samba, LinuxMint)
Connecting to host=LAPPY7
[B][COLOR="Red"]resolve_lmhosts: Attempting lmhosts lookup for name LAPPY7<0x20>
resolve_wins: Attempting wins lookup for name LAPPY7<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name LAPPY7<0x20>
Connecting to 66.152.109.24 at port 445
Connecting to 66.152.109.24 at port 139
Error connecting to 66.152.109.24 (Success)
Connecting to 184.106.31.170 at port 445
Connecting to 184.106.31.170 at port 139
Error connecting to 184.106.31.170 (Success)
cli_start_connection: failed to connect to LAPPY7<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL[/COLOR][/B]
	\\LAPPY4         		lappy4 server (Samba, Ubuntu)
Connecting to host=LAPPY4
[B][COLOR="Red"]resolve_lmhosts: Attempting lmhosts lookup for name LAPPY4<0x20>
resolve_wins: Attempting wins lookup for name LAPPY4<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting _*host*_ lookup[/COLOR][/B] for name LAPPY4<0x20>
**[COLOR="Red"]Connecting to 127.0.1.1[/COLOR]** at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LAPPY4\IPC$           	IPC Service (lappy4 server (Samba, Ubuntu))
		\\LAPPY4\shared_stuff   	
		\\LAPPY4\print$         	Printer Drivers
main4@lappy4:~$ 

```

All that is in red above indicate some pretty severe misconfiguration.  It appears that the host is trying to connect via a public Internet IP address.  Samba (SMB/CIFS) doesn't work over routed inter-networks.  In addition you seem to have some WINS configuration, but not correctly.  WINS is not needed to run Samba in a home network.  Lastly you have requests for resolution using lmhosts.  This indicates that the line I asked you to add (name resolution order) was not properly configured.

I'm curious; how have you provisioned the name resolution for this network? Are you using DNS or WINS or /etc/hosts?  Are all the hosts on a local LAN?  

Please post the contents of the /etc/samba/smb.conf file for the host lappy4```
cat /etc/samba/smb.conf
```

---

### Post by dln9 on 2012-02-27
Well, I can't answer your questions, because....  I don't know what those words mean.  I try to follow the plethora of online advice about setting this up - there's a lot out there, I don't know who knows what he's talking about and who doesn't - but like I said, I don't understand all of what is said.  

Anyway, here's the output you asked about:  

```

main4@lappy4:~$ cat /etc/samba/smb.conf
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
	workgroup = workgroup

;	netbios name = system1

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

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
#   name resolve order = lmhosts host wins bcast
;   name resolve order = bcast host lmhosts

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
	security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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
;	printing = cups
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
;	usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
	usershare allow guests = yes
	username map = /etc/samba/smbusers
;	guest ok = no
;	guest account = nobody

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

;	wins support = no
;	wins support = no
;	wins support = no
;	wins support = no
;	wins support = no
;	wins support = no
;	wins support = no
;	wins support = no
;	wins support = no
[printers]
	comment = All Printers
	browseable = no
	path = /var/spool/samba
	printable = yes
;	guest ok = no
;	read only = yes
	create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
;	browseable = yes
;	read only = yes
;	guest ok = no
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


[shared_stuff]
	path = /home/main4/shared_stuff
;	available = yes
;	browseable = yes
	writeable = yes
	valid users = main4
main4@lappy4:~$ 

```


(In case it matters, I copied this file from the other computers on the network that use samba just fine - all I changed was the user name to be appropriate.)

---

### Post by bab1 on 2012-02-27
> **dln9 said:**
> Well, I can't answer your questions, because....  I don't know what those words mean.  I try to follow the plethora of online advice about setting this up - there's a lot out there, I don't know who knows what he's talking about and who doesn't - but like I said, I don't understand all of what is said.  
...


(In case it matters, I copied this file from the other computers on the network that use samba just fine - all I changed was the user name to be appropriate.)

I see you left the ; in place on this line```
**[COLOR="Red"];[/COLOR]**   name resolve order = bcast host lmhosts
``` You need to remove the ; .  The semicolon causes the Samba app to ignore the line.  Remove the semicolon (; ) and reboot the system.

Post the output again of ```
smbtree -d3
```

Also post the output of ```
findsmb
cat /etc/hosts
```

Are the other machines yours or...?

---

### Post by dln9 on 2012-02-27
Ok, it works now!  Yes, it seems that darn semicolon was the remaining problem.  

THANK YOU SO MUCH FOR YOUR HELP!!!!  

Just to finish things off, I'm including the output of the various commands you requested, just in case you see something else alarming.  

But, one question for you:  Can you explain to me, in laymen's terms, what this command is saying:  

name resolve order = bcast host lmhosts


AND - Why does this computer need  this command, while the other computers on the network do not?  


```

main4@lappy4:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface wlan0 ip=fe80::21c:bfff:fe23:abc8%wlan0 bcast=fe80::ffff:ffff:ffff:ffff%wlan0 netmask=ffff:ffff:ffff:ffff::
added interface wlan0 ip=192.168.0.65 bcast=192.168.0.255 netmask=255.255.255.0
Enter main4's password: 
tdb(/var/run/samba/gencache.tdb): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to host=192.168.0.4
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
name_resolve_bcast: Attempting broadcast lookup for name __MSBROWSE__<0x1>
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to host=192.168.0.4
Connecting to 192.168.0.4 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
WORKGROUP
name_resolve_bcast: Attempting broadcast lookup for name WORKGROUP<0x1d>
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to host=192.168.0.4
Connecting to 192.168.0.4 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
	\\WDTVLIVEHUB    		WDTV LIVE
Connecting to host=WDTVLIVEHUB
name_resolve_bcast: Attempting broadcast lookup for name WDTVLIVEHUB<0x20>
Got a positive name query response from 192.168.0.8 ( 192.168.0.8 )
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to 192.168.0.8 at port 445
Connecting to 192.168.0.8 at port 139
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
	\\SYSTEM1        		system1 server (Samba, Ubuntu)
Connecting to host=SYSTEM1
name_resolve_bcast: Attempting broadcast lookup for name SYSTEM1<0x20>
Got a positive name query response from 192.168.0.2 ( 192.168.0.2 )
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to 192.168.0.2 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\SYSTEM1\dropbox        	
		\\SYSTEM1\IPC$           	IPC Service (system1 server (Samba, Ubuntu))
		\\SYSTEM1\shared_stuff   	
		\\SYSTEM1\print$         	Printer Drivers
	\\LAPPY7         		lappy7 server (Samba, LinuxMint)
Connecting to host=LAPPY7
name_resolve_bcast: Attempting broadcast lookup for name LAPPY7<0x20>
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Got a positive name query response from 192.168.0.4 ( 192.168.0.4 )
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to 192.168.0.4 at port 445
Connecting to 192.168.0.4 at port 139
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LAPPY7\shared_stuff   	
		\\LAPPY7\IPC$           	IPC Service (lappy7 server (Samba, LinuxMint))
		\\LAPPY7\print$         	Printer Drivers
	\\LAPPY4         		lappy4 server (Samba, Ubuntu)
Connecting to host=LAPPY4
name_resolve_bcast: Attempting broadcast lookup for name LAPPY4<0x20>
Got a positive name query response from 192.168.0.65 ( 192.168.0.65 )
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(/var/run/samba/unexpected.tdb): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connecting to 192.168.0.65 at port 445
Doing spnego session setup (blob length=58)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
		\\LAPPY4\IPC$           	IPC Service (lappy4 server (Samba, Ubuntu))
		\\LAPPY4\shared_stuff   	
		\\LAPPY4\print$         	Printer Drivers
main4@lappy4:~$ 

```


```

main4@lappy4:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.2     SYSTEM1        [WORKGROUP] [Unix] [Samba 3.4.7]
192.168.0.4     LAPPY7        +[WORKGROUP] [Unix] [Samba 3.4.7]
192.168.0.8     WDTVLIVEHUB    [WORKGROUP] [Unix] [Samba 3.5.6]
192.168.0.65    LAPPY4         [WORKGROUP] [Unix] [Samba 3.5.11]
main4@lappy4:~$ 

```


```

main4@lappy4:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	lappy4

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
main4@lappy4:~$ 

```

---

### Post by bab1 on 2012-02-27
> **dln9 said:**
> Ok, it works now!  Yes, it seems that darn semicolon was the remaining problem.  

THANK YOU SO MUCH FOR YOUR HELP!!!!  

Just to finish things off, I'm including the output of the various commands you requested, just in case you see something else alarming.  

But, one question for you:  Can you explain to me, in laymen's terms, what this command is saying:  

name resolve order = bcast host lmhosts

The line sets the order that the Samba process uses to resolve the computer name to IP address.  The host uses the /etc/host and then DNS to resolve the name.  You have no reference to the IP address in you /etc/hosts file so it was looking at your ISP's DNS server for help (not a good thing).  The lmhosts is another flat file database to resolve computer name to IP address.  Lastly (and in your case we want it to be used FIRST is bcast which literally broadcasts only on the LAN for computer names.  All computers on the LAN respond to this request.  That's as simple as I can make it.> 


AND - Why does this computer need  this command, while the other computers on the network do not?


I'm not so sure that the other computers wouldn't benefit from that line.  There is a default order if nothing is explicitly declared (hint -- bcast is *not* first).

---

### Post by dln9 on 2012-02-28
Ok, thanks again for all your help.

---


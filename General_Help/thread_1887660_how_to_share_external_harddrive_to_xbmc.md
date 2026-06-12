---
title: "how to share external harddrive to xbmc"
date: 2011-11-27
forum: General Help
---

### Post by reynoldsbrian on 2011-11-27
Hey

So i have ubuntu installed a week.. and the folders i sahre from the c drive work perfectly, but most of my video files are on the external harddrive which i cannot access even though i go through the same smb share tutorial.

Would be great to get the solution here

thanks

---

### Post by Morbius1 on 2011-11-27
Your external drive is formatted in a Windows filesystem like Fat32 or NTFS? If so it will mount with access limited only to you. The remote user isn't you so he's out of luck. The solution is to make the remote user look like you by adding a parameter to smb.conf:
```
force user = your-user-name
```[COLOR=Blue]*Replace your-user-name with your local login user name*[/COLOR].
THen restart samba:
```
sudo service smbd restart
```Wait a few minutes - seriously, minutes and try to access the share.

[COLOR=Blue]**NOTE**[/COLOR]: Where you place that line in smb.conf depends on how you created the share and " smb share tutorial"  doesn't tell us that. If your share definitions are in smb.conf itself then place it in the share definition. If you created the share through Nautilus then place it in the [global] section.

If you have no idea what I'm talking about post the output of the following commands and I can assist:
```
testparm -s
``````
net usershre info --long
```

---

### Post by reynoldsbrian on 2011-11-27
I am new to ubuntu, not sure how to edit that file.. just opens in chrome when i click on it and doesnt open in gedit

thanks for your help so far


testparm -s


Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
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

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


and then


noxy@noxy-Dell:~$ ^C
noxy@noxy-Dell:~$ net usershre info --long
Invalid command: net usershre
Usage:
net rpc             Run functions using RPC transport
net rap             Run functions using RAP transport
net ads             Run functions using ADS transport
net file            Functions on remote opened files
net share           Functions on shares
net session         Manage sessions
net server          List servers in workgroup
net domain          List domains/workgroups on network
net printq          Modify printer queue
net user            Manage users
net group           Manage groups
net groupmap        Manage group mappings
net sam             Functions on the SAM database
net validate        Validate username and password
net groupmember     Modify group memberships
net admin           Execute remote command on a remote OS/2 server
net service         List/modify running services
net password        Change user password on target server
net changetrustpw   Change the trust password
net changesecretpw  Change the secret password
net setauthuser     Set the winbind auth user
net getauthuser     Get the winbind auth user settings
net time            Show/set time
net lookup          Look up host names/IP addresses
net g_lock          Manipulate the global lock table
net join            Join a domain/AD
net dom             Join/unjoin (remote) machines to/from a domain/AD
net cache           Operate on the cache tdb file
net getlocalsid     Get the SID for the local domain
net setlocalsid     Set the SID for the local domain
net setdomainsid    Set domain SID on member servers
net getdomainsid    Get domain SID on member servers
net maxrid          Display the maximul RID currently used
net idmap           IDmap functions
net status          Display server status
net usershare       Manage user-modifiable shares
net usersidlist     Display list of all users with SID
net conf            Manage Samba registry based configuration
net registry        Manage the Samba registry
net eventlog        Process Win32 *.evt eventlog files
net help            Print usage information
noxy@noxy-Dell:~$ ^C
noxy@noxy-Dell:~$

---

### Post by Morbius1 on 2011-11-27
* I have no idea why any *.conf file would open up in Chrome.

* You don't appear to have classic shares in smb.conf so you must have created shares in Nautilus.

* I can't spell. The correct command should have been:
```
net usershare info --long
```I'm going to guess they were created in Nautilus so edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section - right under the workgroup = line is where I'd put it:
```
force user = noxy
```Save the file, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```Wait a bit and then try to access the share.

---


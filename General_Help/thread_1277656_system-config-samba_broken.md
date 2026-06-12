---
title: "system-config-samba broken?"
date: 2009-09-28
forum: General Help
---

### Post by Jive Turkey on 2009-09-28
I thought I would post this here before submitting a bug to see if maybe I have something misconfigured.

system-config-samba appears under System>Administration>Samba, and it should allow configuration of one's smb.conf from a gui.  It hasn't worked for me in quite a while, launching from the menu fails silently after a gksu prompt.  CLI output:
```
$sudo system-config-samba
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 82, in __init__
    self.samba_data = sambaParser.SambaParser(self)
  File "/usr/share/system-config-samba/sambaParser.py", line 185, in __init__
    self.parseFile ()
  File "/usr/share/system-config-samba/sambaParser.py", line 228, in parseFile
    section = SambaSection (token.value)
  File "/usr/share/system-config-samba/sambaParser.py", line 49, in __init__
    raise Error ("section %s already defined" % (name))
NameError: global name 'Error' is not defined

```
I had previously configured smb.conf with swat but removed swat as it is no longer maintained and is not very secure according to the description in synaptic.  Also I could not connect to the swat interface either.  samba will serve to some client machines and not others. 
Here is my (sanitized) smb.conf:
```
[global]
	workgroup = myworkgroup
	server string = %h server
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb bamyuserend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	wins server = mywinsserver's IP
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

[home]
	path = /home/myuser
	valid users = myuser
	write list = myuser
	read only = No

[Videos]
	path = /home/myuser/Videos
	valid users = myuser, otheruser
	read list = otheruser, myuser
	write list = myuser
```
...as summarised by the command testparm

Thanks in advance for any suggestions.

---


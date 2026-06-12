---
title: "Unable to print from remote PC to server via SAMBA"
date: 2009-11-22
forum: General Help
---

### Post by rhcm123 on 2009-11-22
I have a small server setup to do a bunch of stuff, most importantly anon ftp (cause i know ill leave my docs at home occasionally) and Printing. Printing is most important, but only linux-based (aka IPP supporting machines, although its incredibly slow at getting the documents out, but that's another problem) can do it. I have 1 windows xp machine and 2 vista machines and they both need to be printing here.

Heres the cups config: [/etc/cups/cupsd.conf]

```
LogLevel debug
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
order allow, deny
Allow localhost
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  Allow all
  Allow all
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  Allow all
  Allow all
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Allow all
  Allow all
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>

```


samba config file: [/etc/samba/smb.conf]
```
# CONFIG FILE FOR SAMBA
# WRITTEN BY USSR
# LAST MODIFIED 12 APRIL 2009

# Global parameters
[global]
	log file = /var/log/samba/log.%m
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	map to guest = bad user
	wins support = true
	encrypt passwords = yes
	dns proxy = No
	netbios name = USSR-MOSCOW
	server string = SMB system [USSR-MOSCOW]
	client lanman auth = No
	client plaintext auth = No
	lanman auth = No
	default = Share
	local master = Yes
	workgroup = USSR
	os level = 20
	security = user
	preferred master = no
	max log size = 50
	printing = cups
	printcap name = cups
	use client driver = yes
	guest account = nobody
	load printers = yes
	interfaces = 192.168.2.193

# /SHARE CONFIGS
[share]
	browseable = yes
	read only = No
	writeable = yes
	path = /share
	create mask = 0700
	comment = Main share directory on USSR-MOSCOW.
	directory mask = 0700
	valid users = ussr,elisabeth,fred,carol,root,nobody

# PRINTER SETTINGS
[printers]
	comment = Printers on USSR-MOSCOW
	browseable = yes
	path = /printer
	printable = yes
	public = yes
	writable = no
	create mode = 0700
	valid users = ussr,elisabeth,fred,carol,root,nobody

# CDROM SHARING
[cdrom]
	comment = CD on USSR-MOSCOW
	read only = yes
	writable = no
 	locking = no
	path = /media/cdrom
	public = yes

```

---

### Post by jm2 on 2009-11-22
Are you printing to a printer attached to the PC or Linux box?

---

### Post by XubuRoxMySox on 2009-11-22
The # character means that line is "commented out." Think of it as an "un-check" mark. In your post the "uncheck" mark appears at the beginning of the commands you want "checked," so to speak.

Wanna keep it simple? Go to [http://localhost:631/](http://localhost:631/) in your browser, choose **Administration** and see if your printer appears there (if you asked to login, use your root username and password). If not click Add Printer and check the box next to the "share printer" option.

-Robin

---

### Post by rhcm123 on 2009-12-02
> **jm2 said:**
> Are you printing to a printer attached to the PC or Linux box?

the printer is attached to a linux box, the clients are all windows (at least the ones having issues, the ubuntu clients connect fine)

> **dixiedancer said:**
> The # character means that line is "commented out." Think of it as an "un-check" mark. In your post the "uncheck" mark appears at the beginning of the commands you want "checked," so to speak.

Wanna keep it simple? Go to [http://localhost:631/](http://localhost:631/) in your browser, choose **Administration** and see if your printer appears there (if you asked to login, use your root username and password). If not click Add Printer and check the box next to the "share printer" option.

-Robin

i do online administration already.

---

### Post by aguilla1 on 2009-12-05
I have a similar problem where the Linux box (Ubuntu) has my printer attached and the remote PC (Vista laptop) has a hard time printing. The Linux box and Laptop can share files and occasionally (about 10%) the laptop can print via samba, but not usually. The symptoms are that the Vista laptop thinks it has submitted the item to be printed but the Linux Box does not always have this information. 

I have no problem printing from the Linux Box

Unfortunately, the Linux Box does not have the exact updated printer driver while the Laptop does.

Does anyone know where I have to look and what I could change?

---

### Post by rhcm123 on 2009-12-07
> **aguilla1 said:**
> I have a similar problem where the Linux box (Ubuntu) has my printer attached and the remote PC (Vista laptop) has a hard time printing. The Linux box and Laptop can share files and occasionally (about 10%) the laptop can print via samba, but not usually. The symptoms are that the Vista laptop thinks it has submitted the item to be printed but the Linux Box does not always have this information. 

I have no problem printing from the Linux Box

Unfortunately, the Linux Box does not have the exact updated printer driver while the Laptop does.

Does anyone know where I have to look and what I could change?

sounds like an access denied error (e.g. one user allowed to print, other users not). Try also firewall, you say the information isn't getting through.

---

### Post by rhcm123 on 2009-12-22
Never mind, i fixed it. Samba was supposed to write the print files sent by the remote machines to /printers. But printers was chmoded 100. Fixed that with chmod 777, and it works fine. (probs could do that better but i don't really care). Works fine now.

---


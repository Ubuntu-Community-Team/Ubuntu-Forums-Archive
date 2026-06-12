---
title: "Samba read/write troubles"
date: 2006-04-04
forum: General Help
---

### Post by aaalunchbox on 2006-04-04
howdy.

here is the setup.  I have ubuntu breezy running with samba.  I'm using the swat interface and i've had no problems.  However, i have a share folder from my Home folder that i would like to be able to write to from windows over the lan (mostly for backup).  I have my user account added to the smbpasswd folder and i have permissions for the folder (/home/matt/share) set to 777.  However, when i try to transfer a file from a windows machine to my ubuntu box(havn't tried from a *inx machine yet) i get a "write protection or in use" error.  But i can navigate and open files fine.  Just can't write.  In swat, i have my samba account set to admin and valid user.    Anyway, here is the smb.conf file (swat format sorry).  Anything stand out?

```
# Samba config file created using SWAT
# from 0.0.0.0 (0.0.0.0)
# Date: 2006/04/04 13:46:08

# Global parameters
[global]
	dos charset = CP850
	unix charset = UTF-8
	display charset = LOCALE
	workgroup = CCMI1
	realm = 
	netbios name = BOX
	netbios aliases = 
	netbios scope = 
	server string = Samba 3.0.14a-Ubuntu
	interfaces = 
	bind interfaces only = No
	security = USER
	auth methods = 
	encrypt passwords = Yes
	update encrypted = No
	client schannel = Auto
	server schannel = Auto
	allow trusted domains = Yes
	hosts equiv = 
	min password length = 5
	map to guest = Never
	null passwords = No
	obey pam restrictions = No
	password server = *
	smb passwd file = /etc/samba/smbpasswd
	private dir = /etc/samba
	passdb backend = smbpasswd
	algorithmic rid base = 1000
	root directory = 
	guest account = nobody
	enable privileges = No
	pam password change = No
	passwd program = 
	passwd chat = *new*password* %n\n *new*password* %n\n *changed*
	passwd chat debug = No
	passwd chat timeout = 2
	check password script = 
	username map = 
	password level = 0
	username level = 0
	unix password sync = No
	restrict anonymous = 0
	lanman auth = Yes
	ntlm auth = Yes
	client NTLMv2 auth = No
	client lanman auth = Yes
	client plaintext auth = Yes
	preload modules = 
	use kerberos keytab = No
	log level = 0
	syslog = 1
	syslog only = No
	log file = 
	max log size = 5000
	debug timestamp = Yes
	debug hires timestamp = No
	debug pid = No
	debug uid = No
	smb ports = 445 139
	large readwrite = Yes
	max protocol = NT1
	min protocol = CORE
	read bmpx = No
	read raw = Yes
	write raw = Yes
	disable netbios = No
	acl compatibility = 
	defer sharing violations = Yes
	nt pipe support = Yes
	nt status support = Yes
	announce version = 4.9
	announce as = NT
	max mux = 50
	max xmit = 16644
	name resolve order = lmhosts wins host bcast
	max ttl = 259200
	max wins ttl = 518400
	min wins ttl = 21600
	time server = No
	unix extensions = Yes
	use spnego = Yes
	client signing = auto
	server signing = No
	client use spnego = Yes
	change notify timeout = 60
	deadtime = 0
	getwd cache = Yes
	keepalive = 300
	kernel change notify = Yes
	lpq cache time = 30
	max smbd processes = 0
	paranoid server security = Yes
	max disk size = 0
	max open files = 10000
	socket options = TCP_NODELAY
	use mmap = Yes
	hostname lookups = No
	name cache timeout = 660
	load printers = Yes
	printcap cache time = 0
	printcap name = 
	cups server = 
	disable spoolss = No
	enumports command = 
	addprinter command = 
	deleteprinter command = 
	show add printer wizard = Yes
	os2 driver map = 
	mangling method = hash2
	mangle prefix = 1
	stat cache = Yes
	machine password timeout = 604800
	add user script = 
	delete user script = 
	add group script = 
	delete group script = 
	add user to group script = 
	delete user from group script = 
	set primary group script = 
	add machine script = 
	shutdown script = 
	abort shutdown script = 
	logon script = 
	logon path = \\%N\%U\profile
	logon drive = 
	logon home = \\%N\%U
	domain logons = No
	os level = 20
	lm announce = Auto
	lm interval = 60
	preferred master = Auto
	local master = Yes
	domain master = Auto
	browse list = Yes
	enhanced browsing = Yes
	dns proxy = Yes
	wins proxy = No
	wins server = 
	wins support = No
	wins hook = 
	wins partners = 
	kernel oplocks = Yes
	lock spin count = 3
	lock spin time = 10
	oplock break wait time = 0
	ldap admin dn = 
	ldap delete dn = No
	ldap filter = (uid=%u)
	ldap group suffix = 
	ldap idmap suffix = 
	ldap machine suffix = 
	ldap passwd sync = no
	ldap replication sleep = 1000
	ldap suffix = 
	ldap ssl = no
	ldap timeout = 15
	ldap user suffix = 
	add share command = 
	change share command = 
	delete share command = 
	config file = 
	preload = 
	lock directory = 
	pid directory = /var/run/samba
	utmp directory = 
	wtmp directory = 
	utmp = No
	default service = 
	message command = 
	dfree command = 
	get quota command = 
	set quota command = 
	remote announce = 
	remote browse sync = 
	socket address = 0.0.0.0
	homedir map = auto.home
	afs username map = 
	afs token lifetime = 604800
	log nt token command = 
	time offset = 0
	NIS homedir = No
	panic action = 
	host msdfs = No
	enable rid algorithm = Yes
	idmap backend = 
	idmap uid = 
	idmap gid = 
	template primary group = nobody
	template homedir = /home/%D/%U
	template shell = /bin/false
	winbind separator = \
	winbind cache time = 300
	winbind enable local accounts = No
	winbind enum users = Yes
	winbind enum groups = Yes
	winbind use default domain = No
	winbind trusted domains only = No
	winbind nested groups = No
	comment = 
	path = 
	username = 
	invalid users = 
	valid users = box, matt
	admin users = matt
	read list = 
	write list = 
	printer admin = 
	force user = 
	force group = 
	read only = Yes
	create mask = 0744
	force create mode = 00
	security mask = 0777
	force security mode = 00
	directory mask = 0755
	force directory mode = 00
	directory security mask = 0777
	force directory security mode = 00
	force unknown acl user = No
	inherit permissions = No
	inherit acls = No
	guest only = No
	guest ok = No
	only user = No
	hosts allow = 
	hosts deny = 
	allocation roundup size = 1048576
	ea support = No
	nt acl support = Yes
	profile acls = No
	map acl inherit = No
	afs share = No
	block size = 1024
	max connections = 0
	min print space = 0
	strict allocate = No
	strict sync = No
	sync always = No
	use sendfile = No
	write cache size = 0
	max reported print jobs = 0
	max print jobs = 1000
	printable = No
	printing = bsd
	cups options = 
	print command = lpr -r -P'%p' %s
	lpq command = lpq -P'%p'
	lprm command = lprm -P'%p' %j
	lppause command = 
	lpresume command = 
	queuepause command = 
	queueresume command = 
	printer name = 
	use client driver = No
	default devmode = No
	force printername = No
	default case = lower
	case sensitive = Auto
	preserve case = Yes
	short preserve case = Yes
	mangling char = ~
	hide dot files = Yes
	hide special files = No
	hide unreadable = No
	hide unwriteable files = No
	delete veto files = No
	veto files = 
	hide files = 
	veto oplock files = 
	map system = No
	map hidden = No
	map archive = Yes
	mangled names = Yes
	mangled map = 
	store dos attributes = No
	browseable = Yes
	blocking locks = Yes
	csc policy = manual
	fake oplocks = No
	locking = Yes
	oplocks = Yes
	level2 oplocks = Yes
	oplock contention limit = 2
	posix locking = Yes
	strict locking = Yes
	share modes = Yes
	copy = 
	include = 
	preexec = 
	preexec close = No
	postexec = 
	root preexec = 
	root preexec close = No
	root postexec = 
	available = Yes
	volume = 
	fstype = NTFS
	set directory = No
	wide links = Yes
	follow symlinks = Yes
	dont descend = 
	magic script = 
	magic output = 
	delete readonly = No
	dos filemode = No
	dos filetimes = Yes
	dos filetime resolution = No
	fake directory create times = No
	vfs objects = 
	msdfs root = No
	msdfs proxy = 

[dl]
	comment = Work Files
	path = /windows/DL

[klfs]
	path = /windows/klfs

[share]
	path = /home/matt/share
```

---

### Post by rmjokers on 2006-04-04
I think the line:

read only = Yes

is part of the problem.  Try removing that and adding:

read only = No

To the share that you want to be able to write to.

---


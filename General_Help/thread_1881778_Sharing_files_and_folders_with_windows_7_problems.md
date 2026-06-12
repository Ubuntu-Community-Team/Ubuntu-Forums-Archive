---
title: "Sharing files and folders with windows 7 problems"
date: 2011-11-16
forum: General Help
---

### Post by davidtheo on 2011-11-16
I am trying to share files and folders on my Ubuntu computer with mu wifes windows 7 computer.

I right clicked on the folder I wanted and clicked share.
it them asked me to install the share files so I did.
after I tried to share the folder by clicking share again and checking the share check box.

The folders do not show on my wifes computer Under "nerwork" or any other place.
My computer is not showing on my wifes computers

I have searched the web and everywhere tells me I need to select Windows networks from the drop down but I do not have this drop down.

How can I fix this and share my F drive with my wife. Yes I want to share the drive or all the folders on the drive.  

Thanks if you can help.

---

### Post by BillyBoa on 2011-11-16
It's a long story this problem.

Try to do this

From the Software Center install SAMBA.

Then from Dash Search and execute SAMBA.

From the Preferences tab, choose Server Settings and from the Basic tab write a name for the workgroup you are going to create in your house. Then in Security tab, change security to Share.

Go now to the Win7 computer and create  a workgroup with the same name and without security password.

Restart both computers and cross your fingers

---

### Post by decrepit on 2011-11-16
I have this computer sharing files with an XP computer via samba, no problems. but I just couldn't manage it with windows 7. For some reason I couldn't get windows7 to see the samba shares. The auto setup in W7 just wants to look for other W7 computers.
I just assumed they've changed the protocol

---

### Post by davidtheo on 2011-11-16
> **BillyBoa said:**
> It's a long story this problem.

Try to do this

From the Software Center install SAMBA.

Then from Dash Search and execute SAMBA.

From the Preferences tab, choose Server Settings and from the Basic tab write a name for the workgroup you are going to create in your house. Then in Security tab, change security to Share.

Go now to the Win7 computer and create  a workgroup with the same name and without security password.

Restart both computers and cross your fingers

Hi Billy Boa

I tried to download SAMBA and it just asks for my password and then nothing happens.
I download GADMIN-SAMBA too and still no joy

Anything else I can try?

---

### Post by Morbius1 on 2011-11-16
You already had samba installed when you went into Nautilus to share the folder.

Please post the output of the following commands:
```
hostname
smbtree
net usershare info --long
testparm -s
```

Note: If you do anything with gadmin-samba you will end up with an incomprehensible mess and will have to start over again.

---

### Post by davidtheo on 2011-11-16
> **Morbius1 said:**
> You already had samba installed when you went into Nautilus to share the folder.

Please post the output of the following commands:
```
hostname
smbtree
net usershare info --long
testparm -s
```Note: If you do anything with gadmin-samba you will end up with an incomprehensible mess and will have to start over again.
```


hostname = ubuntu smbtree = just asks for my password

net usershare info --long = 

[pictures]
path=/home/david/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=n

[music]
path=/home/david/Music
comment=
usershare_acl=Everyone:F,
guest_ok=n
testparm -s = 

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Processing section "[Share]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	workgroup = HOMEGROUP
	netbios name = SAMBA24
	server string = Samba file and print server
	interfaces = 127.0.0.1/8, 192.168.0.0/24
	bind interfaces only = Yes
	update encrypted = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	guest account = smbguest
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	password level = 6
	username level = 6
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	name resolve order = wins lmhosts bcast
	client signing = No
	client use spnego = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	os level = 33
	local master = No
	domain master = No
	dns proxy = No
	remote announce = 192.168.0.255
	remote browse sync = 192.168.0.255
	idmap uid = 16777216-33554431
	idmap gid = 16777216-33554431
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	hosts allow = 127., 192.168.0.
	cups options = raw
	follow symlinks = No

[homes]
	comment = Home Directories
	path = /home
	read only = No
	locking = No
	strict locking = No

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	locking = No
	strict locking = No

[profiles]
	comment = User Profiles
	path = /var/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	browseable = No
	locking = No
	strict locking = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	browseable = No
	locking = No
	strict locking = No

[pdf-documents]
	comment = Converted PDF Documents
	path = /home/pdf-documents
	read only = No
	guest ok = Yes
	locking = No
	strict locking = No

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	guest ok = Yes
	printable = Yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command = 
	use client driver = Yes

[Share]
	comment = No comment
	path = /home/david/Music
	locking = No
	strict locking = No


```

thanks

---

### Post by Morbius1 on 2011-11-16
You know, when I read that you used gadmin-samba I should have just quietly walked on by ;) 

**(1) Make sure the following file exists: **
>  /usr/share/samba/smb.conf**(2) Make a backup of your current smb.conf**
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.confMOD 
```**(3) Restore a factory fresh one:**
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/ 
```**(4) Correct one mistake in the new one:**
Find the line:
> encrypt passwords = falseand change it to:
> encrypt passwords = [COLOR=Blue]**true**[/COLOR]**(5) Restart some services**
```
sudo service smbd restart
``````
sudo service nmbd restart
```**[6] Don't ever use gadmin-samba again**

**[7] Run the following command and post the output:**
```
smbtree
```Oh, and BTW what are the permissions on the target shared folder:
```
ls -dl /home/david/Music
```

---

### Post by davidtheo on 2011-11-16
Hi Morbius1

I did un-install gadmin-samba if that helps :(


```

david@ubuntu:/usr/share/samba$ smbtree
Enter david's password: 
david@ubuntu:/usr/share/samba$ ls -dl /home/david/Music
drwxrwxrwx 2 david sambashare 4096 2011-11-15 17:32 /home/david/Music
david@ubuntu:/usr/share/samba$ 

```

---

### Post by Morbius1 on 2011-11-16
Did you do anything with the firewall on Ubuntu? If you did, disable it please.

---

### Post by davidtheo on 2011-11-16
I have not done anything to the firewall, how to disable it?

---

### Post by Morbius1 on 2011-11-16
Let's see if samba itself is working properly. From the Ubuntu machine run the following command and see if it lists your shares:
```
nautilus smb://192.168.0.100
```
*[COLOR=Blue]Change 192.168.0.100 to the ip address of your Ubuntu machine.[/COLOR]*

---

### Post by Morbius1 on 2011-11-16
I have to leave for bit so in the interim:

If Ubuntu can see it's own shares by using an ip address then samba seems to be working. Your shares require authentication because you didn't create guest accessible shares in Nautilus but that's another problem.

See if you can connect from the Windows machine by ip address to see if Windows has some kind of problems with it.

If all that works and you want to go back to browsing for the share instead of accessing it by ip address make one adjustment to your smb.conf file - hopefully this is the last:

Add the following line to the [global] section of smb.conf:
```
name resolve order = bcast host lmhosts wins
```Then restart samba:
```
sudo service smbd restart
```Wait a few minutes - seriously. Everytime samba is restarted the network has a fit and things need to settle down before browsing can work.

---

### Post by davidtheo on 2011-11-16
> **Morbius1 said:**
> Let's see if samba itself is working properly. From the Ubuntu machine run the following command and see if it lists your shares:
```
nautilus smb://192.168.0.100
```*[COLOR=Blue]Change 192.168.0.100 to the ip address of your Ubuntu machine.[/COLOR]*

sorry about the late reply I had to go into town.

I am getting this error

                                 Error: Failed to retrieve share list from server 
 Please select another viewer and try again.


windows can not access the IP address. If I enter the IP address into IE I get the default apache2 web page.

---

### Post by davidtheo on 2011-11-16
> **Morbius1 said:**
> 
Add the following line to the [global] section of smb.conf:
```
name resolve order = bcast host lmhosts wins
```Then restart samba:
```
sudo service smbd restart
```

Wait a few minutes - seriously. Everytime samba is restarted the network has a fit and things need to settle down before browsing can work.


Still does not work :mad: Maybe Windows 7 does not like sharing with Ubuntu ;)

---

### Post by Morbius1 on 2011-11-16
Don't take this the wrong way but at the moment I don't care if Win7 cannot access your Linux machine. I'm trying to figure out why your Ubuntu machine cannot view it's own shares by ip address. If you can't see your own shares then there's no hope a remote machine will either. Fix one and we might fix the other.

This is probably a rat hole but I need to see more output please:

Install an app:
```
sudo apt-get install nmap
```Then run the following command with Ubuntu's ip address:
```
sudo nmap -sS -sU -T4 192.168.0.100
```You need to get an output that has these ports open:
PORT     STATE         SERVICE
> 139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm

---

### Post by davidtheo on 2011-11-16
> **Morbius1 said:**
> Don't take this the wrong way but at the moment I don't care if Win7 cannot access your Linux machine. I'm trying to figure out why your Ubuntu machine cannot view it's own shares by ip address. If you can't see your own shares then there's no hope a remote machine will either. Fix one and we might fix the other.

This is probably a rat hole but I need to see more output please:

Install an app:
```
sudo apt-get install nmap
```Then run the following command with Ubuntu's ip address:
```
sudo nmap -sS -sU -T4 192.168.0.100
```You need to get an output that has these ports open:
PORT     STATE         SERVICE

No problem

```

david@ubuntu:/etc/samba$ sudo nmap -sS -sU -T4 192.168.1.4

Starting Nmap 5.21 ( http://nmap.org ) at 2011-11-16 15:18 GMT
Nmap scan report for 192.168.1.4
Host is up (0.0000040s latency).
Not shown: 1995 closed ports
PORT     STATE         SERVICE
80/tcp   open          http
68/udp   open|filtered dhcpc
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.40 seconds


```

---

### Post by Morbius1 on 2011-11-16
Turn off your firewall:
```
sudo ufw disable
```
Then try to access your linux share by ip address again.

---

### Post by davidtheo on 2011-11-16
> **Morbius1 said:**
> Turn off your firewall:
```
sudo ufw disable
```Then try to access your linux share by ip address again.

```
david@ubuntu:~$ sudo ufw disable
Firewall stopped and disabled on system startup
david@ubuntu:~$ sudo nmap -sS -sU -T4 192.168.1.4

Starting Nmap 5.21 ( http://nmap.org ) at 2011-11-16 15:41 GMT
Nmap scan report for 192.168.1.4
Host is up (0.0000040s latency).
Not shown: 1995 closed ports
PORT     STATE         SERVICE
80/tcp   open          http
68/udp   open|filtered dhcpc
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.32 seconds
david@ubuntu:~$ nautilus smb://192.168.1.4
```

Error: Failed to retrieve share list from server
Please select another viewer and try again.

I also did a re-start and got the same

---

### Post by Morbius1 on 2011-11-16
Unless you are using firestarter or ever did use firestarter I don't know why 445 and 139 are being blocked. You're not using apparmour or anything like that re you?

---

### Post by davidtheo on 2011-11-16
> **Morbius1 said:**
> Unless you are using firestarter or ever did use firestarter I don't know why 445 and 139 are being blocked. You're not using apparmour or anything like that re you?


I donot know what they are, I just installed Ubuntu 2 days ago for web development work using the Zend Framework. It is dual booting on a windows 7 system but I did not think that would have anything to do with it. 

All I have instilled is
Apache2
PHP5
Mysql
phpmysqladmin
Zend framwork
PHPunit
ant
xdebug
Pear
skype
and Samba

---

### Post by Morbius1 on 2011-11-16
You made a reference to apache before and I ignored it. I'm not familiar with how it operates to know if it's what's in the way. I'll need to do some research on this I'm afraid. I would think that they would work independently but I'm just not sure.

You might want to do a search on apache and samba.

---

### Post by davidtheo on 2011-11-16
ok will do that

Thanks for your help anyway

---


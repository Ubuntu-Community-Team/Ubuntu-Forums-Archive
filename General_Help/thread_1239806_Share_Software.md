---
title: "Share Software"
date: 2009-08-13
forum: General Help
---

### Post by mthalis on 2009-08-13
I installed Ubuntu 9.04 several machines, I installed software these machines, normally I go to each machine and download software and install them, It wastes my brand with. Is their any way to download software once and share them each computer.

---

### Post by DeMus on 2009-08-13
> **mthalis said:**
> I installed Ubuntu 9.04 several machines, I installed software these machines, normally I go to each machine and download software and install them, It wastes my brand with. Is their any way to download software once and share them each computer.

When you have more than 1 computer you probably also have a network. Share a folder where you place all the downloaded software in and connect to this folder from your other machines.
If not, burn the stuff on a (rewritable) CD or DVD so that you can add new software later. Use this disc to install the programs on the other machines.

---

### Post by doorknob60 on 2009-08-13
I use Arch so I can't verify this right now, but after installing stuff look in /var/cache/apt/archives and the deb files should be there. You can use a flash drive or whatever to get them. Don't forget about dependencies (it can grab those off the internet if you don't copy them over, but that takes away form the point of this).

---

### Post by mthalis on 2009-08-13
I want to do it without copying to flash or burn CD/DVD because software list always update(increase) so more details need.

---

### Post by cariboo on 2009-08-13
Have a look at apt-cacher it will do what you want to do. Apt-cacher is in the repositories. You can also just clink the link.

[apt://apt-cacher](apt://apt-cacher)

---

### Post by mthalis on 2009-08-13
Can you explain more?

---

### Post by ryanhaigh on 2009-08-13
If your only doing this once or twice copying all the debs from /var/cache/apt/archives to the same location on each machine will probably be enough. If you want something more powerful look into apt-proxy, approx or apt-cacher

[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy) (apparently unstable now)
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)
[http://ubuntu-tutorials.com/2007/10/03/saving-bandwidth-with-apt-cacher-revisited/](http://ubuntu-tutorials.com/2007/10/03/saving-bandwidth-with-apt-cacher-revisited/)
[http://lists.netisland.net/archives/plug/plug-2008-05/msg00038.html](http://lists.netisland.net/archives/plug/plug-2008-05/msg00038.html)

---

### Post by rhcm123 on 2009-08-13
> **mthalis said:**
> I want to do it without copying to flash or burn CD/DVD because software list always update(increase) so more details need.

if this user is right:
> **doorknob60 said:**
> ...but after installing stuff look in /var/cache/apt/archives and the deb files should be there. 

You will have to make a samba share of this directory. Do this on the software server:
```
sudo apt-get install samba
```

Then, backup the default config with this (good practice):
```
cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
```

Then, modify /etc/samba/smb.conf to look like this (fill the fields to your needs:
```
# CONFIG FILE FOR SAMBA
# WRITTEN BY USSR
# LAST MODIFIED 12 APRIL 2009

# Global parameters
[global]
	log file = /var/log/samba/log.%m
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	map to guest = Bad User
	wins support = true
	dns proxy = No
	netbios name = NETBIOS HOSTNAME
	server string = SMB system [software]
	client lanman auth = No
	client plaintext auth = No
	lanman auth = No
	default = Share
	local master = Yes
	workgroup = YOUR NETBIOS WORKGROUP
	os level = 20
	security = user
	preferred master = no
	max log size = 50
	printing = cups
	printcap name = cups
	use client driver = yes
	guest account = nobody
	load printers = yes
	interfaces = eth0

# share CONFIGS
[share]
	browseable = yes
	read only = No
	writeable = yes
	path = /var/cache/apt/archives (THIS SHOULD BE RIGHT)
	create mask = 0700
	comment = Main share directory on <SERVER NAME>
	directory mask = 0700
	valid users = nobody (YOU CAN SET OTHERS IF YOU SO DESIRE)

```


You will need a user to login with. Although samba requires the user to exist as a system user, the user's SAMBA password is set seperatley from it's UNIX password. (if you get into this you can configure syncing), and the UNIX user does not have to have login priviliges. I prefer nobody, an unpriviliged system user, for this task, as it can access properly chmod'd files, but has no other priviliges and is very secure. Just make sure the documents are chmod'd ***4, so that nobody can read them. Set the SAMBA password with this:
```
smbpasswd -a nobody
```

Then, on a client machine, add this line to the /etc/fstab:
```
//(SERVER IP)/share   /media/share    smbfs   credentials=/home/YOURUSERNAME/.smb,user,owner,umask=777       0       0
```

then, edit this file /home/YOURUSERNAME/.smb to have this;
```
username=nobody
password=YOURPASSWORD
```

then, run this command, which will setup the mount point and secure the password:
```
cd && chmod 400 ./.smb && sudo apt-get install smbfs && sudo mkdir /media/share
```

to finally mount the share, run this:
```
sudo mount -a
```

a disk called share should appear in nautilus.

---


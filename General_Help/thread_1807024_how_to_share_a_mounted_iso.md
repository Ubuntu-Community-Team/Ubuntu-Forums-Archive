---
title: "how to share a mounted iso"
date: 2011-07-18
forum: General Help
---

### Post by NeoReaper on 2011-07-18
im having trouble sharing a mounted iso in narty.  i have mounty installed which is what i use to mount my iso's with and i attempted to share the folder it creates in my home folder over the network to a windows based machine with no luck.  any ideas?

---

### Post by Cybie257 on 2011-07-18
I believe it has something to do with the fact the a mounted ISO is not a valid filesystem, therefore will not be able to be shared. I could be wrong, but I wanted to reply with another option that might work out better for you since you won't be needing to write to the ISO (which is not usually possible), so this might work for you...

If you want to share the contents with a windows computer through a network, I would suggest a much easier method like sharing the folder that the ISO sits in and mounting the ISO via windows with something like Daemon Tools or some other ISO mounter for Windows.

-Cybie

EDIT/ADD: And because an ISO is only mountable as a Read Only, you 'should' be able to mount it on multiple computers at the same time through the network...

---

### Post by Morbius1 on 2011-07-18
Never used mounty so what are the permissions of the mount point:

```
ls -al /path/to/mount/point
```

---

### Post by NeoReaper on 2011-07-19
dr-xr-xr-x   1 root     root    

i know that i can share the iso and mount it within windows using daemon tools but i prefer not installing any software on the computer to do it.

---

### Post by Morbius1 on 2011-07-19
> i have mounty installed which is what i use to mount my iso's with and i  attempted to share the folder it creates in my home folder over the  network to a windows based machine with no luck.  any ideas?Is the problem that you cannot share whatever the mount point is on Linux?

How are you trying to share it - from Nautilus?

Or is the problem you can not access it from Windows when you do share it.?

By the way you did not post what I asked for. I wanted to know the permissions and the mount point.

---

### Post by NeoReaper on 2011-07-19
when i share the mount point the icon does become a shared folder icon but i have no access to it from my windows based machine.  

im sharing it through nautilus by right clicking and choosing sharing options.

so i guess that means the problem is that i have no access to it from windows, i have no other linux machine to test the share with but if i try to access my linux machine by clicking on network from nautilus it still doesnt show the share that im looking for.  all my other shares work.

sorry, i guess i didnt understand ur question.  mounty appears to mount it with read/write according to what the mount command states and the mount point is a folder it seems to create dynamically based on disc label in my home folder.

---

### Post by Morbius1 on 2011-07-19
Please post the output of the following commands and I'll figure it out myself:

```
testparm -s
```
```
net usershare info --long
```

---

### Post by NeoReaper on 2011-07-19
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[raulduke]"
Processing section "[Desktop]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = MSHOME
	server string = %h server (Samba, Ubuntu)
	obey pam restrictions = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	printcap name = cups
	dns proxy = No
	usershare owner only = No
	panic action = /usr/share/samba/panic-action %d
	invalid users = root

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[raulduke]
	path = /home/raulduke
	read only = No
	guest ok = Yes

[Desktop]
	path = /home/raulduke/Desktop
	read only = No
	guest ok = Yes


net usershare info --long
[office]
path=/home/raulduke/office_disc1_iso
comment=
usershare_acl=Everyone:R,SOAP\raulduke:F,
guest_ok=n

[temp]
path=/home/raulduke/Desktop/temp
comment=
usershare_acl=Everyone:F,
guest_ok=n


sorry if the info i gave you was wrong before, still learning more about linux everyday.

---

### Post by Morbius1 on 2011-07-19
Try this:

Open nautilus and go to /home/raulduke/office_disc1_iso and "un-share" it. Just reverse the steps you used to share it in the first place.

Then from Windows access the "raulduke" share itself and drill down to "office_disc1_iso". Does that work?

---

### Post by NeoReaper on 2011-07-19
yeah, i thought about doing that also, it doesnt work.  all my other folders in my home directory are listed except that one for some reason.

---

### Post by Morbius1 on 2011-07-20
I installed the app in a VBox install of linux and I have the same problem. It appears it's a fuse thing.

Anyway, I have an alternative that does not depend on fuse that I have just installed and have shared the mounted iso across the lan:

```
sudo apt-get install gmountiso
```It's a mini - gui app that will find and mount the iso image anywhere you want.

What I did was create a generic mount point: /media/ISO
Then set up a generic samba share:
```
[ISO Mount]
path = /media/ISO
guest ok = Yes
```Restarted samba

It's a little awkward on the client end of things. The share is visible even if you don't have an iso mounted on the server so it will be empty. If the server then mounts the iso the client will still see it as empty. The client will have to unmount the share and then remount it.

It's the best I got at the moment. Give it a shot and tell me is you see any other problems.

---

### Post by NeoReaper on 2011-07-20
i used this app when i was running the older versions of ubuntu, i just figured since narty has tray tool apps such as mounty i would try to take advantage of it.  i guess if this is the only solution ill learn to live with it.  thanks for your help, if you happen to have any other ideas, im all ears.

---

### Post by smurphy_it on 2011-07-20
Interesting things to note:

From NeoReaper Samba's config:
net usershare info --long
[office]
guest_ok=n

From Morbius1's setup with gmountiso
[ISO Mount]
path = /media/ISO
guest ok = Yes


NeoReaper:  Did you attempt to change your ISO samba share to allow guests ?

---

### Post by NeoReaper on 2011-07-21
hmm thats interesting, how do i edit that setting.  i dont see it in my /etc/samba/smb.conf but when i type "net usershare info", that comes up

---


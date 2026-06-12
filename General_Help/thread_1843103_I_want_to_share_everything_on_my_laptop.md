---
title: "I want to share everything on my laptop"
date: 2011-09-12
forum: General Help
---

### Post by rmcellig on 2011-09-12
I have a HP laptop that I use for testing and learning about Ubuntu and Linux. I would like to be able to share my entire HD as well as every USB device that is plugged into it so that I can access it from anywhere on my LAN. Is this possible and how can I do this?

I have the Samba app installed but for some reason just trying to share a test folder doesn't work. None of my other computers (a mixture of Macs, Windows machines and another Linux machine, can't see that HP laptop. What am I missing and is there some code that I can use to post back the results to this thread? I am using Ubuntu 11.04.

---

### Post by Habitual on 2011-09-12
if, If, IF this is not a internet-facing machine, you can run this as root in the root directory of the system you will to have access to...
Terminal or ssh > 
On the laptop
```

sudo su -
cd /
python -c "import SimpleHTTPServer;SimpleHTTPServer.test()"
```

Then connect to that machine's IP:8000 using your browser from any other machine on your network.

Ctrl+C in terminal to stop the process (kill the python server)

---

### Post by rmcellig on 2011-09-13
The laptop has Internet access through an Ethernet cable, not wireless. If there are security issues sharing the entire laptop, how can I get samba to work to share specific folders? Is there a cli command I can use and post back the rehire here? I'm not sure why I am having trouble sharing on this laptop. Maybe I am doing something wrong when it comes to sharing folders? I would Luke to make this process as easy as possible so that sharing folders is as easy if not easier than sharing on a mac using OS X.

---

### Post by Habitual on 2011-09-13
You should be ok with what I gave you.
Granted, the files can NOT be updated using this method on the laptop. Just gotten/viewed.

---

### Post by Morbius1 on 2011-09-13
If you also want to pursue Samba then some of the commands that will let people know how you are set up are these:
```
testparm -s
net usershare info --long
smbtree

```

---

### Post by rmcellig on 2011-09-13
thanks Morbius1

I know my previous post was confusing/ I guess I am just trying to find the easiest way for me to have access to my test laptop from anywhere in the house regardless of what computer I am using (mac, pc or linux machines).

home@testhplaptop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
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
home@testhplaptop:~$ 

home@testhplaptop:~$ net usershare info --long
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
home@testhplaptop:~$ 


home@testhplaptop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
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
home@testhplaptop:~$ clear

home@testhplaptop:~$ net usershare info --long
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
home@testhplaptop:~$ clear

home@testhplaptop:~$ smbtree
Enter home's password: 
WORKGROUP
	\\MACINTOSH      		home
		\\MACINTOSH\mosaic         	Mosaic
		\\MACINTOSH\home's public folder	home's Public Folder
		\\MACINTOSH\USB4           	User Home Directories
		\\MACINTOSH\USB1           	User Home Directories
		\\MACINTOSH\Dropbox        	User Home Directories
		\\MACINTOSH\80GB Drive     	User Home Directories
		\\MACINTOSH\Main drive     	User Home Directories
		\\MACINTOSH\home           	home
		\\MACINTOSH\IPC$           	IPC Service (home&#8217;s Power Mac G4)
	\\IMAC           		imac
anonymous failed session setup with NT_STATUS_PIPE_BROKEN
HOME
	\\NICOLE         		Nicole's computer
		\\NICOLE\C$             	Default share
		\\NICOLE\ADMIN$         	Remote Admin
		\\NICOLE\F$             	Default share
		\\NICOLE\SharedDocs     	
		\\NICOLE\print$         	Printer Drivers
		\\NICOLE\IPC$           	Remote IPC
home@testhplaptop:~$

---

### Post by Morbius1 on 2011-09-13
Samba is either not installed or not started.

Find the status:
```
sudo service smbd status
```If it's not started start it:
```
sudo service smbd start
```If it is started restart it:
```
sudo service smbd restart
```Then run testparm -s again and see if this error is still there:
> ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist

---

### Post by rmcellig on 2011-09-13
home@testhplaptop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
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
home@testhplaptop:~$ clear

home@testhplaptop:~$ net usershare info --long
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
home@testhplaptop:~$ clear

















home@testhplaptop:~$ smbtree
Enter home's password: 
WORKGROUP
	\\MACINTOSH      		home
		\\MACINTOSH\mosaic         	Mosaic
		\\MACINTOSH\home's public folder	home's Public Folder
		\\MACINTOSH\USB4           	User Home Directories
		\\MACINTOSH\USB1           	User Home Directories
		\\MACINTOSH\Dropbox        	User Home Directories
		\\MACINTOSH\80GB Drive     	User Home Directories
		\\MACINTOSH\Main drive     	User Home Directories
		\\MACINTOSH\home           	home
		\\MACINTOSH\IPC$           	IPC Service (home&#8217;s Power Mac G4)
	\\IMAC           		imac
anonymous failed session setup with NT_STATUS_PIPE_BROKEN
HOME
	\\NICOLE         		Nicole's computer
		\\NICOLE\C$             	Default share
		\\NICOLE\ADMIN$         	Remote Admin
		\\NICOLE\F$             	Default share
		\\NICOLE\SharedDocs     	
		\\NICOLE\print$         	Printer Drivers
		\\NICOLE\IPC$           	Remote IPC
home@testhplaptop:~$ clear

home@testhplaptop:~$ sudo service smbd status
[sudo] password for home: 
smbd: unrecognized service
home@testhplaptop:~$ sudo service smbd start
smbd: unrecognized service
home@testhplaptop:~$ sudo service smbd restart
smbd: unrecognized service
home@testhplaptop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
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
home@testhplaptop:~$

---

### Post by Morbius1 on 2011-09-13
```
sudo apt-get install samba
sudo apt-get install samba-common
sudo apt-get install samba-common-bin
sudo apt-get install nautilus-share
```

---

### Post by rmcellig on 2011-09-13
done. do you need me to post anything back to this thread? what do i do next?

---

### Post by lykwydchykyn on 2011-09-13
Honestly, the easiest and most secure way to do this is to install openssh-server on the Linux machine and access it by ssh.

On windows you can install WinSCP which will give you access to the machine.  I assume OSX has something similar, I'm not familiar enough with it to know.

It's a lot simpler than mucking about with all that samba mess.

---

### Post by Morbius1 on 2011-09-13
Restart all samba services in this order:
```
sudo service smbd restart
sudo service nmbd restart
```

---

### Post by rmcellig on 2011-09-13
lykwydchykyn

SSH is totally new to me although I have heard of it. First I want to nail down how to use Samba and then I am going to dive into SSH. Are there any good videos on youtube you would recommend me watching?

---

### Post by rmcellig on 2011-09-13
home@testhplaptop:~$ sudo service smbd restart
[sudo] password for home: 
smbd start/running, process 2023
home@testhplaptop:~$ sudo service nmbd restart
nmbd start/running, process 2035
home@testhplaptop:~$

---

### Post by Morbius1 on 2011-09-13
When you run testparm -s do you still get the following error:
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist

---

### Post by rmcellig on 2011-09-13
home@testhplaptop:~$ testparm -s
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
home@testhplaptop:~$

---

### Post by Morbius1 on 2011-09-13
Open Nautilus, right click a folder you own - say ... Documents, Select "Sharing Options", mark all the boxes, and select "Create Share".

Now run the following command just to make sure there are no errors:
```
net usershare info --long
```If there aren't any then access the share from your own box:
```
nautilus smb://testhplaptop
```If you get any type of error at all access it by ip address:
```
nautilus smb://192.168.0.100
```Change 192.168.0.100 to the ip address for your machine.

If all that works then try to access it from another machine.

---

### Post by rmcellig on 2011-09-13
I can see the shared folder from my Mac and Windows machines but for example when I try to copy a file to the Desktop folder through the shared home folder, On my Mac i am prompted for a password. my user name/password is home and it doesn't work. When I try to do the same thing on my win 7 machine, I get permission denied. What should I do now?

---

### Post by Morbius1 on 2011-09-13
Did you create a guest share or one that requires authentication?

If you created one that does not allow guest access then you have to create a user on the server that corresponds to the remote user then add him to the samba database. If you just want to see if you can connect to the laptop using your own user name:
```
sudo smbpasswd -a home
```

---

### Post by rmcellig on 2011-09-13
home@testhplaptop:~$ nautilus smb://testhplaptop
home@testhplaptop:~$ sudo smbpasswd -a home
[sudo] password for home: 
New SMB password:
Retype new SMB password:
home@testhplaptop:~$ 


does this now allow me to connect with user home as well as the new smb password from another computer,

So i have to create a new guest account if i configured the shared folder for guest access? makes sense.

---

### Post by Morbius1 on 2011-09-13
>  does this now allow me to connect with user home as well as the new smb password from another computer,Try it and find out.
> So i have to create a new guest account if i configured the shared folder for guest access?Nope. If you created a guest share no one will be prompted for a password. [ Actually what happens is the remote user will be converted to a guest account that's already set up for you ] .

If you did indeed create a guest share and you are prompted for a password then something isn't right. Please post the output of the following:
```
net usershare info --long
```

---

### Post by rmcellig on 2011-09-13
home@testhplaptop:~$ net usershare info --long
[homelaptop]
path=/home/home
comment=
usershare_acl=Everyone:F,
guest_ok=y

home@testhplaptop:~$

---

### Post by rmcellig on 2011-09-13
I tried accessing my Ubuntu Home share from my Mac and it was totally successful. You will see from the attached that I had an option to connect with my user/password credentials. That worked fine and gave me full access to my Ubuntu Home directory on my laptop.

When I tried on my other HP laptop, I was not prompted for my user/password credentials. I would assume that what I saw were the contents of my Ubuntu home directory as gust and not as user Home therefore I had no permissions to do anything like copy a file to the Home folder or any of the other sub folders. Do I have to do something on my other HP in order for this to work?

Next, I will try in Windows 7 to access my Ubuntu Home share and post back with the results. Windows 7 worked great. No problems at all. I can copy files to any of the home directories just fine. What puzzled me was that I didn't have to enter a user name/password like I had to on my Mac.

---

### Post by Morbius1 on 2011-09-13
Didn't see your last post.

OK, And what are it's permissions:
```
ls -al /home
```

---

### Post by rmcellig on 2011-09-13
home@testhplaptop:~$ ls -al /home
total 12
drwxr-xr-x  3 root root 4096 2011-09-13 10:49 .
drwxr-xr-x 22 root root 4096 2011-09-13 10:54 ..
drwxrwxrwx 32 home home 4096 2011-09-13 15:34 home
home@testhplaptop:~$

---

### Post by rmcellig on 2011-09-13
Everything works fine now on all computers. I disabled guest access so you have to put in the login credentials. Tried it and it works!! Thanks for all of your help! I will post back if I run into any issues but for now I will mark this thread solved.

---

### Post by Morbius1 on 2011-09-13
You created a guest share and your Linux permissions are wide open so all remote users will be able to add to or remove existing files from that share without being prompted for credentials. What you may not be able to do is actually edit a given file within that share since the permissions on that file will not permit it.

By the way, I wouldn't take that laptop outside the safety of your home lan as you are allowing anyone to access it without permission.
[COLOR=Blue]**EDIT on my last remark:**[/COLOR] It looks like you removed that problem by creating a private share.

---

### Post by rmcellig on 2011-09-13
I have an external usb drive hooked up to my laptop. Is it posible to share that drive or are there any issues?

---

### Post by cryptotheslow on 2011-09-13
Anything is possible.

Your external USB drive will most likely be mounted into the filesystem on the laptop at:

/media/externalUSB

That "externalUSB" I made up but it should be mounted to a directory under /media - the directory name will be the partition name on the drive or if no name something a bit random. Take a browse to there and see what you find.

Just as you did with your other directory, you should be able to share it from within Nautilus - although also take a look at the Permission tab while you are in there and make sure it has Read & Write for everyone - I can't remember of the top of my head what the default permissions are for a mounted USB drive. (No doubt someone will be a long to remind me shortly!) :D

Edit to add - when posting a follow-up question on a thread it is best to use the thread tools to remove the "Solved" flag - so people know it still needs attention ;)

---

### Post by rmcellig on 2011-09-13
Hi Morbius1,

So, now that I have everything working, could you please summarize for me the steps involved in implementing sharing in Ubuntu before I get to the point of right clicking on an item to share it.

Thanks a million!! I will use this when I have to implement sharing on a new installation, preferably friends of mine switching from Windows to Ubuntu :).

---

### Post by Morbius1 on 2011-09-14
[1] Steps to enable Samba File Sharing on Ubuntu

* Do not read or implement any HowTo's on setting up Samba ( except this one, of course ;) )
* Do not enable ( at least in the beginning ) any firewalls
* Open Nautilus
* Right click a folder you own say ... Documents
* Select "Sharing Options"

At this point if you don't have Samba installed it will ask you if you want to install it ( If I remember correctly it calls it "Windows Networking" )

* Select "Share this folder", "Allow others to create and delete..", "Guest Access".
* Select "Create Share"

It will ask you if you want it to modify permissions - you do.
Done

No need to restart any services.
No need to create any samba users or passwords.
No need to change permissions on the target folder.

To verify that a share has been created:
```
net usershare info --long
```To verify if someone on the network can see it and check for errors:
```
smbtree
```That should list all the workgroups on your LAN and all the hosts on those workgroups and all the shares on those hosts - including the one you just created above. 

If you run into problems post the output of "smbtree", "net usershare info --long", and the following:
```
testparm -s
hostname
```[2]          I have an external usb drive hooked up to my laptop. Is it posible to share that drive or are there any issues?

Yes, there might be. If the USB drive is formatted in NTFS or FAT32 it will mount with you as owner and with access granted only to you. You will not be able to share it in the traditional sense since none of the remote users are you. There are a couple of ways around this problem - one of which is making the share private and accessible only to you but you're stretching the definition of sharing. There are other ways to make it accessible to others besides you and that can be done withing Samba itself.

[3] Final note
> I will use this when I have to implement sharing on a new installation,  preferably friends of mine switching from Windows to UbuntuI wouldn't draw any broad conclusions from your Samba experience since I consider your Samba configuration broke. It appears to be working just the opposite of the way it should. A guest share should never prompt the remote user for credentials. There's something going on with your install that I haven't quite figured out yet. You had to install of lot of packages that should have been there by default so something seems amiss. My current theory is that you have encrypted your home directory but based on your description I'm not sure that explains all your symptoms.

When I have time I'll set up a VM in VBox , encrypt the home directory, and see if I can duplicate your symptoms. I haven't had any experience with an encrypted directory to know how Samba deals with it so this is a good excuse to find out.

---

### Post by rmcellig on 2011-09-14
Thanks! By the way, I keep my password in the keychain or whatever you call it that allows you to store passwords. This way I don't have to type in my password every time.

---

### Post by Morbius1 on 2011-09-14
I'm going to guess that you are referring to the keychain in OSX since Windows doesn't have one ( that I know of ) and it makes no sense to have it on the Ubuntu machine that has the share.

---

### Post by rmcellig on 2011-09-14
that's right.

---


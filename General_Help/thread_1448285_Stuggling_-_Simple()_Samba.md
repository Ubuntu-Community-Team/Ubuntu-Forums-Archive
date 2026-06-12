---
title: "Stuggling - Simple(?) Samba"
date: 2010-04-06
forum: General Help
---

### Post by Quarkrad on 2010-04-06
Newbie -  I would like to share files between two home PCs (using Samba?) but am struggling.  I have set up Samba on both PCs and set up sharing on a folder A on PC1.  Via Nautilus/ Networking I can see PC1 and navigate to folder A.  However,when I double clip to open it I get a window asking me for a password.  My username: is already filed out in the window so is Domain: WORKGROUP -the Password: box is empty.  I have other options - Forget password immediately, Remember password until you logout and Remember forever.

I do not remember setting up this windows domain (perhaps I did some time ago setting up a shared printer).  Problem is, I do not know what the password is (for the Domain: Workgroup).  I have tried every password I use - including the password I set up on PC 1 when I allowed sharing for folder A.

Can I find out what the password is or delete the networking and start again from scratch?  What do I do?

---

### Post by Morbius1 on 2010-04-06
Need more information please:

(1) What operating systems are on these machines:

(2) What method of sharing are you using? 

There are two completely different methods. If you post the output of the following commands we can determine what method you are using and how you're using it:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**
Type [B]testparm -s
[/B]
(3) When you created the share did you want it to ask for a username and password or did you create it so anyone can access it?

---

### Post by Quarkrad on 2010-04-06
Thanks for your reply.

1.  Both PCs are running Ubuntu 9.10 although on PC1 (lets call this the server as it has the printer connected to it) the folder I want to share is on a NTFS partition.

2.  Not sure - newbie!  I have set up Samba on both PCs

3.  This is the output from PC 2.  I actually use PC2 and it is on this machine that I am struggling with the password.

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	encrypt passwords = No
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


This is the output from PC1

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Home Files]"
Processing section "[Home Files]"
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
	usershare owner only = No
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

[Home Files]
	path = /media/Home Files
	read only = No
	guest ok = Yes

**Home Files** is the folder on PC1 that I want to share with from PC2.

---

### Post by Morbius1 on 2010-04-06
> [Home Files]
    path = /media/Home Files
    read only = No
    guest ok = YesI take it this is pointing to an NTFS partition? Lord I hate spaces in directory names almost as much as linux does.

The easiest way to fix this is to add one line to that share definition but you need to figure out who owns the mount point.

If you do a **ls -dl /media/"Home Files"**

and it comes back with something like this:

> drwxr-xr-x 1 [COLOR=Blue]morbius[/COLOR] plugdevThen you would add the following line: ```
force user = morbius
``` to the share definition so that it looks like this:
> [Home Files]
     path = /media/Home Files
     read only = No
     guest ok = Yes
[COLOR=Blue]force user = morbius[/COLOR]Then restart samba: **sudo service samba restart**

If it comes back as being owned by root then we've got more work to do.

---

### Post by Quarkrad on 2010-04-06
I'm **very** sorry but I have to leave the PC for some time - I really appreciate your support.  Is it OK if we continue tomorrow?

---

### Post by Quarkrad on 2010-04-07
You are right - there is more work to do!   The out put of ls -dl /media/"Home Files" is:

drwxrwxrwx 1 root root 8192 2010-03-23 18:39 /media/Home Files

The user names of each PC is:

PC1 (where the folder sits) is lizubuntu
PC2 (where I'm trying to access from) is dadubuntu

---

### Post by Morbius1 on 2010-04-07
Actually that should work.
> [Home Files]
    path = /media/Home Files
    read only = No
    guest ok = Yes                      You've created a writeable share that allows everyone to access it.
>  drwxrwxrwx 1 root root 8192 2010-03-23 18:39 /media/Home FilesThe linux files permissions , although owned by root, is allowing read / write access to everyone.

Samba and Linux are in sync and nobody should be asking you for password.

Is the password prompt happening when you try to open "Home Files" or is it happening when you try to open the WORKGROUP or Machine Name level?


There is one other possibility. On PC2 which has the share you're trying to get to, you have one line in your smb.conf:
>      usershare owner only = NoThat's not there by default. You had to put it there yourself. That's used by Nautilus-share which is the alternate method of samba sharing. It could be that you have share definitions using both methods and gumming things up.

From PC2 did you not have any output from these commands:

**net usershare info**
[B]sudo net usershare info

[COLOR=Blue]EDIT: Sorry I'm confusing myself on PC! and PC2 - Run those commands from PC1.[/COLOR]
[/B]

---

### Post by Quarkrad on 2010-04-07
Here is the output from PC1

liz@lizubuntu:~$ **net usershare info**
[home]
path=/media/Home Files/Home
comment=
usershare_acl=Everyone:F,
guest_ok=n

liz@lizubuntu:~$ **sudo net usershare info**
liz@lizubuntu:~$ **testparm -s**
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Home Files]"
Processing section "[Home Files]"
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
	usershare owner only = No
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

[Home Files]
	path = /media/Home Files
	read only = No
	guest ok = Yes
liz@lizubuntu:~$

---

### Post by hugo007 on 2010-04-07
Did you add a smb user?
If not just open console and then type [FONT=Courier][SIZE=2]smbpasswd -a yourname[/SIZE][/FONT]
[FONT=Courier][SIZE=2]then it will ask you for a password[/SIZE][/FONT]
[FONT=Courier][SIZE=2]then its done[/SIZE][/FONT]
[FONT=Courier][SIZE=2]you can now use this to login on smb share[/SIZE][/FONT]

---

### Post by Quarkrad on 2010-04-07
Sorry to be stupid on this - Do I set up this user on PC1, PC2 or both?

---

### Post by Morbius1 on 2010-04-07
You don't need to add a samba user if you have a public share. You're allowing guests - no password required.

The problem is here:

Nautilus-share:
> liz@lizubuntu:~$ **net usershare info**
[home]
path=/media/Home Files/Home
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]guest_ok=n[/COLOR]Classic-share:
> [Home Files]
    path = /media/Home Files
    read only = No
  [COLOR=Blue]  guest ok = Yes[/COLOR]
liz@lizubuntu:~$     I assume you want this to be a public share so go into nautilus > /media/Home Files/Home and "unshare" it.

Then restart Samba: **sudo service samba restart**

---

### Post by Quarkrad on 2010-04-07
It works - I have access.  Thank you very much for your effort, much appreciated.

---

### Post by Quarkrad on 2010-04-07
Ah - too soon. I forgot to restart both machines and then test. Back to square 1'ish.

PC 1

Places - Network:-  I see a folder called Windows Network.  Double click Windows Network Folder:- in this folder there are two other folders called MS Home and Workgroup.  Inside the MS Home folder there is an icon that looks like an array of three hard drives stacked together on top of each other called YOUR-C7096BBDSB. If I were to double click on this (folder?) to open it I get the original window asking me for a password.  It i spe filed with my user name (Liz) and Domain (WORKGROUP) but the Password box is blank.  If I were to go back to the Workgroup folder that sits in Places - Network - Windows Network and double click on it I get the same password window.  

PC 2

The same as PC 1

---

### Post by Morbius1 on 2010-04-07
Based on your output only PC1 has any shares so trying to access shares on PC2 will not get you far.

Why not post the output of the following commands so we can stop calling them PC1 and PC2 and maybe if we're lucky we can get some error messages:

From both machines

Open **Terminal**
Type **smbtree**
Type **findsmb**

---

### Post by Quarkrad on 2010-04-07
Thank you.

From my machine, dadubuntu, 

dad@dadubuntu:~$ smbtree
Enter dad's password: 
Server requested plaintext password but 'client plaintext auth' is disabled
anonymous failed session setup with NT_STATUS_INVALID_PARAMETER
Server requested plaintext password but 'client plaintext auth' is disabled
anonymous failed session setup with NT_STATUS_INVALID_PARAMETER

dad@dadubuntu:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.4     DADUBUNTU     +[	WORKGROUP     ]


From lizubunu

liz@lizubuntu:~$ smbtree
Enter liz's password:
Server requested plaintext password but 'client plaintext auth' is disabled
anonymous failed session setup with NT_STATUS_INVALID_PARAMETER
Server requested plaintext password but 'client plaintext auth' is disabled
anonymous failed session setup with NT_STATUS_INVALID_PARAMETER 

liz@lizubuntu:~$ findsmb

                               *=DMB
                               +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION
---------------------------------------------------------------------
192.168.1.2     LIZUBUNTU      [WORKGROUP] [Unix] [Samba 3.4.0]
192.168.1.4     DADUBUNTU     +[    WORKGROUP     ] 


hope this helps.

---

### Post by Morbius1 on 2010-04-07
Try this:

On each machine

Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Add the following line to the [COLOR=Blue][global][/COLOR] section of smb.conf:
```
encrypt passwords = Yes
```Save smb.conf, exit gedit, and back in the Terminal type: **sudo service samba restart**

See if that works without resorting to a less than ideal solution.

---

### Post by Morbius1 on 2010-04-07
Wait. !!!  I Think I found it  :oops:
> 3.  This is the output from PC 2.  I actually use PC2 and it is on this machine that I am struggling with the password.

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
[COLOR=Blue]     encrypt passwords = No[/COLOR]
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
Open **Terminal**
Type **gksu gedit /etc/samba/smb.conf**

Put a # sign in front of that line so that it looks like this:
```
[COLOR=Blue] #encrypt passwords = No[/COLOR]
```Now save the file, exit gedit, and restart samba: **sudo service samba restart**

Look through the smb.conf file on the other machine and if it has that same line as "No" do the same thing as you did here.

---

### Post by Quarkrad on 2010-04-07
Magic - it works, even after rebooting.  It worked before I got your last post.  When I go Places - Network  I now see LIZUBUNTU and DADUBUNTU -  double clicking LIZUBUNTU I see two folders Home and Home Files.  I can double click Home Files and get in.  (Double clicking Home brings up that password window again. I might try your last post suggestion and see what happens).  Many thanks for your time, I really appreciate it.

note.  I'm hoping to upgrade both machines soon to 10.4 (after month end) - can you suggest an idiots guide for me to get this working again.  No doubt I can go through this thread again but there might be a better way for me.

---

### Post by Morbius1 on 2010-04-07
>  I can double click Home Files and get in.  (Double clicking Home brings up that password window againMake sure you still don't have the Nautilus-share enabled:
> The problem is here:

***Nautilus-share:***
     Quote:
                                                 liz@lizubuntu:~$ **net usershare info**
[home]
path=/media/Home Files/Home
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]guest_ok=n[/COLOR]                                 

*** Classic-share:***
     Quote:
                                                 [Home Files]
    path = /media/Home Files
    read only = No
  [COLOR=Blue]  guest ok = Yes[/COLOR]
liz@lizubuntu:~$                                 
I assume you want this to be a public share so go into nautilus > /media/Home Files/Home and "unshare" it.

Then restart Samba: **sudo service samba restart**

---


---
title: "SMB on 11.10?"
date: 2012-02-24
forum: General Help
---

### Post by exitlimit on 2012-02-24
Hey guys, I'm very new to Linux but learning extremely fast. But I'm gonna need a literal step by step tutorial in very discriptive text, and reasons why for each step as to HOW ON EARTH do I set up my Office Desktop machine running Ubuntu 11.10 (which is connected to my home router) and be able to use my Windows XP based wifi enabled laptop in the living room to access a sharing folder between the two computers?
 
I used to be able to do it all the time when I had XP on both machines simpy by Run Command. I'm sure the process is quite different with Linux to Windows.
 
I've searched everywhere and have tried SO much to try get this working and finding myself very frustrated. Can anyone help me with a DETAILED STEP-BY-STEP?

---

### Post by Morbius1 on 2012-02-24
I don't understand the question.

Are you trying to access a WinXP share?
Nautilus > Network 

Are you trying to access a Linux share from WinXP?

It's done almost exactly the same way you would create a "Simple Share" on WinXP:

From Nautilus:

Right click a folder you own say ... Documents
Select "Sharing Options"
[COLOR=Blue]*At this point if you don't have Samba installed it will ask you if you want to install it - you do.*[/COLOR]
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
[COLOR=Blue]*It will ask you if you want it to modify permissions - you do.*[/COLOR]
Done

If you run into problems with any of that we will need more information on how you are set up by posting the output of each of the following commands:

```
smbtree
testparm -s
net usershare info --long
```

---

### Post by exitlimit on 2012-02-24
Alright, now, I've decided to share my 'Public' folder from my Ubuntu desktop, it's all set-up as per your instruction and all went smooth. I had already previously installed Samba as per some other useless guide I was trying to understand (also, 2 glade packages were among that instruction, not sure what they're for).

Now - How do I access this 'Public' folder that's found on my Ubuntu 11.10 desktop from my Windows XP laptop in the next room? Is there something special I need to do on the Windows XP laptop in order to be able to access the Ubuntu Desktop 'Public' folder remotely?

---

### Post by Morbius1 on 2012-02-24
The same way you would access it if it were another WInXP machine. My Network Places is one way.

---

### Post by exitlimit on 2012-02-24
Can it also be done by typing something into the 'run' command option on the XP laptop (just out of curiosity)? And what's the difference, if so, between that and accessing it through 'My Network Places'?

---

### Post by Morbius1 on 2012-02-24
Yes the same way you would connect if it were a another WinXP machine:

Start > Run:

\\hostname
\\hostname\sharename
\\ipaddress
\\ipaddress\sharename

---

### Post by Derek Karpinski on 2012-02-24
if you want to map the network drive via Windows command line, you can execute:
 
```
net use Z: "[\\server\share]("file://\\server\share")" "Nickname"
```
 
change 'Z' to whatever drive you want your share mapped to
change 'Nickname' to whatever you want to name your mapped drive (optional)
 
Quotes are needed if there are spaces in the string, doesn't hurt if there's not though.
 
```
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.
C:\Users\dkarp>net use /?
The syntax of this command is:
NET USE
[devicename | *] [\\computername\sharename[\volume] [password | *]]
        [/USER:[domainname\]username]
        [/USER:[dotted domain name\]username]
        [/USER:[username@dotted domain name]
        [/SMARTCARD]
        [/SAVECRED]
        [[/DELETE] | [/PERSISTENT:{YES | NO}]]
NET USE {devicename | *} [password | *] /HOME
NET USE [/PERSISTENT:{YES | NO}]
```

---

### Post by exitlimit on 2012-02-24
> **Morbius1 said:**
> I don't understand the question.

Are you trying to access a WinXP share?
Nautilus > Network 

Are you trying to access a Linux share from WinXP?

It's done almost exactly the same way you would create a "Simple Share" on WinXP:

From Nautilus:

Right click a folder you own say ... Documents
Select "Sharing Options"
[COLOR=Blue]*At this point if you don't have Samba installed it will ask you if you want to install it - you do.*[/COLOR]
Select "Share this folder", "Allow others to create and delete..", "Guest Access".
Select "Create Share"
[COLOR=Blue]*It will ask you if you want it to modify permissions - you do.*[/COLOR]
Done

If you run into problems with any of that we will need more information on how you are set up by posting the output of each of the following commands:

```
smbtree
testparm -s
net usershare info --long
```
I can't seem to find the folder 'Public' when I enter paths into 'Add Network Place'. I tried a few different combinations, but still nothing, thought I was close once, what am I doing wrong?...
 
I tried:
[\\steve\public]("file://\\steve\public")
[\\steve]("file://\\steve") (hoping the public folder would have just appeared since I set up the folder for sharing)
[\\server\share\public]("file://\\server\share\public")
[\\server\public]("file://\\server\public") 
 
....nothing is working, so I'm sure there is something yet I'm not fully understanding.
 
Do I need to enter my actual COMPUTER NAME or something? I'm sure I'm really close.
 
However, here is the information you asked for:
 
[EMAIL="smsteve@steve-MS-6380:~$"]smsteve@steve-MS-6380:~$[/EMAIL] smbtree
Enter steve's password:
 
(Nothing happened after that) ^

[EMAIL="steve@steve-MS-6380:~$"]steve@steve-MS-6380:~$[/EMAIL] testparm -s
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

[EMAIL="steve@steve-MS-6380:~$"]steve@steve-MS-6380:~$[/EMAIL] net usershare info --long
[public]
path=/home/steve/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by Morbius1 on 2012-02-24
The smbtree command should list all the hosts and all the shares on those hosts and output error messages if something is wrong. Forgetting for a moment that it can't see the WinXP machine what's more interesting is that it can't see itself.

* My guess is that your firewall is messed up somewhere so turn it off and run smbtree again:
```
sudo ufw disable
```* Another possibility is that your samba services are not running. So check their status:
```
sudo service smbd status
sudo service nmbd status
```If they are not running start them:
```
sudo service smbd start
sudo service nmbd start
```* One last thing to do is to change the the priority of how netbios names are converted to ip addresses by doing this:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section - right under the workgroup line:
```
name resolve order = bcast host lmhosts wins
```Save the file and restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```*BTW*:
> I tried:
\\steve\public
\\steve (hoping the public folder would have just appeared since I set up the folder for sharing)
\\server\share\public
\\server\public 
It works the same way as if you were trying to access another WinXP machine:

```
\\steve-MS-6380\public
```OR
```
\\192.168.0.103\public
```

---

### Post by exitlimit on 2012-02-24
Alright, finally; on my XP laptop under 'Add Network Place Wizard' OR 'RUN COMMAND'  trying to access my UBUNTU desktop; "\\steve-MS-6380\public" prompted me for a username and password, but [COLOR=Red]either way the password doesn't seem to want to work[/COLOR] (the username/password box/window just flickers and does nothing, and the password entry stays highlighted).

**[COLOR=Red]1.[/COLOR]** Am I to assume the same password for my UBUNTU system is the same one I will use to connect or do I have yet to set one up with samba or something?

[COLOR=Red]**2.**[/COLOR] And what in my firewall (Firestarter) is causing zero recognition in this case? Is there another firewall package I can use to get around this issue?

Here is the new smbtree and soforth:

steve@steve-MS-6380:~$ smbtree
Enter steve's password: 
WORKGROUP
    \\STEVE-MS-6380          steve-MS-6380 server (Samba, Ubuntu)
        \\STEVE-MS-6380\public             
        \\STEVE-MS-6380\IPC$               IPC Service (steve-MS-6380 server (Samba, Ubuntu))
        \\STEVE-MS-6380\print$             Printer Drivers
steve@steve-MS-6380:~$ testparm -s
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
    name resolve order = bcast host lmhosts wins
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
steve@steve-MS-6380:~$ net usershare info --long
[public]
path=/home/steve/Public
comment=
usershare_acl=Everyone:F,
guest_ok=y

---

### Post by exitlimit on 2012-02-24
Also, this is what I'm getting when I in the terminal as well for some reason;

steve@steve-MS-6380:~$ gksu gedit /ect/samba/smb.conf 
 
(gksu:15354): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:15354): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:15354): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:15354): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by Morbius1 on 2012-02-25
Here's the problem as I see it:
> "\\steve-MS-6380\public" prompted me for a username and passwordBut you have a share that does not require authentication and you shouldn't be asked for a user name and password:
> [public]
path=/home/steve/Public
comment=
usershare_acl=Everyone:F,
[COLOR=Blue]guest_ok=y[/COLOR]     There may be other reasons why this is happening but the 2 I can think of at the moment are:

**[1]** Windows automatically passes without being asked the login user's username and password when it tries to access a remote share. If the user name on the Linux box is the same as the username on the Windows box but the samba password does not the Windows client is asked for a password. There are 2 ways to fix this:

** Remove the samba password for the common user name:
```
sudo smbpasswd -x common-user-name
```** **OR**, Make the samba password [COLOR=Blue]match exactly[/COLOR] the Windows login password:
```
sudo smbpasswd -a common-user-name
```Again, this is true only if you are using the same login name on both machines.

**[2] **You have encrypted your home directory.

I really don't have any experience with what to do with Samba in this case since I've never encrypted my home directory but based on other posts it appears to match your symptoms. You could try to share a folder outside your home directory to see if that circumvents the problem.

For example:

** Create a folder at say ... /home/Public
```
sudo mkdir /home/Public
```** Then bring up a root instance of nautilus to share that folder:
```
gksu nautilus
```

---

### Post by oppobeenrot on 2012-02-25
losing fat, how to lose weight, [african mango plus grapefruit diet]("http://www.africanmango.be") , effective diets , [http://www.africanmango.be](http://www.africanmango.be)

---

### Post by roelforg on 2012-02-25
> **exitlimit said:**
> Also, this is what I'm getting when I in the terminal as well for some reason;

steve@steve-MS-6380:~$ gksu gedit /ect/samba/smb.conf 
 
(gksu:15354): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:15354): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:15354): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", 
 
(gksu:15354): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Just ignore the warning, it's because you don't have some gtk-module installed gedit doesn't use.

---


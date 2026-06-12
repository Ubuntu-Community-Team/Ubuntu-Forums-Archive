---
title: "Sharing folder between Ubuntu 10.04 PC and a Snow Leopard Mac?"
date: 2010-06-04
forum: General Help
---

### Post by A440 on 2010-06-04
Hi There,

This is my first post and also my first experience using a Linux distro.

I've installed Ubuntu 10.04 as a dual boot on my PC and it's all gone pretty well so far (very enjoyable!). However, I'm having difficulties setting up a shared folder between my Ubuntu PC and my Snow Leopard 10.6.3 Mac. They are both connected by ethernet to my router.

Initially I tried connecting from the Mac to a folder I'd set up on the PC for sharing,  and actually managed to get it to work for a session, but for some reason it has now ceased to work and I can't seem to figure out why.

I'd appreciate any help you can offer. Please assume a fairly low level of technical ability with me. This is my first exploration of Linux and I am a complete beginner with it. 

Thanks in advance.

---

### Post by Morbius1 on 2010-06-04
If you had it working once and now it's stopped then the first thing I would check is if samba is running on Ubuntu. In a terminal type:
```
sudo status smbd
```If it's not running then start it:
```
sudo restart smbd
sudo restart nmbd

```If that isn't it you might want to post the output of these commands just to see if there is something misconfigured:
```
net usershare info
testparm -s
```

---

### Post by A440 on 2010-06-04
Thanks Morbius...

okay, so I'm a total newbie when it comes to terminal...but have entered suggested commands and this was the result:

[COLOR=Red]paul@paul-desktop:~$ sudo status smbd
smbd start/running, process 800
paul@paul-desktop:~$ sudo restart smbd
smbd start/running, process 3097
paul@paul-desktop:~$ sudo restart nmbd
nmbd start/running, process 3105
paul@paul-desktop:~$ net usershare info
[macshare]
path=/home/paul/Desktop/MacShare
comment=
usershare_acl=Everyone:F,
guest_ok=n

paul@paul-desktop:~$ testparm -s[/COLOR] [COLOR=Red]
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[MacShare]"
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
    panic action = /usr/share/samba/panic-action %d

[printers][/COLOR] [COLOR=Red]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$][/COLOR] [COLOR=Red]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[MacShare][/COLOR] [COLOR=Red]
    path = /home/paul/Desktop/MacShare
    valid users = paul
    read only = No
paul@paul-desktop:~$ ^C
[/COLOR] 
Now when I 'connect to server' on my Mac...the server address is:

SMB://paul-desktop/home/paul/Desktop/MacShare

press connect. Result on Mac (after about a minute) is : Connection failed : The server "paul-desktop" may not exist or it is unavailable at this time. Check the server name or IP address, check your network connection, and then try again.

If my Ubuntu firewwall is disabled, I get the same message, only instantly.

---

### Post by Morbius1 on 2010-06-04
**First**, There is one thing that confuses just about everyone because it's not documented well. There are two methods of using samba to share directories in Ubuntu and you are using both on the same target:

One is Nautilus-share:
> [COLOR=Red][macshare]
path=/home/paul/Desktop/MacShare
comment=
usershare_acl=Everyone:F,
guest_ok=n[/COLOR]The other is Classic-share:
> [COLOR=Red][MacShare][/COLOR] [COLOR=Red]
    path = /home/paul/Desktop/MacShare
    valid users = paul
    read only = No[/COLOR]They are configured differently so I would suggest you get rid of the Nautilus-share version. Just go back into Nautilus and reverse the steps you used to create the share.

**Second**, In your classic share you have:
> [COLOR=Red]     valid users = paul[/COLOR]Did you create a samba password for user "paul"?
```
sudo smbpasswd -a paul
```**Third** , I don't know where this is coming from but this is the second time in as many days that I've seen this line in smb.conf:
> [COLOR=Red]     username map = /etc/samba/smbusers[/COLOR]You will need to comment out that line and restart samba:
Open Terminal and type:
```
gksu gedit /etc/samba/smb.conf
```Find the "username map" line and place a # sign in front of it so it reads:
```
[COLOR=Red]#username map = /etc/samba/smbusers[/COLOR]
```Save the file, exit gedit, and back in the terminal restart samba:
```
sudo restart smbd
sudo restart nmbd
```**Forth**, this is the wrong syntax:
>  SMB://paul-desktop/home/paul/Desktop/MacShareIt should be:
```
 SMB://paul-desktop/MacShare
```

Oh and keep the Ubuntu firewall disabled for the time being - at least until we can get an actual connection.

---

### Post by A440 on 2010-06-04
Still no joy. Have disabled firewire and followed your suggestions...some updates came in that I installed too (followed your suggested after updating btw).

seem to get a different response to sudo restart smbd now .

[COLOR=Red]paul@paul-desktop:~$ sudo smbpasswd -a paul
New SMB password:
Retype new SMB password:
paul@paul-desktop:~$ gksu gedit /etc/samba/smb.conf
paul@paul-desktop:~$ sudo restart smbd
restart: Unknown instance: 
paul@paul-desktop:~$ sudo restart nmbd
nmbd start/running, process 2615
paul@paul-desktop:~$ ^C
paul@paul-desktop:~$ [/COLOR]

---

### Post by A440 on 2010-06-04
I ran your initial terminal commands again to help diagnosis...

[COLOR=Red]paul@paul-desktop:~$ sudo status smbd
[sudo] password for paul: 
smbd stop/waiting
paul@paul-desktop:~$ sudo restart smbd
restart: Unknown instance: 
paul@paul-desktop:~$ sudo restart nmbd
nmbd start/running, process 2886
paul@paul-desktop:~$ net usershare info
paul@paul-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[MacShare]"
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
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[MacShare]
    path = /home/paul/Desktop/MacShare
    valid users = paul
    read only = No
paul@paul-desktop:~$ 
[/COLOR]

---

### Post by Morbius1 on 2010-06-04
> [COLOR=Red][COLOR=Black]paul@paul-desktop:~$ sudo status smbd
[sudo] password for paul: 
smbd stop/waiting
paul@paul-desktop:~$ sudo restart smbd
restart: Unknown instance:[/COLOR] [/COLOR]
That's a problem. Let me research this a little since I'm not sure why samba won't start.

[COLOR=Blue]EDIT:[/COLOR] Try :
```
sudo start smbd
```

---

### Post by A440 on 2010-06-04
Update!!! I rebooted both computers and can now access the shared folder!!...looks like samba is now working:
[COLOR=Red]
[/COLOR]A big heartfelt thankyou to you :)

I'll continue to monitor the situation and report back ... touch wood it's now stable.

[COLOR=Red]paul@paul-desktop:~$ sudo status smbd
[sudo] password for paul: 
smbd start/running, process 807
paul@paul-desktop:~$ net usershare info
paul@paul-desktop:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[MacShare]"
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
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

[MacShare]
    path = /home/paul/Desktop/MacShare
    valid users = paul
    read only = No
paul@paul-desktop:~$ 


[/COLOR]

---

### Post by A440 on 2010-06-07
OK, so after a few days of living with the shared folder an issue has come to light. Basically it doesn't work with the Ubuntu firewall running. Any tips on how to configure the firewall, so the shared folder works with it on, would be most welcome.

---

### Post by Morbius1 on 2010-06-07
That I can't help you with so consider this a bump. I'm behind a router so I don't feel the need to add rules to the linux firewall. If I remember correctly the following ports have to allow access:

137, 138, 139, and 445. Both UDP and TCP.

There may be more I just don't remember, Sorry

---

### Post by A440 on 2010-06-07
I have a router too, so it looks like I don't really need an additional firewall either. Thanks again for your help.

---


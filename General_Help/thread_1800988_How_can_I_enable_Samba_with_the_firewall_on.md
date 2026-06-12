---
title: "How can I enable Samba with the firewall on?"
date: 2011-07-09
forum: General Help
---

### Post by linuxuser12345 on 2011-07-09
Hey, I want to have file sharing with Windows computers, but I guess I am not allowed to while my gufw firewall tool is on. Is there a way I can set up an easy work-around using my firewall?

---

### Post by 11ghjones on 2011-07-09
I'm assuming gufw is just a frontend to ufw.  Just run sudo ufw allow samba and it will open all the ports necessary.

---

### Post by mikewhatever on 2011-07-09
Use gufw to create a rule to allow samba.;)
See the link below for more info.
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by linuxuser12345 on 2011-07-09
I found out my firewall was never on in the first place. Is there a way I can completely remove Samba and all the files and folders that came along with it when I tried to set up file sharing with Windows, so that I can reinstall it and all the settings go back to default?

---

### Post by 11ghjones on 2011-07-09
sudo apt-get purge samba-common

---

### Post by mikewhatever on 2011-07-09
Samba has nothing to do with the firewall settings. Why do you want to remove it?

---

### Post by linuxuser12345 on 2011-07-09
Thank you! I hope this works! :)

---

### Post by 11ghjones on 2011-07-09
I believe what he's saying is that it had nothing to do with the firewall, and he simply wants to start over on his Samba configuration files.

---

### Post by linuxuser12345 on 2011-07-09
^what that person said^

---

### Post by linuxuser12345 on 2011-07-09
Samba has been completely uninstalled and reinstalled again, and I restarted the system. Now, whenever I right-click on a folder or location, go to "Properties", there is no "Sharing" tab! :(

Somebody please help me. Thanks

---

### Post by linuxuser12345 on 2011-07-09
Can somebody help me? I followed what [11ghjones]("http://ubuntuforums.org/member.php?u=781282") told me to do, then I reinstalled Samba to see if I could get it working, and nothin. Now file sharing doesn't even come up under the properties of a folder! :(

---

### Post by 11ghjones on 2011-07-09
```
sudo apt-get install nautilus-share ubuntu-desktop
```

What happened was that the nautilus-share extension (the share tab) is dependent on samba, and was uninstalled when you removed samba.  I put the ubuntu-desktop package in that command, because I think samba is part of the base distribution, and when you uninstalled samba, it may have removed it too.  The ubuntu-desktop package helps ease upgrades, so I usually try to keep it if at all possible.

Sorry it took so long to get back!

---

### Post by linuxuser12345 on 2011-07-09
Thank you! :) Hopefully this works...

---

### Post by linuxuser12345 on 2011-07-27
Okay, our Windows 7 computer on the network will not recognize my Ubuntu 11.04-powered system. Any suggestions? I am trying to set up a file server, but I can't if the Windows computer can't even "see" this computer I'm using... :/

---

### Post by Morbius1 on 2011-07-27
What would help is the output of each o the following commands so we can see how you are set up and the good folks here can stop guessing:
```
testparm -s
net usershare info --long
```

---

### Post by linuxuser12345 on 2011-07-27
```
jeb@Kitchen-PC:~$ testparm -s
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
jeb@Kitchen-PC:~$ net usershare info --long
[documents]
path=/home/jeb/Documents
comment=
usershare_acl=Everyone:R,KITCHEN-PC\jeb:F,
guest_ok=n

info_fn: file /var/lib/samba/usershares/1125 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
info_fn: file /var/lib/samba/usershares/frank13 is not a well formed usershare file.
info_fn: Error was Path is not a directory.
jeb@Kitchen-PC:~$ 

```
Here you go :)

---

### Post by Morbius1 on 2011-07-27
Now we need to find out if Kitchen-PC can see it's own share. What's the output of this command:
```
smbtree
```

---

### Post by linuxuser12345 on 2011-07-27
```
jeb@Kitchen-PC:~$ smbtree
Enter jeb's password: 
jeb@Kitchen-PC:~$ 
```

---

### Post by Morbius1 on 2011-07-27
Find out if nmbd is running:
```
sudo service nmbd status
```If it's not running start it:
```
sudo service nmbd start
```Then try smbtree again. You have to get this so that at least Kitchen-PC can see it's own shares.

EDIT: It's not clear to me if the firewall is on or off so disable it to see if it's getting in the way:
```
 sudo ufw disable
```

---

### Post by linuxuser12345 on 2011-07-27
```
jeb@Kitchen-PC:~$ sudo service nmbd status
[sudo] password for jeb: 
nmbd start/running, process 1495
jeb@Kitchen-PC:~$ sudo service nmbd start
start: Job is already running: nmbd
jeb@Kitchen-PC:~$ smbtree
Enter jeb's password: 
jeb@Kitchen-PC:~$ sudo ufw disable
Firewall stopped and disabled on system startup
jeb@Kitchen-PC:~$ smbtree
Enter jeb's password: 
WORKGROUP
    \\KITCHEN-PC             Kitchen-PC server (Samba, Ubuntu)
        \\KITCHEN-PC\documents          
        \\KITCHEN-PC\HP-Officejet-4500-G510g-m    HP Officejet 4500 G510g-m
        \\KITCHEN-PC\IPC$               IPC Service (Kitchen-PC server (Samba, Ubuntu))
        \\KITCHEN-PC\print$             Printer Drivers
jeb@Kitchen-PC:~$ 

```

Is there a way I can get "smbtree" working with the firewall on?

---

### Post by Morbius1 on 2011-07-27
```
sudo ufw allow Samba
```

---

### Post by Morbius1 on 2011-07-27
I keep forgetting to add something to that command. You will probably need to make one adjustment to the default config for ufw to allow netbios transfer so that yu can browse by name. Edit /etc/default/ufw and add add the netbios_ns option to the last line:

From this:
> IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc"To this:

> IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc [COLOR=Blue]nf_conntrack_netbios_ns[/COLOR]"
See if "sudo ufw allow Samba" works by itself first. If it doewsn't work then try editing the /etc/default/ufw file. No need to muck about with config files if you don't have to.

---

### Post by linuxuser12345 on 2011-07-27
> **Morbius1 said:**
> I keep forgetting to add something to that command. You will probably need to make one adjustment to the default config for ufw to allow netbios transfer so that yu can browse by name. Edit /etc/default/ufw and add add the netbios_ns option to the last line:

From this:
To this:

See if "sudo ufw allow Samba" works by itself first. If it doewsn't work then try editing the /etc/default/ufw file. No need to muck about with config files if you don't have to.
How do I do this?

---

### Post by Morbius1 on 2011-07-28
Open up a terminal and type:
```
gksu gedit /etc/default/ufw
```The last 2 lines of the file should look like this:
> # extra connection tracking modules to load
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc"Change it to this:
> # extra connection tracking modules to load
IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_irc nf_nat_irc [COLOR=Blue]nf_conntrack_netbios_ns[/COLOR]"You may have to restart the firewall:
sudo ufw disable
sudo ufw enable

---

### Post by linuxuser12345 on 2011-07-28
Okay, the network is now up and running! Thank you :)

---

### Post by mcellius on 2011-07-28
Ah, this worked for me, as well!!!!!  Thank you!

---


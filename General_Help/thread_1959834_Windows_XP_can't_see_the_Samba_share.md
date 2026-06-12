---
title: "Windows XP can't see the Samba share"
date: 2012-04-16
forum: General Help
---

### Post by Phasma Felis on 2012-04-16
So I've just set up a Samba share on my Ubuntu 11.10 file server, following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1659816"). My OS X Snow Leopard MacBook can see it; so can my roommate's Win7 box. My XP machine can't.

I'm not really sure how to find a solution for this. Googling reveals a million different (contradictory) tutorials on setting up and troubleshooting an Ubuntu Samba share, but given that the other machines can see it, this may be a Windows problem more than Ubuntu, and none of them say much about that. Any suggestions? 

Here's some outputs that Morbius1 said would help, if it is an Ubuntu problem. Note that, in the smbtree output, it's aware of Mnemosyne (the Ubuntu host) and Athens (the Win7 machine that can see the share). It's not aware of Titan (the WinXP machine) or, bizarrely, Argent (the MacBook that *can* see the share). So...I don't know what that means.
```
phasma@Mnemosyne:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = ROSENET
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
        comment = Home Directories
        read only = No

[printers]
        comment = All Printers
        path = /var/spool/samba
        read only = Yes
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        read only = Yes
```

```
phasma@Mnemosyne:~$ net usershare info --long
[fileshare]
path=/home/phasma/fileshare
comment=Rosenet fileshare
usershare_acl=Everyone:F,
guest_ok=y
```
```
phasma@Mnemosyne:~$ hostname
Mnemosyne
```
```
phasma@Mnemosyne:~$ smbtree
Enter phasma's password:
WORKGROUP
        \\ATHENS
ROSENET
        \\MNEMOSYNE                     Mnemosyne server (Samba, Ubuntu)
                \\MNEMOSYNE\fileshare           Rosenet fileshare
                \\MNEMOSYNE\print$              Printer Drivers
                \\MNEMOSYNE\IPC$                IPC Service (Mnemosyne server (Samba, Ubuntu))
```

---

### Post by Morbius1 on 2012-04-16
Is Titan and Mnemosyne in the same subnet? Do they both connect to the same router? Their IP address should be in the same range if they are.

192.168.0.xxx - something like that.

---

### Post by Phasma Felis on 2012-04-16
> **Morbius1 said:**
> Is Titan and Mnemosyne in the same subnet? Do they both connect to the same router? Their IP address should be in the same range if they are.

192.168.0.xxx - something like that.
Yes--they're both in 192.168.1.xxx.

---

### Post by Morbius1 on 2012-04-16
I'm having a hard time finding an explanation that fits all your symptoms.

It's only the WinXP machine that can't access the share. The Win7 and OSX machine have no problem. The only thing I can think of at the moments that explains why Linux and XP can't see each other is a firewall on the XP machine is getting in the way. Disable it and see if a connection can be made.

---


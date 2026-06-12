---
title: "Debugging samba problems?"
date: 2011-03-27
forum: General Help
---

### Post by ailling on 2011-03-27
Hello-

I have 2 windows 7 machines & an ubuntu 10.04 LTS machine, and a crossover cable. The two win7 machines can see each other fine, so the cable, etc. works.

I followed these instructions exactly:
[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html)

And the windows 7 client can't recognize the ubuntu machine.

Below is a print out from SWAT, and I'm concerned that SWAT isn't picking up the [share] section as specified in /etc/samba/smb.conf

any suggestions for how to debug this? I'm not sure what's wrong--if you can't tell from my post, I'm very inexperienced in networking....

thanks in advance =)

**from SWAT:**
# Samba config file created using SWAT
# from UNKNOWN (127.0.0.1)
# Date: 2011/03/27 22:22:41

[global]
    netbios name = UBUNTU_MACHINE
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

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    read only = No
    create mask = 0755

[B]
[share] section from /etc/samba/smb.conf:[/B]
[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

    guest ok = Yes

---


---
title: "Samba"
date: 2010-06-06
forum: General Help
---

### Post by Dn4mycrownj on 2010-06-06
I am trying to see share files on my windows machine to my linux machine. I would like an answer to how to fix the problem. This is where i am at i am using my own network to learn who to use nmap properly. I ping my whole network with nmap -sS -O. Then i used nmblookup -a which gave me the infromation i needed. Then i run smbclient -L computername -I ip address -N 

This will not show me the windows os this only show me my laptop. What can i change for this to show me the other computer on this network. The port i am wanting is open. 

I want to be able to mount the share files and move them to my computer i am going to use the commands put and get to move the files when i am able to get to the smb: > . This is the way i want to learn it please just help me with this way.


```
[global]
    ; General server settings
    netbios name = 
    server string =
    workgroup = 
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
[DVD-ROM Drive]
    path = /media/cdrom
    browseable = yes
    read only = yes
    guest ok = yes

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = 
    force group =
```

---

### Post by bodhi.zazen on 2010-06-06
I am moving this thread to general help.

Which computer is the server (Server = location where files are located).

From your post I can not tell if Windows or Ubuntu is the server.

Second question , firewall ?

---

### Post by Dn4mycrownj on 2010-06-06
i will run nmap -sS -O 192.168.1.100-125 -p 139 it returns the one computer i am looking for.
 ```
Interesting ports on 192.168.1.100:
PORT    STATE SERVICE
139/tcp open  netbios-ssn
MAC Address: **:**:**:**:**:** (Hon Hai Precision Ind. Co.)
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running: Microsoft Windows Vista|2008
OS details: Microsoft Windows Vista or Windows Server 2008 SP1, Microsoft Windows Vista SP0 or SP1 or Server 2008 SP1
Network Distance: 1 hop

```then i run nmblookup -A 192.168.1.100 and get this
```
Looking up status of 192.168.1.100
    FAMILY-PC       <00> -         B <ACTIVE> 
    WORKGROUP       <00> - <GROUP> B <ACTIVE> 
    WORKGROUP       <1e> - <GROUP> B <ACTIVE> 
    FAMILY-PC       <20> -         B <ACTIVE> 
    WORKGROUP       <1d> -         B <ACTIVE> 
    ..__MSBROWSE__. <01> - <GROUP> B <ACTIVE> 


```Now when i type in smbclient -LFAMILY-PC -I 192.168.1.100 

it gives the error below (that command should show me the shared files on that computer.) 

Connection to family-pc failed (Error NT_STATUS_BAD_NETWORK_NAME)

That cant be right because i called for the network name and i know the network name they are both the same.

---

### Post by bodhi.zazen on 2010-06-07
Typically to connect to a windows share I either use the grpahical tools or mount command.

Under the ment 

Places -> Connect to a server -> Fill in the pop up box 
service type - Windows share
Enter the Windows IP , Shared folder, and user name. You may or may not need to also enter the domain name.

Or from the command line

```
sudo mkdir /media/windows_share
sudo mount -t cifs //windows_ip/share /media/windows_share -o username=windows_user
```

To connect to a windows server you do not need to install or configure the samba server on Ubuntu.

Is the windows server firewalled ? Is the windows share properly configured ?

---

### Post by JoelOl75 on 2010-06-07
Even to share folders in Ubuntu to Windows it's much easier to just right click and share the folder in Nautilus than to set up manual entries in /etc/samba/smb.conf

---


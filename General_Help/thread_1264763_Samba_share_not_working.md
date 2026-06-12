---
title: "Samba share not working"
date: 2009-09-12
forum: General Help
---

### Post by rmvg on 2009-09-12
Hello all Samaba is not working for me i followed a step by step guide for 9.04.  

From windows Vista i can see an unknown device and if i try to connect to it get an error about not being able to find the properties.

I followed the a troubleshooting guide found here [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting)  

I can ping the client from the host and the host from the client using ip addresses the dns stuff does not work but i will be using IP's anyway.

I get stuck on step 3 the one about broadcasting I have disabled my windows firewall and do not believe jaunty has a firewall by default. My router is a buffalo whr54hp running the latest version of tomato firmware.  Also step 4 fails to find my client and only seems to find the server Please see below

Permissions on the share directory are 

c0mputerking@Surveillance-King-Home:/srv/samba$ ls -l
total 4
drwxr-xr-x 2 nobody nogroup 4096 2009-09-11 22:21 share
 
############################################################

c0mputerking@Surveillance-King-Home:/dvrdata/bin2$ testparm -s
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
        workgroup = ASIA
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
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

[share]
        comment = Computer King Server File Share
        path = /svr/samba/share
        read only = No
        create mask = 0755
        guest ok = Yes

################################################################

smbclient -L 192.168.1.137
Enter c0mputerking's password:
Anonymous login successful
Domain=[ASIA] OS=[Unix] Server=[Samba 3.3.2]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        share           Disk      Computer King Server File Share
        IPC$            IPC       IPC Service (Surveillance-King-Home server (Samba, Ubuntu))
Anonymous login successful
Domain=[ASIA] OS=[Unix] Server=[Samba 3.3.2]

        Server               Comment
        ---------            -------
        SURVEILLANCE-KIN     Surveillance-King-Home server (Samba, Ubuntu)
        WHO-MOBILE

        Workgroup            Master
        ---------            -------
        ASIA                 SURVEILLANCE-KING-HOME

##########################################################

nmblookup -B 192.168.1.137 __SAMBA__
querying __SAMBA__ on 192.168.1.137
192.168.1.137 __SAMBA__<00>

##########################################################

nmblookup -B 192.168.1.50 "*"
querying * on 192.168.1.50
name_query failed to find name *

#################################################################

nmblookup -d 2 '*'
added interface eth0 ip=fe80::211:11ff:fe8d:9764%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.1.137 bcast=192.168.1.255 netmask=255.255.255.0
querying * on 192.168.1.255
Got a positive name query response from 192.168.1.137 ( 192.168.1.137 )
192.168.1.137 *<00>

---

### Post by swerdna on 2009-09-12
Here are the contents of your [global} as revealed by testparm:

[global]
workgroup = ASIA
server string = %h server (Samba, Ubuntu)
map to guest = Bad User
obey pam restrictions = Yes
passdb backend = tdbsam
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

The form of [global] that is recommended for a small home LAN is this:

[global]
workgroup = ASIA
netbios name = NETBIOS_NAME  <== put here your name for the server
name resolve order = bcast host lmhosts wins
server string =
map to guest = Bad User
local master = yes
preferred master = yes
os level = 65
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False

FFI: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

perhaps before making changes, back up the old file with this:```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.backup
```

---

### Post by rmvg on 2009-09-13
Thank you greatly for your reply!

I made some changes as you suggested now vista finds nothing in the network and sharing center.  I have included another testparm and the output of /var/log/log.nmbd log.smbd seems to be empty.

Load smb config files from /etc/samba/smb.conf
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = ASIA
        netbios name = ASIA
        server string = ASIA
        map to guest = Bad User
        name resolve order = bcast host lmhosts wins
        os level = 65
        preferred master = Yes
        usershare allow guests = Yes
        usershare owner only = No

[share]
        comment = king
        path = /svr/samba/share
        read only = No
        create mask = 0755
        guest ok = Yes


[2009/09/13 12:43:43,  0] nmbd/nmbd.c:terminate(71)
  Got SIGTERM: going down...
[2009/09/13 12:43:49,  0] nmbd/nmbd.c:main(850)
  nmbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/09/13 12:43:49,  0] nmbd/nmbd_nameregister.c:register_name_response(129)
  register_name_response: server at IP 192.168.1.50 rejected our name registration of ASIA<00> IP 192.168.1.137 with error code 6.
[2009/09/13 12:43:49,  0] nmbd/nmbd_mynames.c:my_name_register_failed(35)
  my_name_register_failed: Failed to register my name ASIA<00> on subnet 192.168.1.137.
[2009/09/13 12:43:49,  0] nmbd/nmbd_namelistdb.c:standard_fail_register(307)
  standard_fail_register: Failed to register/refresh name ASIA<00> on subnet 192.168.1.137
[2009/09/13 12:44:12,  0] nmbd/nmbd_become_lmb.c:become_local_master_stage2(395)
  *****

  Samba name server ASIA is now a local master browser for workgroup ASIA on subnet 192.168.1.137

  *****




c0mputerking@Surveillance-King-Home:/srv/samba$ sudo vim /var/log/samba/log.smbd.1.gz
c0mputerking@Surveillance-King-Home:/srv/samba$ test
test             testparm         testparm.samba3  test-speech
c0mputerking@Surveillance-King-Home:/srv/samba$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        workgroup = ASIA
        netbios name = ASIA
        server string = ASIA
        map to guest = Bad User
        name resolve order = bcast host lmhosts wins
        os level = 65
        preferred master = Yes
        usershare allow guests = Yes
        usershare owner only = No

[share]
        comment = king
        path = /svr/samba/share
        read only = No
        create mask = 0755
        guest ok = Yes
c0mputerking@Surveillanc

---

### Post by swerdna on 2009-09-13
Check the Samba daemons are set to run. For Ubuntu you would look in System --> Administration --> Services --> Folder sharing (Samba)

And/or check they are running with this command:```
sudo /etc/init.d/samba status
```

As a temporary diagnostic measure, turn off the Linux firewall and any proprietary windows firewalls. Turn them back on when the network is running OK.

Restart all your routers and modems and peripheral network hardware.


Cause the Local Master Browser election to be held: In simple networks I find a good way to get the election of Local Master Browser finalised is to reboot Linux, then pause 2 minutes then reboot windows then pause 2 minutes then reboot Linux then pause 2 minutes then reboot windows then have a beverage then have a look in network neighborhood. From linux side, run command ```
smbtree -N
```

Those will eliminate a lot of issues/questions. See what that does / if any improvement.

---

### Post by rmvg on 2009-09-13
hmm smbd is not running? that would explain why the smbd log is empty.

sudo /etc/init.d/samba status
[sudo] password for c0mputerking:
 * nmbd is running
 * smbd is not running

Also i have already disabled windows firewall, is thier a firewall installed by default on the xubuntu box? something i need to disable?

---

### Post by rmvg on 2009-09-13
hmm smbd is not running? that would explain why the smbd log is empty.

sudo /etc/init.d/samba status
[sudo] password for c0mputerking:
 * nmbd is running
 * smbd is not running

Also i have already disabled windows firewall, is thier a firewall installed by default on the xubuntu box? something i need to disable?

---

### Post by swerdna on 2009-09-13
```
sudo /etc/init.d/samba restart
```should start the smb daemon. It will go to off when you reboot unless yoyu set it to be always on. I told you how to set the daemons to be always on in Ubuntu -- but I don't know what management interface operates in Xubuntu. Check your management intefaces there.

Re the firewall. UFW is the default firewall. Try these three commands, see what happens:[LIST]
[*]sudo ufw status
[*]sudo ufw disable 
[*]sudo ufw enable
[/LIST]

---

### Post by rmvg on 2009-09-13
> **swerdna said:**
> ```
sudo /etc/init.d/samba restart
```should start the smb daemon. It will go to off when you reboot unless yoyu set it to be always on. I told you how to set the daemons to be always on in Ubuntu -- but I don't know what management interface operates in Xubuntu. Check your management intefaces there.

Re the firewall. UFW is the default firewall. Try these three commands, see what happens:[LIST]
[*]sudo ufw status
[*]sudo ufw disable 
[*]sudo ufw enable
[/LIST]

firewall is not turned on? which is what i want for now
sudo ufw status
Status: inactive
c0mputerking@Surveillance-King-Home:/etc/samba$ sudo ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? n
Aborted

#################################################

smbd is not starting tried both a restart and a stop/start do not think it has anything to do with system restart as i have not restarted yet!

c0mputerking@Surveillance-King-Home:/etc/samba$ sudo /etc/init.d/samba restart
[sudo] password for c0mputerking:
 * Stopping Samba daemons                                                [ OK ]
 * Starting Samba daemons                                                [ OK ]
c0mputerking@Surveillance-King-Home:/etc/samba$ sudo /etc/init.d/samba status
 * nmbd is running
 * smbd is not running
c0mputerking@Surveillance-King-Home:/etc/samba$ sudo /etc/init.d/samba stop
 * Stopping Samba daemons                                                [ OK ]
c0mputerking@Surveillance-King-Home:/etc/samba$ sudo /etc/init.d/samba start
 * Starting Samba daemons                                                [ OK ]
c0mputerking@Surveillance-King-Home:/etc/samba$ sudo /etc/init.d/samba status
 * nmbd is running
 * smbd is not running

---

### Post by swerdna on 2009-09-13
Check the Samba packages are installed. This command will search and report on them: ```
dpkg -l | egrep "samba|smbclient"
```
What do you see?

Also, sampa might be properly installed but not switched on. I don't use Xubuntu. I said earlier to check you had set it to permanently on. Have you done that?

---

### Post by rmvg on 2009-09-13
> **swerdna said:**
> Check the Samba packages are installed. This command will search and report on them: ```
dpkg -l | egrep "samba|smbclient"
```
What do you see?

Also, sampa might be properly installed but not switched on. I don't use Xubuntu. I said earlier to check you had set it to permanently on. Have you done that?

Packages are installed see below also xubuntu is the same as ubuntu in the fact that if you run /etc/init.d/samba start it should start smbd right? how do you start your programs?  See the output of my above post jaunty is telling me that samba is starting fine, but in reality is not starting at all


dpkg -l | egrep "samba|smbclient"
ii  libsmbclient                               2:3.3.2-1ubuntu3.1                        shared library for communication with SMB/CIFS servers
ii  python-smbc                                1.0.6-0ubuntu2                            Python bindings for Samba clients (libsmbclient)
ii  samba                                      2:3.3.2-1ubuntu3.1                        SMB/CIFS file, print, and login server for Unix
ii  samba-common                               2:3.3.2-1ubuntu3.1                        common files used by both the Samba server and client
ii  smbclient                                  2:3.3.2-1ubuntu3.1                        command-line SMB/CIFS clients for Unix
c0mputerking@Surveillance-King-Home:/etc/samba$

---

### Post by swerdna on 2009-09-14
> Packages are installed see below also xubuntu is the same as ubuntu in the fact that if you run /etc/init.d/samba start it should start smbd right? how do you start your programs? See the output of my above post jaunty is telling me that samba is starting fine, but in reality is not starting at allEither the starting mechanism for the smb daemon is broken or the daemon is broken. Watch this thread re the second possibility:
[http://ubuntuforums.org/showthread.php?t=1265899](http://ubuntuforums.org/showthread.php?t=1265899)

---

### Post by swerdna on 2009-09-14
[OK, uncle-c has replied]("http://ubuntuforums.org/showthread.php?p=7946352") to install sysv-rc-conf and run it from the CLI. I did that. It works well. Put X marks in runlevels 2, 3, 4 and 5.

[this may or may not solve the problem but if it's "not", at least  it will take away one more possibility for error]

---


---
title: "Problems with configurating Samba"
date: 2006-03-15
forum: General Help
---

### Post by UeB on 2006-03-15
I have red in the Ubuntu FAQ Guide how to share home folders with read/write permission which can be found at:
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-serv](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-samba-serv)
I had no problems doing this:

sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup
sudo gedit /etc/samba/smb.conf
and edit the file at this lines:

security = share

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
writable = yes

But when i try to perform this:

sudo testparm sudo /etc/init.d/samba restart

the terminal says:

moritz@ubuntu-notebook:~$ sudo testparm sudo /etc/init.d/samba restart
Password:
Load smb config files from sudo
params.c:OpenConfFile() - Unable to open configuration file "sudo":
        No such file or directory
Error loading services.
moritz@ubuntu-notebook:~$
moritz@ubuntu-notebook:~$

althow there ist a file named sudo and an file named samba in the /etc/init.d/samba  folder

my windows machine can see my ubuntu machine but it does not see any folder

how to get it working? :-)

and second question how to change the workgroup name of my ubuntu machine?
this is not mentioned in the FAQ Guide.

---

### Post by firecat53 on 2006-03-15
It looks like you're trying to run two separate commands at one time. Try them separately:

```
sudo testparm
```
(this checks the smb.conf syntax)
then if there's nothing to fix
```
sudo /etc/init.d/samba restart
```
to start using your newly changed smb.conf

To change the workgroup (network) name is the
```
workgroup = NETWORKNAME
```
and the name of your computer on the network is the
```
# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)
```

Good luck :)
Scott

---

### Post by UeB on 2006-03-15
thanks for the explaining

athough my ubunu machine is now in the same workgroup as the windows machines there is still no visible folder. only an icon named "printer" can be seen by the windows machines (both windows 2000 prof.) if i double click on the name of my ubuntu machine

is the output of the testparm command usefull? well if here it is:

```
moritz@ubuntu-notebook:~$ sudo testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
        workgroup = 1
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
moritz@ubuntu-notebook:~$ sudo gedit /etc/samba/smb.conf

```

there is another problem: somethimes (lets say every third day)  i am asked to type a password when i double click on network-server on the ubuntu maschin which is impossible because there is no password set for the windwos LAN.

the exact fraise is:
>>
Authentification Required
You must log in to access [here comes ether the ip number of the pc of my borther or the windows name of the pc of my brother (also running win2kprof) ]
Login
Domain
Password
>>
as i said i have no idea why because there is no password set. And the network configuration of the my brother's pc is the same as on my windows pc...

---

### Post by UeB on 2006-03-16
push it!

---

### Post by UeB on 2006-03-17
i changed the option: "browsable" to "yes" see:
[homes]
   comment = Home Directories
   browseable = yes

now  a folder "homes" is visable in the network enviroment on my windwos machines but when i try to open it i am asked for login and password although the security option is set on "share" and the ubuntu starter guide said this is the option to disable password.

so what's wrong?
or who knows how to disable these anoing password query?
and why dosnt it work the way it is discripted in the ubuntu starter guide?

---


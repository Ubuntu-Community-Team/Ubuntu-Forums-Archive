---
title: "Samba in Badger (sharing with OSX10.4.6)"
date: 2006-04-08
forum: General Help
---

### Post by bloodniece on 2006-04-08
Hi,
I just switched from Fedora Core 5 to Ubuntu Breezy and am having trouble with Samba.   I can connect to the Ubuntu box via the Finder (on the MAC), but my shares are not showing up.  According to Webmin, the Mac Client is connected using the smb.  I tried sharing my home folder both using System > Administration > Shared Folders and using Webmin's Samba Server config tools.
Any ideas?  I used Firestarter to open everything up the mac box.

---

### Post by ksudbury on 2006-04-08
Check the smb.conf to double check it has your shares in there. Also for testing perposes only, stop the iptables service and see if you can connect? Does the box trying to access the samba server get prompted for a password at all ? 
 
Try to provide a little more info.

Keith

---

### Post by bloodniece on 2006-04-09
On the OSX side I never see a password prompt. Finder just hangs till it times out.
How do I stop IPTABLES?
Thanks,
D


My smb.conf file -->

```

[global]
   workgroup = MYWORKGROUP
   netbios name = ubuntu
   server string = %h server (Samba, Ubuntu)


   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes

   # Set CUPS for printing
   printcap name = CUPS
   printing = CUPS

   # Default logon
   logon drive = H:
   logon script = scripts/logon.bat
   logon path = \\server1\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000






   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:$
   passwd chat debug = yes
   unix password sync = yes

   # set the loglevel
   log level = 3


[homes]
   comment = Home
   valid users = %S
   read only = no
   browsable = no


[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   browsable = no


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   valid users = %U

   valid users = %U
   read only = no


[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = no
[allusers]
  comment = All Users
  path = /home/derek
  valid users = @users
  force group = users
  create mask = 0660
  directory mask = 0771
  writable = yes
```

---

### Post by bloodniece on 2006-04-09
Fixed it up:
apt-get install firestarter
added policy for my mac ip
added policy for smb service for mac ip
sudo smbpasswd -a derek
Password:
New SMB password:
Retype new SMB password:

Mac:
Finder --> command+K --> smb://192.168.1.104/sharename

Works!:p :p :p

---

### Post by Monster Boxx on 2006-05-16
I am happy to see that there may be other ways around it.

However I am troubled by the fact you are comprimising IP tables to accomplish this. Im kin of newb with all of that. (besides im behind a dedicated gentoo box with IP tables.)

In order to accomplish connetion to a share I simply on the MAC end typed

smb://xxx.xxx.x.xxx/"share" I was then prompted for a user/pass.

From what I read it is a MAC issue for some reason the mac is confused about what protocol to use when connecting to a linux box....

---


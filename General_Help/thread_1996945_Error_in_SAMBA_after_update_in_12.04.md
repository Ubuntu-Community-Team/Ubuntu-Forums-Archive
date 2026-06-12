---
title: "Error in SAMBA after update in 12.04"
date: 2012-06-04
forum: General Help
---

### Post by Randy M on 2012-06-04
Every time I run the Update Manager I get this error. SAMBA seems to be working, my connection to the printer on my wife's 10.04 machine and the shared directories work fine. Update also seems to work. Anyone know what's happening?

installArchives() failed: (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 202402 files and directories currently installed.) 
Preparing to replace update-manager 1:0.156.14.4 (using .../update-manager_1%%3a0.156.14.5_all.deb) ... 
Unpacking replacement update-manager ... 
Preparing to replace update-manager-core 1:0.156.14.4 (using .../update-manager-core_1%%3a0.156.14.5_amd64.deb) ... 
Unpacking replacement update-manager-core ... 
Processing triggers for libglib2.0-0 ... 
Processing triggers for man-db ... 
Processing triggers for gconf2 ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for gnome-menus ... 
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ... 
Unknown parameter encountered: "max log size" 
Ignoring unknown parameter "max log size" 
Unknown parameter encountered: "syslog" 
Ignoring unknown parameter "syslog" 
Unknown parameter encountered: "unix password sync" 
Ignoring unknown parameter "unix password sync" 
Unknown parameter encountered: "passwd program" 
Ignoring unknown parameter "passwd program" 
Unknown parameter encountered: "pam password change" 
Ignoring unknown parameter "pam password change" 
Unknown parameter encountered: "map to guest" 
Ignoring unknown parameter "map to guest" 
Unknown parameter encountered: "usershare allow guests" 
Ignoring unknown parameter "usershare allow guests" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
ERROR: Invalid smb.conf 
Unknown parameter encountered: "max log size" 
Ignoring unknown parameter "max log size" 
Unknown parameter encountered: "syslog" 
Ignoring unknown parameter "syslog" 
Unknown parameter encountered: "unix password sync" 
Ignoring unknown parameter "unix password sync" 
Unknown parameter encountered: "passwd program" 
Ignoring unknown parameter "passwd program" 
Unknown parameter encountered: "pam password change" 
Ignoring unknown parameter "pam password change" 
Unknown parameter encountered: "map to guest" 
Ignoring unknown parameter "map to guest" 
Unknown parameter encountered: "usershare allow guests" 
Ignoring unknown parameter "usershare allow guests" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
ERROR: Invalid smb.conf 
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied 
dpkg: error processing samba4 (--configure): 
 subprocess installed post-installation script returned error exit status 126 
No apport report written because MaxReports is reached already
Setting up update-manager-core (1:0.156.14.5) ... 
Setting up update-manager (1:0.156.14.5) ... 
Errors were encountered while processing: 
 samba4 
Error in function:  
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ... 
Unknown parameter encountered: "max log size" 
Ignoring unknown parameter "max log size" 
Unknown parameter encountered: "syslog" 
Ignoring unknown parameter "syslog" 
Unknown parameter encountered: "unix password sync" 
Ignoring unknown parameter "unix password sync" 
Unknown parameter encountered: "passwd program" 
Ignoring unknown parameter "passwd program" 
Unknown parameter encountered: "pam password change" 
Ignoring unknown parameter "pam password change" 
Unknown parameter encountered: "map to guest" 
Ignoring unknown parameter "map to guest" 
Unknown parameter encountered: "usershare allow guests" 
Ignoring unknown parameter "usershare allow guests" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
ERROR: Invalid smb.conf 
Unknown parameter encountered: "max log size" 
Ignoring unknown parameter "max log size" 
Unknown parameter encountered: "syslog" 
Ignoring unknown parameter "syslog" 
Unknown parameter encountered: "unix password sync" 
Ignoring unknown parameter "unix password sync" 
Unknown parameter encountered: "passwd program" 
Ignoring unknown parameter "passwd program" 
Unknown parameter encountered: "pam password change" 
Ignoring unknown parameter "pam password change" 
Unknown parameter encountered: "map to guest" 
Ignoring unknown parameter "map to guest" 
Unknown parameter encountered: "usershare allow guests" 
Ignoring unknown parameter "usershare allow guests" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
Unknown parameter encountered: "guest ok" 
Ignoring unknown parameter "guest ok" 
ERROR: Invalid smb.conf 
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied 
dpkg: error processing samba4 (--configure): 
 subprocess installed post-installation script returned error exit status 126

---

### Post by maverickaddicted on 2012-06-05
This may help you -

[https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/992820](https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/992820)

---

### Post by Randy M on 2012-06-05
It's still erroring out, now the error includes:
 
samba.provision.InvalidNetbiosName: The name ''RANDY-HP-PAVILION-G7-NOTEBOOK-PC'' is not a valid NetBIOS name

and it generates a system error. Is it safe to delete and re-install SAMBA?

---

### Post by bab1 on 2012-06-05
> **Randy M said:**
> It's still erroring out, now the error includes:
 
samba.provision.InvalidNetbiosName: The name ''RANDY-HP-PAVILION-G7-NOTEBOOK-PC'' is not a valid NetBIOS name

and it generates a system error. Is it safe to delete and re-install SAMBA?

Randy,

It looks like you have both Samba4 and Samba3 installed.  It's griping about the Samba4 install.  You need to un-install Samba4.

The netbios name (most likely your hostname) needs to be 15 characters or less.  You need a shorter (and IMHO nicer) name than this:```
 RANDY-HP-PAVILION-G7-NOTEBOOK-PC
```

Edit: To un-install samba4 you can use this ```
sudo apt-get purge samba4
```

---

### Post by maverickaddicted on 2012-06-06
> **bab1 said:**
> Randy,

It looks like you have both Samba4 and Samba3 installed.  It's griping about the Samba4 install.  You need to un-install Samba4.

The netbios name (most likely your hostname) needs to be 15 characters or less.  You need a shorter (and IMHO nicer) name than this:```
 RANDY-HP-PAVILION-G7-NOTEBOOK-PC
```

Edit: To un-install samba4 you can use this ```
sudo apt-get purge samba4
```

+1 to bab1 response.

OR

I have update around 14 Ubuntu Machines in last ten days and out of that I faced the wine and samba problem in two machines. I also tried several solution, but ended up in reinstalling of Samba. If you want you can reconfigure your Samba.

---

### Post by Randy M on 2012-06-06
Thanks, I uninstalled Samba4 and that seems to have cleared the errors. It also eliminated my connection to the shared drives on my other system. I'll try re-installing later.  
  
How do I shorten the name. That one is something that was automatically generated during install. I never typed it in.

---

### Post by bab1 on 2012-06-06
> **Randy M said:**
> Thanks, I uninstalled Samba4 and that seems to have cleared the errors. It also eliminated my connection to the shared drives on my other system. I'll try re-installing later.  
  
How do I shorten the name. That one is something that was automatically generated during install. I never typed it in.

Randy,  You have several options on that issue.  You could just change the netbios name within the /etc/samba/smb.conf file or change the hostname in the /etc/hosts file *along with* the hosts entry in the /etc/hosts file.  These last 2 need to be done as a pair.

I'm have to leave right now for about 4 hours.  I'll provide you the command options when I get back then if you need them.

---

### Post by Randy M on 2012-06-06
It seems that the hosts file would be the best place to make the change. Here's mine. I see the name, but I don't see the second edit that you mentioned. Thanks for all the help!

127.0.0.1    localhost
127.0.1.1    randy-HP-Pavilion-g7-Notebook-PC

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

### Post by bab1 on 2012-06-06
> **Randy M said:**
> It seems that the hosts file would be the best place to make the change. Here's mine. I see the name, but I don't see the second edit that you mentioned. Thanks for all the help!

127.0.0.1    localhost
127.0.1.1    randy-HP-Pavilion-g7-Notebook-PC

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

The second file is the /etc/hostname file.  Change the name of *randy-HP-Pavilion-g7-Notebook-PC * to a smaller name in both files.  I have  a host named **hermosa** and another named *newport*.  They don't have to be anything more than human memorable to you(no spaces please).  At the end of the day, it's just a name.  Any themes come to mind?

---

### Post by Randy M on 2012-06-06
Thanks, I have the edits made. I'll get SAMBA4 reinstalled in the next couple of days and see what happens.

---

### Post by bab1 on 2012-06-06
> **Randy M said:**
> Thanks, I have the edits made. I'll get SAMBA4 reinstalled in the next couple of days and see what happens.

[SIZE="2"]**[COLOR="Red"]DO NOT INSTALL SAMBA4![/COLOR]**[/SIZE]

Samba for is very experimental and as the developers have stated "incomplete"  It is alpha software for developers only.  The current stable version of Samba is Samba3 (3.6 I believe).  You should install *samba* not *[COLOR="Red"]samba4[/COLOR]*.

When you install *samba*, it installs version 3.

If you get requests for installing *[COLOR="Red"]samba4[/COLOR]* then you have provoked it using an incorrect command.

---

### Post by Randy M on 2012-06-07
> **bab1 said:**
> [SIZE=2]**[COLOR=Red]DO NOT INSTALL SAMBA4![/COLOR]**[/SIZE]

Samba for is very experimental and as the developers have stated "incomplete"  It is alpha software for developers only.  The current stable version of Samba is Samba3 (3.6 I believe).  You should install *samba* not *[COLOR=Red]samba4[/COLOR]*.

When you install *samba*, it installs version 3.

If you get requests for installing *[COLOR=Red]samba4[/COLOR]* then you have provoked it using an incorrect command.

Aha! The root of my problem. I'll leave it uninstalled and re-install Samba. Thanks!

---

### Post by Randy M on 2012-06-07
Still not working after re-installing samba. I get this when I try to create a share on this machine.

Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:OpenConfFile() - Unable to open configuration file "/etc/samba/smb.conf":
    Permission denied
Error loading services.


What should the permissions be on the smb.conf file?  I have:
 
Owner: Root
    Access: Read and Write
 
Group: Root
   Access: None

Others: blank
   Access: None


Should I do a complete removal and then re-install?

---

### Post by Randy M on 2012-06-08
I renamed the file and created a new one using the contents of the old. The lower permissions seem to have resolved the issue.

---

### Post by bab1 on 2012-06-09
> **Randy M said:**
> I renamed the file and created a new one using the contents of the old. The lower permissions seem to have resolved the issue.

Randy,

The permissions for the /etc/samba/smb,conf file should be:

Owner: Root
Access: Read and Write

Group: Root
Access: Read and Write

Others: 
Access: Read

---


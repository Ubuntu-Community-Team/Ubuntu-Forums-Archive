---
title: "Scanned document files do not have read permission for other users"
date: 2010-07-31
forum: General Help
---

### Post by golbez_88rule on 2010-07-31
I recently added a scanner to my Ubuntu Lucid installation and enabled network access detailed [here]("http://ubuntuforums.org/showthread.php?t=1519068").  However, when I scan documents and save the file, only my user has read and write permissions, and Group and Others have no permissions to even read the file. Hence if I try to open the file from another computer on the network, I am getting an error that there are insufficient priveleges to access the file.  I configured samba to share the directory where I scan files. How can I enable read access to scanned files for users other than myself, i.e. guest users accessing the file via the network directory?  Here are my config files that may help diagnosis the issue:

/etc/samba/smb.conf

```

[global]
workgroup = MSHOME
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share

[scanned_docs]
comment = Scanned Documents
path = /home/eric/Documents/scanned_documents
public = yes
read only = no
writable = yes
browseable = yes
available = yes
create mask = 0666
#directory mask = 0700
guest ok = yes
#force user = nobody
#force group = nogroup

[printers]
comment = All Printers
path = /var/spool/samba
browseable = no
printable = yes
guest ok = yes
read only = yes
create mask = 0700
use client driver = yes

```

/etc/default/saned
```

# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=yes

# Set to the user saned should run as
#RUN_AS_USER=root
RUN_AS_USER=saned

```

/etc/sane.d/saned.conf

```

# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=yes

# Set to the user saned should run as
#RUN_AS_USER=root
RUN_AS_USER=saned
eric@mythtvback:~/Documents/scanned_documents/health$ cat /etc/sane.d/saned.conf 
# saned.conf
# Configuration for the saned daemon

## Daemon options
# Port range for the data connection. Choose a range inside [1024 - 65535].
# Avoid specifying too large a range, for performance reasons.
#
# ONLY use this if your saned server is sitting behind a firewall. If your
# firewall is a Linux machine, we strongly recommend using the
# Netfilter nf_conntrack_sane connection tracking module instead.
#
# data_portrange = 10000 - 10100


## Access list
# A list of host names, IP addresses or IP subnets (CIDR notation) that
# are permitted to use local SANE devices. IPv6 addresses must be enclosed
# in brackets, and should always be specified in their compressed form.
#
# The hostname matching is not case-sensitive.

#scan-client.somedomain.firm
#localhost
#192.168.1.1/200
192.168.1.4
192.168.1.7
192.168.1.100
#192.168.0.1/29
#[2001:7a8:185e::42:12]
#[2001:7a8:185e::42:12]/64

# NOTE: /etc/inetd.conf (or /etc/xinetd.conf) and
# /etc/services must also be properly configured to start
# the saned daemon as documented in saned(8), services(4)
# and inetd.conf(4) (or xinetd.conf(5)).

```

listing of permissions for scanned document files:

```

-rw------- 1 eric eric  31564 2010-07-31 11:29 test permissions 2.pdf
-rw------- 1 eric eric  31670 2010-07-31 11:32 test permissions 3.pdf
-rw------- 1 eric eric  31149 2010-07-31 11:40 test permissions 4.pdf
-rw------- 1 eric eric  34379 2010-07-31 11:23 test permissions.pdf

```

---

### Post by AlphaLexman on 2010-07-31
Are you trying to automatically have read permissions when you scan a file,
Or just fix these files:
```
chmod + r *.pdf
```

---

### Post by golbez_88rule on 2010-07-31
AlphaLexman, I want each scanned file to automatically have read permissions after scanning the file.  If there is no way to make that happen, then I would use your solution to do it manually after the scan.

---

### Post by AlphaLexman on 2010-07-31
What is the result of:
```
umask
```

---

### Post by golbez_88rule on 2010-07-31
> **AlphaLexman said:**
> What is the result of:
```
umask
```

Here is the result of umask:

```

eric@mythtvback:~$ umask
0022

```

---

### Post by AlphaLexman on 2010-07-31
That's what it should be.
What are the permissions of the directory you are saving to?
(i.e., /home/eric/Documents/scanned_documents)
```
ls -l ~/Documents/
```

---

### Post by golbez_88rule on 2010-07-31
> **AlphaLexman said:**
> That's what it should be.
What are the permissions of the directory you are saving to?
(i.e., /home/eric/Documents/scanned_documents)
```
ls -l ~/Documents/
```

I checked that out earlier and it seems the permissions are just fine on that directory:
```


drwxrwxrwx 15 eric eric    4096 2010-07-25 18:02 scanned_documents

```

I tested by scanning a file and saving it just in my home directory, and the permissions on the file itself still had no read access for group and others, just read access for me (user eric).

---

### Post by AlphaLexman on 2010-07-31
This is just a shot in the dark... but what if you changed
> [scanned_docs]
comment = Scanned Documents
path = /home/eric/Documents/scanned_documents
in /etc/samba/smb.conf to:
```
[scanned_docs]
comment = Scanned Documents
path = /home/eric/Public/scanned_documents

```And re-scan something?

---

### Post by golbez_88rule on 2010-07-31
> **AlphaLexman said:**
> This is just a shot in the dark... but what if you changed
in /etc/samba/smb.conf to:
```
[scanned_docs]
comment = Scanned Documents
path = /home/eric/Public/scanned_documents

```And re-scan something?

Unfortunately I get the same results after changing the path.

---


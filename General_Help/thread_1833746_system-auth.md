---
title: "system-auth"
date: 2011-08-26
forum: General Help
---

### Post by KaySee1 on 2011-08-26
Hi,
 
Please note that I am a Linux noob, but I have many years experiance as a PC support analyst.
 
I am using Ubuntu Server 11.04 64 bit configured as Windows 2008 R2 active directory member server, and I am having problems with home directories being created at login.
 
A search produces the advice to add 'session required /lib/security/pam_mkhomedir.so' to the system-auth file, but it is already there.
 
I have noticed that the 'pam_mkhomedir.so' file doesn't exist, but it does exist in the '/lib/x86_64-linux-gnu$' directory. I changed the path in the system-auth to reflect this, but it didn't help.
 
I also noticed that the rest of the file references files in '/lib/security/$ISA' which doesn't exist, all files listed do exist in '/lib/x86_64-linux-gnu$' though.
 
What is happening? Is this file actually used or is there a nother one for 64 bit Ubuntu installations? What is '$ISA', a link?
 
And finaly should the system-auth file be edited, there is a warning at the top to say it is dynamically overwritten? Or is there a configuration utility to maintain it?
 
KaySee

---

### Post by gordintoronto on 2011-08-26
> **KaySee1 said:**
> ... I am having problems with home directories being created at login....

Perhaps you could be more specific? You expect home folders to be created, but they are not, or extraneous home folders are being created? "I do X and Y and expect Z to happen, but this other thing happens instead."

As an aside, Ubuntu Server is good for high-volume web sites, or other (database?) applications where performance is an issue. In most cases, it's a lot easier to install Ubuntu Desktop, then install the server modules you want.

For example, I have all the "LAMP" components installed on my desktop system, so I can test web site development, but I don't have to live in the command line.

---

### Post by KaySee1 on 2011-08-27
Sorry I thought I had been specific enough.
 
When a domain user logs onto the server the following error is displayed:
 
```
 
Could not chdir to home directory /home/MYDOMAIN/kaysee: No such file or directory

```
 
i.e. home directories are not created at login.
 
I understood from reading help guides and foram posts that the 'pam_mkhomedir.so' module creates home directories if they do not already exist during the login process.
 
i.e. When a domain user logs onto the server I expect a home directory to be created for him but it dosn't happen.
 
I am aware that I could have installed Desktop instead of Server and still install all the modules I want but it wouldn't have helped me in this instance; it might have been worse, what happens on Desktop if a user's home directory is missing?
 
KaySee.

---

### Post by gordintoronto on 2011-08-27
I'm out of my depth; I have no productive suggestions.

Is the domain consistent across the network? Is it all lower-case? I see many problems caused by upper-case in Linux.

---

### Post by galvatron408 on 2011-08-27
this configuration works perfectly fine for me.

ThinkPad-T61:/etc/pam.d$ cat common-session
#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
session    [default=1]            pam_permit.so
# here's the fallback if no module succeeds
session    requisite            pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
session    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
session    required    pam_unix.so 
session required        pam_mkhomedir.so skel=/etc/skel/ umask=0022
session    optional    pam_ecryptfs.so unwrap
session    optional            pam_ck_connector.so nox11
# end of pam-auth-update config

---

### Post by galvatron408 on 2011-08-27
here's an example...

ThinkPad-T61:/etc/pam.d$ ssh luser@localhost
luser@localhost's password: 
Creating directory '/home/luser'.

---

### Post by KaySee1 on 2011-08-28
Thanks galvatron408 that fixed the home directory problem.
 
I would still like to know what  '/lib/security/$ISA' means though.
 
Does anyone know a really good source of info for PAM? The man pages are rather sparse.
 
kaySee

---

### Post by galvatron408 on 2011-08-28
the $ISA is a variable. I do not know what it is since that variable doesn't exist on my system. Maybe you installed something that added it or maybe someone created it.

Pam is actually pretty simple and pretty powerful. You're going to want to read the pam systems administrator guide.

[http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html)

---


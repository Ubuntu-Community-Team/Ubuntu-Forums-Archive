---
title: "passwd: Authentication information cannot be recovered"
date: 2010-11-30
forum: General Help
---

### Post by Mynamedoesntfi on 2010-11-30
Hey guys,

Not sure what the go is with this, however I've seemingly lost the ability to reset passwords of other users.

For example, I can su to root and change the password for root.

However, I cannot change the password for other users.


root@server:/etc# passwd bobtest
passwd: Authentication information cannot be recovered
passwd: password unchanged


Not, as far as I understand it, this is normally a pam issue.

# here are the per-package modules (the "Primary" block)
password        requisite                       pam_krb5.so minimum_uid=1000
password        [success=1 default=ignore]      pam_unix.so obscure try_first_pass sha512
# here's the fallback if no module succeeds
password        requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password        required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
password        optional        pam_gnome_keyring.so
# end of pam-auth-update config




To give more info, if I add a user it will work.... but I cannot set a password for them and while I can SU to the new user, I cannot set a password either.


root@server:/etc# useradd bobtest
root@server:/etc# su bobtest
$ passwd
passwd: Authentication information cannot be recovered
passwd: password unchanged
$ exit
root@server:/etc# userdel bobtest
root@server:/etc# adduser bobtest
Adding user `bobtest' ...
Adding new group `bobtest' (1021) ...
Adding new user `bobtest' (1021) with group `bobtest' ...
Creating home directory `/home/bobtest' ...
Copying files from `/etc/skel' ...
passwd: Authentication information cannot be recovered
passwd: password unchanged
Try again? [y/N] y





root@server:/etc# passwd bobtest
passwd: Authentication information cannot be recovered
passwd: password unchanged


I'm not sure what the problem is...and I have no idea how long this has been a problem, as I havent added any new users for quite some time (this was originally just a test server).


I'm still a bit of a newbie so please be gentle ;)

---

### Post by galvatron408 on 2010-12-01
that error usually means that the system is trying to change the password somewhere besides the local system. take a look at your nsswitch file. does it look like mine (below)? (my file is default)

you'll also want to look at all of your pam common-* files and make sure you are using pam_unix and not something else like pam_ldap.

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by Mynamedoesntfi on 2010-12-01
Yep, nsswitch.conf is exactly the same as that.

---

### Post by darryn.smith on 2010-12-28
Good Day, 

Sorry for the late reply. I had this issue pop up for me today. 

Here's what it ended up being on my end:

check /etc/pam.d/common-password

password       requisite                       pam_krb5.so minimum_uid=1000
password        [success=2 default=ignore]      pam_unix.so obscure try_first_pass sha512
password        [success=1 default=ignore]      pam_winbind.so try_first_pass


That 1st line 'password       requisite                       pam_krb5.so minimum_uid=1000'  was the culprit.  Likely from months ago when I was mucking around with Kerberos.  Just comment it out. Or remove it.  

Hope that works for you.

---


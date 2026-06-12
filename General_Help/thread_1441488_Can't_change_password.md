---
title: "Can't change password"
date: 2010-03-28
forum: General Help
---

### Post by Corfy on 2010-03-28
I'm having a problem with passwords.

I go to System->Preferences->About Me and click on "Change Password". It then asks to authenticate the existing password. But it won't authenticate. I can log in just fine using the same password, but this won't authenticate it.

I tried opening terminal and running passwd, sudo passwd, and even sudo passwd {user}, but all of them fail.

This system has two users (both with sudo privileges), so even though I didn't really want to change the password on the other user, I logged in and tried all of the same steps from above. That was also unsuccessful.

BTW, if I run sudo with another command, the passwords work fine, and I have no trouble logging in. I just can't change them.

I am running 10.04. I've had Ubuntu on this computer since 8.04 (doing an in-place upgrade with each release), but this time I did a fresh install of the root folder, but kept the /home files in a different partition.

---

### Post by Corfy on 2010-03-28
BTW, I mentioned that the command passwd "failed", but I guess I should have included the actual error message:

passwd: System error
passwd: Password unchanged

---

### Post by Kevinator on 2010-03-28
Damn, that's kind of weird. Can you post the content of /etc/pam.d/passwd and /etc/pam.d/common-password?

---

### Post by Kevinator on 2010-03-28
Also /etc/nsswitch.conf, just in case.

---

### Post by Corfy on 2010-03-28
Here you go.

/etc/pam.d/passwd:
> #
# The PAM configuration file for the Shadow 'passwd' service
#

@include common-password

/etc/pam.d/common-password
> #
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define the services to be
# used to change user passwords.  The default is pam_unix.

# Explanation of pam_unix options:
#
# The "sha512" option enables salted SHA512 passwords.  Without this option,
# the default is Unix crypt.  Prior releases used the option "md5".
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs.
#
# See the pam_unix manpage for other options.

# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
password	[success=1 default=ignore]	pam_unix.so obscure sha512
# here's the fallback if no module succeeds
password	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
password	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
password	optional	pam_gnome_keyring.so 
# end of pam-auth-update config


/etc/nsswitch.conf
> # /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the 'glibc-doc-reference' and 'info' packages installed, try:
# 'info libc "Name Service Switch"' for information about this file.

passwd:		compat
group:		compat
shadow:		compat

hosts: 		files mdns4_minimal [NOTFOUND=return] dns mdns4
networks: 	files

protocols:	db files
services:	db files
ethers: 	db files
rpc: 		db files

netgroup:	nis


---

### Post by Kevinator on 2010-03-28
Everything there looks fine. I think it's all identical to mine, and just to be sure I changed my password with 'passwd' and there was no problem.

We might be able to narrow down where the error is occurring with this:

strace -f -o trace.txt passwd

That will run passwd, but will also trace all the system calls it performs and write them to trace.txt. Don't enter your real password when prompted, because it might end up in the trace file. I'm not sure this will tell us anything useful, and to be honest I'm not sure that it won't reveal any sensitive information, but I don't see how it could. The trace is a rather large file, so you'll want to attach it rather than paste it inline (if that's possible).

---

### Post by Kevinator on 2010-03-28
Something else you might try is checking /var/log/auth.log. You might not want to post the whole thing, but the timestamps in the log should tell you what lines are associated with a particular passwd-attempt.

---

### Post by Kevinator on 2010-03-28
Thinking about this a bit more, it wouldn't hurt to make sure the permissions and ownership are correct on /etc/passwd and /etc/shadow. passwd should be -rw-r--r-- root:root, and shadow should be -rw-r----- root:shadow.

/etc/shadow (and maybe /etc/passwd) has to be writable to change passwords, so its partition needs to be mounted read-write. The surest way to test writability would be to edit /etc/shadow itself, but I wouldn't do that. There are plenty of files in /etc that you can safely edit to make sure they are writable. Try /etc/bash.bashrc or /etc/hosts. Just try adding a blank line and saving, or something like that. You can immediately revert the change.

---


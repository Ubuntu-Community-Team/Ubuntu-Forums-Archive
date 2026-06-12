---
title: "Cannot change password (Module unknown)"
date: 2012-05-04
forum: General Help
---

### Post by ufuser01 on 2012-05-04
Hi, 
**EDIT: I tried to recover the password sometime back using a live CD, but I could change the password after that, but not now.**
I am facing an unusual issue. I am unable to change the password. I am guessing it has something to do with PAM, but I am not sure what.  Any ideas? Below is what I see:
```

~$passwd
Changing password for my_user_name.
(current) UNIX password: 
passwd: Module is unknown
passwd: password unchanged
```Below info is what was asked in other threads:
```


~$sudo pam-auth-update &#8211;force

~$ which passwd
/usr/bin/passwd

~$sudo grep -i my_user_name /etc/shadow
[sudo] password for my_user_name: 
my_user_name:$very_long_hashed_password_alpha_numeric_string$:15294:7:180:14:::

~$ grep -i my_user_name /etc/passwd
my_user_name:x:1000:1000:my_user_name,,,:/home/my_user_name:/bin/bash

~$ cat /etc/pam.d/passwd
# The PAM configuration file for the Shadow `passwd' service
@include common-password

~$ cat /etc/pam.d/common-password 
password    requisite            pam_passwdqc.so 
password    [success=1 default=ignore]    pam_unix.so obscure use_authtok try_first_pass sha512
password    optional    pam_gnome_keyring.so 
password    optional    pam_ecryptfs.so 
password required pam_cracklib.so try_first_pass retry=3 minclass=3 lcredit=-1 dcredit=-1 ucredit=-1 ocredit=-1 minlen=12
password required pam_unix.so nullok shadow try_first_pass use_authtok remember=8 md5

~$ cat /etc/pam.d/common-auth
auth    [success=1 default=ignore]    pam_unix.so nullok_secure
auth    requisite            pam_deny.so
auth    required            pam_permit.so
auth    optional    pam_ecryptfs.so unwrap
auth        required      pam_tally2.so deny=3
account    required          pam_tally2.so

~$ sudo pam_tally --reset --user my_user_name
[sudo] password for my_user_name: 
User my_user_name    (1000)    had 0

```When I tried to install libpam-cracklib, this is the message I got:

Incompatible PAM profiles selected.
```

The following PAM profiles cannot be used together:    
passwdqc password strength enforcement, Cracklib password strength    
checking  
Please select a different set of modules to enable.  

```I am able to login with my existing password etc, but I cannot change it. I tried the following methods WITHOUT success:

Thanks.

[B]EDIT:
I installed libpam-cracklib and ignored the warning I mentioned above and I could change the password, but still there is an issue; When I type and re-type the password, I get this message[/B]
```

~$ passwd
Changing password for my_user_name.
(current) UNIX password: 
You can now choose the new password or passphrase
** PASSWORD RULES INFO ** 
Enter new password: 
Re-type new password: 
Retype new password: 
passwd: Authentication failure
passwd: password unchanged

```Since, it says failure, I try again, but I cannot login; But, my new password works. ie, The password changes, but I get a message saying "password unchanged".  Any ideas?

---

### Post by cmont899 on 2012-05-04
[B]What are the contents of the file /etc/pam.d/passwd and any includes contained within?

[/B]

---

### Post by ufuser01 on 2012-05-04
Hi,

Thanks. This is the only uncommented line in that file:

```
@include common-password
```

Also, I updated my post with additional info, if that helps. 

Thanks. 

> **cmont899 said:**
> What are the contents of the file /etc/pam.d/passwd and any includes contained within?



---

### Post by philinux on 2012-05-04
> **ufuser01 said:**
> Hi,

Thanks. This is the only uncommented line in that file:

```
@include common-password
```

Also, I updated my post with additional info, if that helps. 

Thanks.

This looks promising.

[http://ubuntuforums.org/showthread.php?t=1150786](http://ubuntuforums.org/showthread.php?t=1150786)

---

### Post by cmont899 on 2012-05-04
Contents of /etc/pam.d/common-password please

---

### Post by ufuser01 on 2012-05-04
Thanks, here it is 
```

password        requisite                       pam_passwdqc.so
password        [success=1 default=ignore]      pam_unix.so obscure use_authtok try_first_pass sha512

# here's the fallback if no module succeeds
#password       requisite                       pam_deny.so

# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
#password       required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
password        optional        pam_gnome_keyring.so
password        optional        pam_ecryptfs.so

# end of pam-auth-update config
password required pam_cracklib.so try_first_pass retry=3 minclass=3 lcredit=-1 dcredit=-1 ucredit=-1 ocredit=-1 minlen=12
password required pam_unix.so nullok shadow try_first_pass use_authtok remember=8 md5


```

> **cmont899 said:**
> Contents of /etc/pam.d/common-password please

---

### Post by cmont899 on 2012-05-04
Both cracklib and passwdqc are used for password strength checking, try commenting out the cracklib line and see if things get better:



password    requisite            pam_passwdqc.so 
password    [success=1 default=ignore]    pam_unix.so obscure use_authtok try_first_pass sha512
password    optional    pam_gnome_keyring.so 
password    optional    pam_ecryptfs.so 
#password required pam_cracklib.so try_first_pass retry=3 minclass=3 lcredit=-1 dcredit=-1 ucredit=-1 ocredit=-1 minlen=12
password required pam_unix.so nullok shadow try_first_pass use_authtok remember=8 md5

---


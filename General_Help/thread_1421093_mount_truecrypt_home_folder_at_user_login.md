---
title: "mount truecrypt home folder at user login"
date: 2010-03-03
forum: General Help
---

### Post by Kradziej on 2010-03-03
Hi all

I`m trying to mount crypted home folder at startup, but I want to only prompt for mount when main user is starting session, not for all users.
I`ve edited gdm PostLogin with it:

> 
zenity --title "lol" --question --text "Mount home folder?"


if [ $? -eq 0 ]
then
 truecrypt /home/workimage /home/anon
 
 if [ $? -eq 0 ]
 then
  exit 0
 else
  service gdm restart
 fi

else
 exit 0
fi


I can`t get user name or something to test in PostLogin. Mounting in PreSession is too late. Is this any way to do this, maybe not by gdm?

---

### Post by Kradziej on 2010-03-04
Bampo

---

### Post by undecim on 2010-03-04
You might have to mess around with PAM modules. This is how ecryptfs (the encryption option you have when installing Ubuntu) does it.

But there's a problem: How does your computer get the key to decrypt it? ecryptfs uses a key that is "wrapped" with your passphrase and stored on your drive so that it can unlock it when you log in. Without writing a new PAM module, that could be pretty difficult.

---

### Post by Kradziej on 2010-03-04
Ok so undecim u`re right I got it to work by PAM modules (2 days lost ;/), now I understand how authentication system works

Maybe someone need it:

1.Edit /etc/pam.d/gdm

> 
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth [default=1 success=ignore]	pam_succeed_if.so quiet user = user_name <---#add this
auth requisite	pam_exec.so quiet /usr/bin/mount_homedir  <-------#add this
auth 	sufficient 	pam_listfile.so item=user sense=allow file=/etc/gdm/nopassusers.txt onerr=fail
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password



2. Make /usr/bin/mount_homedir (or whatever u want and edit gdm file)

> 

#!/bin/sh

if [ -e /dev/mapper/truecrypt1 ]
then
 exit 0
else
 export DISPLAY=:0.0
 truecrypt /home/workimage /home/user_name
 if [ $? -eq 1 ]
 then
  exit 1
 fi
fi

exit 0




Now if u login to user_name u`ll be asked for the password, if u enter wrong pass, system won`t authenticate u. If u login to another user, system won`t prompt for the password. That`s all

---

### Post by swissz on 2010-11-24
> **Kradziej said:**
> Ok so undecim u`re right I got it to work by PAM modules (2 days lost ;/), now I understand how authentication system works

Maybe someone need it:

1.Edit /etc/pam.d/gdm



2. Make /usr/bin/mount_homedir (or whatever u want and edit gdm file)




Now if u login to user_name u`ll be asked for the password, if u enter wrong pass, system won`t authenticate u. If u login to another user, system won`t prompt for the password. That`s all

Hi Kradziej!
Thanks for the howto!
Unfortunatelly it doesn't work for me. When I log in, it doesn't ask for the truecrypt password, just begin to complain, that some directories are missing...
It's not clear though, whether the truecrypt volume should have the same password as the login password, or is it irrelevant. When you say it should ask for the password, do you mean the user-login password in gdm, or the truecrypt password?

My truecrypt volume is not in a file-container, but a whole partition.
In the /usr/bin/mount_homedir file I have the device name instead of the container:
truecrypt /dev/sda10 /home/user

I have truecrypt 7.10, Ubuntu Karmic (9.10).

---


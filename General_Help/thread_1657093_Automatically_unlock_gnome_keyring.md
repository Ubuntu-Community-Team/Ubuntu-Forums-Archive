---
title: "Automatically unlock gnome keyring"
date: 2010-12-31
forum: General Help
---

### Post by GrdLock02 on 2010-12-31
I've done the process with no problem on Ubuntu, but I can't get it working with Lubuntu.

I installed the pam package. I then added the @include common-pamkeyring line to my /etc/pam.d/lxdm file.

Here's my complete /etc/pam.d/lxdm file:

```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinu$
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinu$
session optional        pam_gnome_keyring.so auto_start
@include common-password
@include common-pamkeyring
```

Am I doing something wrong? Does something have to be done differently in LXDE?

---

### Post by andrewbrown22 on 2011-06-10
Man I really wish someone would take a look at this and let us know how to do this...or... OP: did you figure out how to do this?

---

### Post by michaelb28 on 2011-09-20
I've got the same problem on Lubuntu Natty. It looks like my /etc/pam.d/ config files were preconfigured correctly. I installed the libpam-gnome-keyring package but all that did was grey out the option to automatically unlock the keyring.

I'm getting some error messages in /var/log/auth.log:
```
Sep 20 11:41:10 asnlb gnome-keyring-daemon[3795]: GLib-GIO: Using the 'memory' 
GSettings backend.  Your settings will not be saved or shared with other applic
ations.
Sep 20 11:41:10 asnlb gnome-keyring-daemon[3795]: couldn't set environment vari
able in session: The name org.gnome.SessionManager was not provided by any .ser
vice files
Sep 20 11:41:11 asnlb polkitd(authority=local): Registered Authentication Agent
 for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.41 [
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /o
rg/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Sep 20 11:41:14 asnlb gnome-keyring-daemon[3795]: unsupported key algorithm in 
certificate: 1.2.840.10045.2.1
Sep 20 11:41:17 asnlb gnome-keyring-prompt: could not grab keyboard: 1
Sep 20 11:41:17 asnlb gnome-keyring-daemon[3795]: ** Message: could not grab keyboard: 1

```

I think I came across a website where some folks using Fedora & LXDE were talking about a bug on this issue.

---

### Post by michaelb28 on 2011-09-21
Hi, I just got it working.  I'm not sure if the OP is still around, but maybe this will help someone else.

I came across this thread and credit user Arlanthir for the solution:
[http://ubuntuforums.org/showthread.php?p=9938975](http://ubuntuforums.org/showthread.php?p=9938975)

His solution was to delete the default keyring and set the login keyring as default. (Warning: This will delete any passwords saved in the keyring).
> System > Preferences > Passwords and Encryption Keys

Right click on the default keyring, delete
Right click the login keyring, set as default

Notice the window will not update, don't be alarmed if the keyring doesn't disappear when you delete it 

Note: You can install seahorse to get the Passwords and Encryption Keys program to appear on the start menu. It was not preinstalled on my Lubuntu system.

I'd think that libpam-gnome-keyring also is required, which I had installed prior to this.

Now I can automatically unlock the keyring whenever I login to Lubuntu.

---

### Post by countryranger on 2012-03-26
The problem I had was that after I set Lubuntu up not to ask for my password on startup, it kept asking for my keyring password.  It turns out if you have Ubuntu One open on start up it asks for the password from Keyring and if you auto signed in or without a password, you need to enter it again.

---

### Post by ohnonot on 2012-03-30
> **countryranger said:**
> The problem I had was that after I set Lubuntu up not to ask for my password on startup, it kept asking for my keyring password.  It turns out if you have Ubuntu One open on start up it asks for the password from Keyring and if you auto signed in or without a password, you need to enter it again.same thing here.
meaning the above solution doesn't apply because the passwords in question are in the login keyring anyway
:confused:

---

### Post by michaelb28 on 2012-03-30
I might be addressing a different scenario then.

I was having to enter a password twice on startup:  Once to login to Lubuntu and once immediately afterwards to unlock the keyring.

Now I just have to enter the login password and it unlocks the keyring automatically.

-Michael

---

### Post by ohnonot on 2012-03-31
actually i did remove it.
a bit tricky -
installed seahorse first, then i deleted the default keyring, which was the login keyring, too.
after reboot it asks me lots of passwords, but when it asks me the password for the default keyring i leave that empty despite warnings!
the tricky thing was, i couldn't remove the password (leave it blank) from within seahorse.

---


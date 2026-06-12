---
title: "&quot;Login automatically&quot; does not work in Natty"
date: 2011-10-05
forum: General Help
---

### Post by bigred1 on 2011-10-05
I was using "Automatic Login" fine in Maverick, Lucid and earlier versions. After upgrading to Natty it does not work. A password is required on bootup.

The Login Settings GUI shows that it is configured correctly. Please see image. How can I make automatic login work?


Edit: RESOLVED. See below.

---

### Post by AskTell on 2011-10-05
i noticed your login screen settings menu had "Ubuntu" as its  default session instead of GNOME
this may have something to do with it but I don't really know, I'm still on my first cup:)
/etc/gdm/custom.conf holds my login settings
contents of my custom.conf

[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=josh
AutomaticLogin=josh
TimedLoginDelay=13
DefaultSession=gnome

all files under the etc/gdm directory and permissions.

4 -rw-r--r--   1 root root   135 2011-10-05 17:45 custom.conf
 4 -rw-r--r--   1 root root   132 2010-04-01 06:07 failsafeBlacklist
12 -rwxr-xr-x   1 root root  8778 2010-04-01 06:07 failsafeXinit
 8 -rwxr-xr-x   1 root root  4778 2010-04-01 06:07 failsafeXServer
 4 -rw-r--r--   1 root root  3157 2010-04-14 18:50 gdm.schemas
 4 drwxr-xr-x   2 root root  4096 2011-06-25 13:29 Init
 4 drwxr-xr-x   2 root root  4096 2011-06-25 13:29 PostLogin
 4 drwxr-xr-x   2 root root  4096 2011-06-25 13:29 PostSession
 4 drwxr-xr-x   2 root root  4096 2011-06-25 13:29 PreSession
 8 -rwxr-xr-x   1 root root  6111 2011-04-28 03:07 Xsession

./Init:
total 12
4 drwxr-xr-x 2 root root 4096 2011-06-25 13:29 .
4 drwxr-xr-x 6 root root 4096 2011-10-05 17:45 ..
4 -rwxr-xr-x 1 root root 2791 2010-04-14 18:50 Default

./PostLogin:
total 12
4 drwxr-xr-x 2 root root 4096 2011-06-25 13:29 .
4 drwxr-xr-x 6 root root 4096 2011-10-05 17:45 ..
4 -rwxr-xr-x 1 root root  441 2010-04-14 18:50 Default.sample

./PostSession:
total 12
4 drwxr-xr-x 2 root root 4096 2011-06-25 13:29 .
4 drwxr-xr-x 6 root root 4096 2011-10-05 17:45 ..
4 -rwxr-xr-x 1 root root   18 2010-04-14 18:50 Default

./PreSession:
total 12
4 drwxr-xr-x 2 root root 4096 2011-06-25 13:29 .
4 drwxr-xr-x 6 root root 4096 2011-10-05 17:45 ..
4 -rwxr-xr-x 1 root root  400 2010-04-14 18:50 Default

heres more information from the forum

[http://ubuntuforums.org/showthread.php?t=1209043](http://ubuntuforums.org/showthread.php?t=1209043)

one guy suggests running this command which didn't help the person in that thread but might help you
sudo dpkg-reconfigure xserver-xorg

GL!

---

### Post by bigred1 on 2011-10-06
My conf file also has ```
DefaultSession=gnome
```.

Reconfiguring the XServer is a broad step, which does not work.

It seems we need a solution to the specific problem  -- the failure of automatic login.

---

### Post by Krytarik on 2011-10-06
Are you sure that you aren't asked for a keyring password instead, *after* the automatic login?

Greetings.

---

### Post by bigred1 on 2011-10-10
Thanks, I checked, and it really is a non-automatic login.

Can you suggest how to configure automatic login using the command line or config files? This might  allow me to bypass the problem.

---

### Post by raja.genupula on 2011-10-10
> **bigred1 said:**
> Thanks, I checked, and it really is a non-automatic login.

Can you suggest how to configure automatic login using the command line or config files? This might  allow me to bypass the problem.

Hi

please go with this

[http://ubuntuforums.org/showthread.php?t=1012602](http://ubuntuforums.org/showthread.php?t=1012602)

---

### Post by Krytarik on 2011-10-10
> **bigred1 said:**
> Can you suggest how to configure automatic login using the command line or config files?
It's like *AskTell* already indicated:
> **AskTell said:**
> 
/etc/gdm/custom.conf holds my login settings
contents of my custom.conf

[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=josh
AutomaticLogin=josh
TimedLoginDelay=13
DefaultSession=gnome

---

### Post by bigred1 on 2011-10-10
Thank you. My ```
/etc/gdm/custom.conf
``` is as follows. Appears to be the correct configuration, but -- no auto-login.

```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=fox
TimedLoginEnable=false
TimedLogin=fox
TimedLoginDelay=1
DefaultSession=gnome
```

---

### Post by bigred1 on 2011-10-16
Issue resolved as follows.

Upgraded to Ubuntu  11.10 Oneiric.

Chose user name on upper right of desktop.

Chose "User Accounts."

"Automatic Login" was set to OFF. Changed it to ON.

---

### Post by Krytarik on 2011-10-16
> **bigred1 said:**
> Issue resolved as follows.

Upgraded to Ubuntu  11.10 Oneiric.

Chose user name on upper right of desktop.

Chose "User Accounts."

"Automatic Login" was set to OFF. Changed it to ON.
Yeah, this is LightDM now, not GDM anymore, on which your initial issue was based. ;-)

However, glad that at least *this* works now!

---


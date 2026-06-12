---
title: "How to disable the password prompt on login?"
date: 2010-11-12
forum: General Help
---

### Post by nnn= on 2010-11-12
I click on the corresponding checkbox in users and groups but but it doesn't do anything. I also want to disable password prompts in general. Also when I try using Computer Janitor it says it could not complete and to check if other package managers are open, but none are.

---

### Post by coffeecat on 2010-11-12
Log in prompt: System > Administration > Login Screen. Unlock window and tick box for log in automatically.

To stop the screen locking and requiring password when you leave it for a few minutes: System > Preferences > Screensaver. Untick 'Lock screen'. Also - System > Preferences > Power Management. Put computer to sleep when inactive = never.

Disabling other password prompts for sudo, adminstrative GUI apps, etc: **BAD** idea.

---

### Post by nnn= on 2010-11-12
In  System > Administration > Login Screen: I press unlock but nothing happens.

---

### Post by gupti on 2010-11-12
That's strange. I tested clicked it and it gave me a password prompt, so then I could change the settings.

---

### Post by nnn= on 2010-11-12
So what can I do about it?

---

### Post by coffeecat on 2010-11-13
> **nnn= said:**
> So what can I do about it?

What checkbox did you tick in users and groups? Did you by chance inadvertently remove yourself from the admin group?

Go to User and Groups and highlight your account name. Click on Advanced Settings. Do you get a password prompt?

---

### Post by nnn= on 2010-11-13
I don't think I ticked anything in users and groups. I checked in manage groups and it seems I'm still part of admin group. But when I press on advanced settings I don't get a password prompt.

---

### Post by kerry_s on 2010-11-13
see pic

---

### Post by nnn= on 2010-11-15
-

---

### Post by nnn= on 2010-11-15
I still can't tick that box. I need help to figure out what's going on. And the package manager issue wasn't addressed at all.

---

### Post by sisco311 on 2010-11-15
Hmmm, please post the output of:
```
groups
groups $USER
```
```
grep nopasswd /etc/pam.d/gdm
grep nopasswd /etc/group
```
and
```
pgrep -lf polkit
```

---

### Post by sikander3786 on 2010-11-15
> And the package manager issue wasn't addressed at all.

Are you sure anyother package manager like Synaptic, apt-get, Software Center or Update Manger is not running while you run Computer Janitor?

A simple reboot might fix that error.

Even after reboot, if the error persists, from Terminal please post the output of

```
sudo apt-get update
```

---

### Post by nnn= on 2010-11-17
groups
```
n adm dialout cdrom audio plugdev lpadmin admin sambashare
```groups $USER
```
n : n adm dialout cdrom audio plugdev lpadmin admin sambashare
```grep nopasswd /etc/pam.d/gdm
```
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
```grep nopasswd /etc/group
```
nopasswdlogin:x:126:
```pgrep -lf polkit
```
1225 /usr/lib/policykit-1/polkitd
```sudo apt-get update
```

[sudo] password for n: 
Hit http://archive.canonical.com maverick Release.gpg
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                  
Get:1 http://extras.ubuntu.com maverick Release.gpg [65B]                                 
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                         
Hit http://security.ubuntu.com maverick-security Release.gpg                               
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en               
Hit http://us.archive.ubuntu.com maverick Release.gpg                                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                   
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US                
Hit http://archive.canonical.com maverick Release                                          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US            
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release             
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Hit http://extras.ubuntu.com maverick Release                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US       
Hit http://archive.canonical.com maverick/partner i386 Packages                            
Hit http://us.archive.ubuntu.com maverick Release                                          
Hit http://us.archive.ubuntu.com maverick-updates Release                                  
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages                  
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Hit http://security.ubuntu.com maverick-security/main i386 Packages  
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/main Sources               
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Fetched 65B in 1s (47B/s)
Reading package lists... Done

```I just used the update manager to check for updates and there are several but when I click on install I don't get any prompts. I just recently upgraded from 9.04 (via recommended procedure) and since then have been experiencing several problems. I don't know if it's relevant, but for instance I have to choose safe mode when logging in, otherwise after the desktop shows, the login prompt returns. While in 9.04 I set it to login automatically and it worked fine.

---

### Post by sisco311 on 2010-11-17
See:
[http://ubuntuforums.org/showpost.php?p=10010966&postcount=10](http://ubuntuforums.org/showpost.php?p=10010966&postcount=10)

---

### Post by nnn= on 2010-11-19
This resolved the above problems. Computer Janitor also required  authentication. I suppose I need to choose safe mode when logging in,  because my computer does not support some features in regular mode.  Could you tell me why I had this authentication problem?

---

### Post by sisco311 on 2010-11-19
> **nnn= said:**
> I suppose I need to choose safe mode when logging in,  because my computer does not support some features in regular mode.

I don't think so, I think there is something wrong with the video driver. Start a new topic about this issue. You will get better answers.

---

### Post by nnn= on 2010-11-27
> **sisco311 said:**
> See:
[http://ubuntuforums.org/showpost.php?p=10010966&postcount=10](http://ubuntuforums.org/showpost.php?p=10010966&postcount=10)

This works, but turns out even though I followed the instructions, it doesn't load on startup. How can I make it do so?

So when I update I do
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 & disown
```

and get
```
(polkit-gnome-authentication-agent-1:3054): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:3054): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

```

But this works and I get an authentication prompt in update manager.

---

### Post by nnn= on 2010-11-27
Help.

---

### Post by nnn= on 2010-12-03
Help.

---


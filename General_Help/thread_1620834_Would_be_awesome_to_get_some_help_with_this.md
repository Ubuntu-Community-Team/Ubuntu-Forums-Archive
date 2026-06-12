---
title: "Would be awesome to get some help with this"
date: 2010-11-13
forum: General Help
---

### Post by U_buntu on 2010-11-13
Spent 20 minutes trying to log in. I click login and it starts to load, goes to a black screen, then starts to load, then to a black screen again, then back to the login screen. Eventually I get in, but its always random.

---

### Post by arpanaut on 2010-11-13
Need more info, system specs, especially your video card.
What version of Ubuntu are you running?

---

### Post by U_buntu on 2010-11-14
9.10 nividia, but havnt had this proble till recently.

---

### Post by sikander3786 on 2010-11-14
Is compiz enabled?

You mentioned you could login, but it is random. If compiz is enabled, try disabling it and again try log out/log in or a restart. I guess it would be compiz causing problems.

Is this the default Ubuntu install with Gnome and GDM or it is Kubuntu?

---

### Post by U_buntu on 2010-11-14
not sure where to look to see if compiz is enabled, but I'll get on that. And its the gnome

---

### Post by sikander3786 on 2010-11-15
> **U_buntu said:**
> not sure where to look to see if compiz is enabled, but I'll get on that. And its the gnome
Go to System > Preferences > Appearance > Visual Effects Tab and select None.

---

### Post by U_buntu on 2010-11-15
None is already selected

---

### Post by dino99 on 2010-11-15
check driver activation: system admin driver (or so)

sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -phigh -a

---

### Post by U_buntu on 2010-11-15
I have run those commands, what now?

---

### Post by sikander3786 on 2010-11-15
> **U_buntu said:**
> I have run those commands, what now?
Did any of them report an error?

Did you try log out/log in to see if those commands helped?

---

### Post by U_buntu on 2010-11-15
I couldnt tell if there was an error or not, so heres what I got

dpkg: conflicting actions -p (--print-avail) and -

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !


I'm new to both linux as well as Ubuntu, But I'm getting around. I did not however, log out then log back in, I've had this issue for over a month, and I'm kinda tired of playing login-tag

---

### Post by sikander3786 on 2010-11-15
> **U_buntu said:**
> I couldnt tell if there was an error or not, so heres what I got

dpkg: conflicting actions -p (--print-avail) and -

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !


I'm new to both linux as well as Ubuntu, But I'm getting around. I did not however, log out then log back in, I've had this issue for over a month, and I'm kinda tired of playing login-tag
I think there is a syntax error in dino99's command.

Try this one.

```
sudo dpkg-reconfigure -phigh -a
```

---

### Post by SeijiSensei on 2010-11-15
I recommend selecting the "console login" option and booting up into that.  Log in, then type "startx" at the prompt and see what happens.  My bet is you'll get some type of error about xorg.conf and the nvidia driver.

If you can't find the console login option, you can choose to boot into "rescue mode" (I think that's what it's called.).  Type "su" followed by your username at the prompt to acquire your identify then run "startx".  Running startx without the "su username" step will try and run X Windows as the root user.  That will also tell you what's wrong if it's an xorg.conf misconfiguration.

---

### Post by U_buntu on 2010-11-15
Ok with that command I get

 * Disabling power management...                                         [ OK ] 
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 * Checking battery state...                                             [ OK ] 
acpid stop/waiting
acpid start/running, process 7867
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
dpkg-trigger: dpkg-trigger must be called from a maintainer script (or with a --by-package option)

---

### Post by sikander3786 on 2010-11-15
> **U_buntu said:**
> Ok with that command I get

 * Disabling power management...                                         [ OK ] 
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 * Checking battery state...                                             [ OK ] 
acpid stop/waiting
acpid start/running, process 7867
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
dpkg-trigger: dpkg-trigger must be called from a maintainer script (or with a --by-package option)
Thats seems successful however it should be a long list of text. Anyways, tell us the next time you try logging in from GDM if the problem persists or it is gone.

---

### Post by U_buntu on 2010-11-17
Still having the same problem.

---


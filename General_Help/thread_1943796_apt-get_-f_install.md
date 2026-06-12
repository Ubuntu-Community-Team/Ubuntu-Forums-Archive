---
title: "apt-get -f install"
date: 2012-03-20
forum: General Help
---

### Post by mohanradhakrishnan on 2012-03-20
[RIGHT]Hi,[/RIGHT]
I think "apt-get -f install" was a mistake because it removed lot of packages. So with my limited knowledge of Ubuntu I executed
 
apt-get --fix-missing install
apt-get update
apt-get upgrade
apt-get dist-upgrade
 
I also thought Unity was the problem. So I tried to install gnome by executing
 
apt-get install gnome-session-fallback
 
Can anyone point out the error in what I have attempted ?
 
Update: Version is 11.10. It might not be relevant but I tried to install libgtk2.0-dev and gradually messed up. Now it is just that the initial ubuntu screen appears and does not proceed to the login page. I think it shuts down. I have tried all the commands in the recovery mode.
 
Thanks,
Mohan

---

### Post by winh8r on 2012-03-20
Firstly, it would be better to know what problem you were trying to fix before you entered these commands.

Was it an update issue?

An installing new software issue?

So if you can tell us what the initial problem was, and what the problem is now then someone may be able to help you resolve the issue.

Also tell us which version of ubuntu you are using.

Hope this helps.

---

### Post by mohanradhakrishnan on 2012-03-20
Version is 11.10. It might not be relevant but I tried to install libgtk2.0-dev and gradually messed up. Now it is just that the initial ubuntu screen appears and does not proceed to the login page. I think it shuts down. I have tried all the commands in the recovery mode.
 
Thanks,
Mohan

---

### Post by matt_symes on 2012-03-20
Hi

Morning winh8r.

11.10 uses gtk3. Any reason for gtk2 ?

I would remove libgtk2-dev (at least for the moment) and reinstall ubuntu-desktop from the recovery console. You can get to the via the GRUB menu.

```
apt-get remove --purge libgtk2-dev
```

```
apt-get remove --purge ubuntu-desktop
```

```
apt-get install ubuntu-desktop
```

It's easier than chrooting from a LiveCD/USB. See where that gets you for a start.

This is its dependencies. It looks like you may have had a conflict somewhere.

```
matthew@matthew-Aspire-7540:~$ apt-cache show libgtk2.0-dev | grep -i depends
Depends: libgtk2.0-0 (= 2.24.10-0ubuntu5), libgtk2.0-common, libglib2.0-dev (>= 2.27.3), libgdk-pixbuf2.0-dev (>= 2.21.0), libpango1.0-dev (>= 1.20), libatk1.0-dev (>= 1.29.2), libcairo2-dev (>= 1.6.4-6.1), libx11-dev (>= 2:1.0.0-6), libxext-dev (>= 1:1.0.1-2), libxinerama-dev (>= 1:1.0.1-4.1), libxi-dev (>= 1:1.0.1-4), libxrandr-dev (>= 1:1.2.99), libxcursor-dev, libxfixes-dev (>= 1:3.0.0-3), libxcomposite-dev (>= 1:0.2.0-3), libxdamage-dev (>= 1:1.0.1-3), pkg-config (>= 0.26-1), libxml2-utils, gir1.2-gtk-2.0
matthew@matthew-Aspire-7540:~$ 
```

What packages did it remove ?

Kind regards

---

### Post by mohanradhakrishnan on 2012-03-22
Hello,
Thanks. After removing libgtk2.0-dev I installed ubuntu-desktop. When I checked for ubuntu-desktop before that it wasn't there. Looks like apt-get -f install removed it.
 
Now I see from the recovery mode that firefox, libreoffice and I presume everything related to the desktop got installed. It finished successfully.
 
When I booted in normal mode there was a change in the screen resolution but after the initial screen showing "moving dots" it printed a few messages to the console with status [ok]. It stopped at the battery check. 
 
I believe I am on the right track. Pardon my non-technical explanation here.
 
Mohan

---

### Post by matt_symes on 2012-03-22
Hi

Maybe lightdm needs reconfiguring. From recovery console

```
sudo dpkg-reconfigure lightdm
```

What are the logs in /var/log saying ?

Kind regards

---

### Post by mohanradhakrishnan on 2012-03-22
saned disabled; edit /etc/default/saned
initctl: Event failed
 
Now even the recovery mode stops there. I can drop to root login though.
 
got into tty login. Maybe this([http://askubuntu.com/questions/59978/lightdm-is-running-but-does-not-display-on-login](http://askubuntu.com/questions/59978/lightdm-is-running-but-does-not-display-on-login)) might help.
 
Update : When I tried to run "sudo apt-get install lightdm" it showed many gtk packages and asked me to run "autoremove". After that I got to the stage described in [http://askubuntu.com/questions/67430/my-fresh-installation-doesnt-load-pulseaudio-problem](http://askubuntu.com/questions/67430/my-fresh-installation-doesnt-load-pulseaudio-problem).
 
Mohan

---

### Post by matt_symes on 2012-03-22
Hi

Nicely done ! Keep working through the problem.

Kind regards

---

### Post by mohanradhakrishnan on 2012-03-23
:-) The problem is solved.
 
So what started this problem is this. What is this advising ?
 
sudo apt-get install tsclient
Reading package lists... Done
Building dependency tree 
Reading state information... Done
tsclient is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
tsclient : Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
Depends: libbonoboui2-0 (>= 2.15.1) but it is not going to be installed
Depends: libgnomeui-0 (>= 2.22.0) but it is not going to be installed
Depends: libpanel-applet2-0 (>= 2.26.0) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
 
Thanks Matt.

---

### Post by matt_symes on 2012-03-23
Hi

> **mohanradhakrishnan said:**
> 
sudo apt-get install tsclient
Reading package lists... Done
Building dependency tree 
Reading state information... Done
tsclient is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
tsclient : Depends: libbonobo2-0 (>= 2.15.0) but it is not going to be installed
Depends: libbonoboui2-0 (>= 2.15.1) but it is not going to be installed
Depends: libgnomeui-0 (>= 2.22.0) but it is not going to be installed
Depends: libpanel-applet2-0 (>= 2.26.0) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
 
Thanks Matt.

This is telling you it will not install tsclient because it has depedencies on libraries that it cannot install.

Let's check your sources first.

Post back the results of this.

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Kind regards

---


---
title: "Authentication failure 10.04"
date: 2012-08-19
forum: General Help
---

### Post by foxy123 on 2012-08-19
I was upgrading software on my mother's laptop remotely (over ssh) and she misunderstood me and turned it off during the process. Now she cannot enter the system. After entering her password in the GDM login screen she's got something like 
```
Authentication failure
```

She was able to log in in the console and finished the upgrade but still cannot pass by the GDM login screen. 

I cannot connect to her laptop anymore as she needs to start VPN to enter the external network (it's is how her provider sets up external IPs). I was hoping to use nmcli to start VPN but is not present in 10.04. 

Anyway, does anyone know any solution or at least how to start VPN from the console in 10.04 so I can try things as now I have to dictate commands to my mother which is extremely tedious and time consuming.

---

### Post by foxy123 on 2012-08-21
Tried a few things yesterday with my mother over the phone driving her mad with all those silly commands :) but to no avail. 

Gnome greeter gives the following:

```
Install Problem The configuration defaults for GNOME Power Management have not been installed correctly Please contact your Computer Administrator
```

I tried to stop GDM and reinstall ubuntu-desktop. 
```
sudo apt-get --reinstall install ubuntu-desktop
```
We ran
```
sudo dpkg --configure -a
```
Also I tried to get a newer version of network-manager to be able to connect to the laptop and relieve my mother from typing things she's got no idea about. We managed to add PPA with a newer version and start the update but then ran into a problem of needing to answer some questions where I think we failed as I could not see what that was about (some was about EULA or something) and as a result the version of NM remained 0.80 without nmcli. After that we decided to call it a day. Or I have checked disk space it is looks (or actually sounds as I could not see it myself)there is no space shortage on the /.

Anyway, if anyone can suggest something it would be great as I really cannot think of anything else.

---

### Post by foxy123 on 2012-08-21
Managed to update NetworkManager but nmcli does not show the VPN connection :(

However, managed to get into the desktop with startx and got VPN up and ssh'ed into the laptop! Have no idea what to do though.

---

### Post by foxy123 on 2012-08-23
Well, after a many hours spent on the phone I have not managed to fix it. However, I have come up with a temporary solution (which is probably quite obvious):

1. go to console (Ctrl+Alt+F1) and log in
2. sudo service gdm stop
3. startx

A small problem (apart of a sheer annoyance) is that VPN connection asks for a key-ring password, which does not exist, so the only solution is to create a new VPN connection to get connected remotely.

---

### Post by foxy123 on 2012-09-05
The saga continues. I have tried to delete the existing keyring and create a new one. After that VPN did not ask for authentication. However, after reboot still cannot log in through GDM and VPN asks for a keyring password again (the new password does not work anymore). It looks like it resets itself after the reboot. 

My hypothesis is that something is wrong with PAM and the keyring is corrupted big time (probably permissions of one or several files are wrong). So when I try to log in on the GDM screen it cannot authenticate something and does not let me in. 

Again, any help will be really appreciated.

---


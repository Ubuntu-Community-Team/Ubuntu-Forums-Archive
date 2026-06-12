---
title: "apt-get upgrade problem - dovecot"
date: 2009-10-01
forum: General Help
---

### Post by Discus on 2009-10-01
I have a problem where sudo apt-get upgrade isn't upgrading my Dovecot package. 

Here is an example of the errors I get:  

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  dovecot-common dovecot-imapd dovecot-pop3d
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/3128kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 72213 files and directories currently installed.)
Preparing to replace dovecot-imapd 1:1.0.10-1ubuntu5.1 (using .../dovecot-imapd_1%3a1.0.10-1ubuntu5.2_amd64.deb) ...
invoke-rc.d: not a symlink: /etc/rc2.d/S99dovecot
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: not a symlink: /etc/rc2.d/S99dovecot
dpkg: error processing /var/cache/apt/archives/dovecot-imapd_1%3a1.0.10-1ubuntu5.2_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
invoke-rc.d: not a symlink: /etc/rc2.d/S99dovecot
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 102
Preparing to replace dovecot-pop3d 1:1.0.10-1ubuntu5.1 (using .../dovecot-pop3d_1%3a1.0.10-1ubuntu5.2_amd64.deb) ...
invoke-rc.d: not a symlink: /etc/rc2.d/S99dovecot
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: not a symlink: /etc/rc2.d/S99dovecot
dpkg: error processing /var/cache/apt/archives/dovecot-pop3d_1%3a1.0.10-1ubuntu5.2_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
invoke-rc.d: not a symlink: /etc/rc2.d/S99dovecot
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 102
Preparing to replace dovecot-common 1:1.0.10-1ubuntu5.1 (using .../dovecot-common_1%3a1.0.10-1ubuntu5.2_amd64.deb) ...
invoke-rc.d: not a symlink: /etc/rc2.d/S99dovecot
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: not a symlink: /etc/rc2.d/S99dovecot
dpkg: error processing /var/cache/apt/archives/dovecot-common_1%3a1.0.10-1ubuntu5.2_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/dovecot-imapd_1%3a1.0.10-1ubuntu5.2_amd64.deb
 /var/cache/apt/archives/dovecot-pop3d_1%3a1.0.10-1ubuntu5.2_amd64.deb
 /var/cache/apt/archives/dovecot-common_1%3a1.0.10-1ubuntu5.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Any ideas how I can fix this? 
I have tried apt-get update numerous times. 
Many thanks!

---

### Post by Discus on 2009-10-05
*bump*

---

### Post by Discus on 2009-10-12
Still no joy here - am worried about this problem! Anyone have any suggestions? Many thanks!

---

### Post by Discus on 2009-10-12
I finally decided to get drastic and I think I've "fixed" part of the problem, but still don't get upgrade joy. 

So far: 

The key problem was the line about symlinks:
```
invoke-rc.d: not a symlink: /etc/rc2.d/S99dovecot

```

Some googling got me the following page: [http://talk.maemo.org/showthread.php?t=21613](http://talk.maemo.org/showthread.php?t=21613) which seemed rather drastic, so instead: 

At a command line, I used the following:
```
cd /etc/rc2.d/
sudo rm /etc/rc2.d/S99dovecot
```
which removed the file in rc2.d which was causing issues.

I then created a symlink to the dovecot startup script (/etc/init.d/dovecot): 
```
sudo ln -s /etc/init.d/dovecot /etc/rc2.d/S99dovecot

```

Then I did an apt-get update and apt-get upgrade, but ran into more problems...!

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up dovecot-common (1:1.0.10-1ubuntu5.2) ...
You already have ssl certs for dovecot.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing dovecot-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dovecot-imapd:
 dovecot-imapd depends on dovecot-common (= 1:1.0.10-1ubuntu5.2); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-imapd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dovecot-pop3d:
 dovecot-pop3d depends on dovecot-common (= 1:1.0.10-1ubuntu5.2); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-pop3d (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dovecot-common
 dovecot-imapd
 dovecot-pop3d
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

apt-get install -f does not work as advertised :/

---

### Post by Discus on 2009-10-15
Any ideas? 

Still have this issue: 

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up dovecot-common (1:1.0.10-1ubuntu5.2) ...
You already have ssl certs for dovecot.
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error processing dovecot-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dovecot-imapd:
 dovecot-imapd depends on dovecot-common (= 1:1.0.10-1ubuntu5.2); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-imapd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dovecot-pop3d:
 dovecot-pop3d depends on dovecot-common (= 1:1.0.10-1ubuntu5.2); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-pop3d (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dovecot-common
 dovecot-imapd
 dovecot-pop3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Discus on 2009-10-20
Eventually, I ended up 
1) uninstalling all of dovecot
2) removing all the dovecot-related files in the caches
3) reinstalling

This fixed it, but was rather traumatic, as email went down whilst I did this. 

Make sure you backup your dovecot configuration file, as the default one (obviously!) won't have your changes (including changes you probably don't remember making in the ages since you set up your machine!). I went through the new one line-by-line changing things back as I wasn't certain the two would be compatible with their options (i.e. simply over-writing with the old one). 

Several things broke until I got all the settings back to the way they were - most notably authentication by postfix, which came back after I got the config right at rebooted.

---

### Post by kpholmes on 2009-10-20
ya that looks weird, if you have x installed try using synaptic and make sure you have all the dependencies, and check out the package on launchpad

---

### Post by Discus on 2009-10-20
Hi kpholmes, 

Yes, you'll see in my original post (after the error output) I did say I tried apt-get update (numerous times) too :) 

Perhaps there was a problem with the automatic update package (unattended-upgrades) I installed a few weeks back corrupting things...

This is a Server version with no X installed (it's a virtual machine running inside VMWare server v1.x on a Server 2003 SBE box).

---

### Post by Discus on 2010-03-12
Of course, now my system thinks dovecot-common is not installed :/

---


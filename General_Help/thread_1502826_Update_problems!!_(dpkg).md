---
title: "Update problems!! (dpkg)"
date: 2010-06-06
forum: General Help
---

### Post by bluTaz on 2010-06-06
Having some problems with updating my system. I believe it was caused when I accidentally powered off the machine while it was updating. Any suggestions will be greatly appreciated. Thanks in advance.

OUTPUT:
```

Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'cdemu' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Setting up transmission-daemon (1.93-0ubuntu0~ppa1) ...
dpkg-statoverrides: unrecoverable fatal error, aborting:
 syntax error: unknown group 'cdemu' in statoverride file
dpkg-statoverrides: unrecoverable fatal error, aborting:
 syntax error: unknown group 'cdemu' in statoverride file
dpkg: error processing transmission-daemon (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up vhba-dkms (1.2.1-0ubuntu7) ...

Error! DKMS tree already contains: vhba-1.2.1
You cannot add the same module/version combo more than once.
ERROR: Failed to add dkms add module
dpkg: error processing vhba-dkms (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cdemu-daemon:
 cdemu-daemon depends on vhba-dkms (>= 1.1.0); however:
  Package vhba-dkms is not configured yet.
dpkg: error processing cdemu-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cdemu-client:
 cdemu-client depends on cdemu-daemon (>= 1.1.0); however:
  Package cdemu-daemon is not configured yet.
dpkg: error processing cdemu-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcdemu:
 gcdemu depends on cdemu-daemon (>= 1.1.0); however:
  Package cdemu-daemon is not configured yet.
dpkg: error processing gcdemu (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 transmission-daemon
 vhba-dkms
 cdemu-daemon
 cdemu-client
 gcdemu

```

---

### Post by bluTaz on 2010-06-06
anyone? any suggestions are welcome... I would really like to get my Ubuntu updated. Cheers.

---

### Post by stderr on 2010-06-06
Try

```
sudo dpkg --configure --pending
sudo apt-get -f install
```

If you're still having trouble, see if the output from this helps at all:

```
sudo dpkg --audit
```

---

### Post by bluTaz on 2010-06-06
Thanks for the suggestions.

first two commands did not solve it.

The output of the second suggestion is:

```
david@ubuntu-laptop:(~)$ sudo dpkg --audit
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 gcdemu               A GNOME panel applet to control CDEmu daemon

The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 cdemu-daemon         CDEmu daemon
 cdemu-client         A simple command-line client to control CDEmu daemon

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 transmission-daemon  lightweight BitTorrent client (daemon)
 vhba-dkms            VHBA virtual host bus adapter module

```

It seems gcdemu is my biggest problem. I tried to purge it through synaptic... but it wouldn't allow me to do so. It also wouldn't allow me to reinstall it, so.... ??? any other tips? Thanks a ton.

---

### Post by bluTaz on 2010-06-06
anyone have some suggestions?... I'd really like to avoid a fresh install.

---

### Post by stderr on 2010-06-06
You shouldn't have to reinstall due to this :)

I'd try doing what audit suggests. Re-audit after each attempt to see if anything helped:

```
sudo dpkg --configure transmission-daemon vhba-dkms
sudo dpkg --audit
```


```
sudo dpkg --configure cdemu-daemon cdemu-client
sudo dpkg --audit
```

```
sudo apt-get -f install
sudo apt-get --reinstall install gcdemu
```

Failing that, have you got the original .deb you used to install gcdemu? Try:

```
sudo dpkg -i path/to/the_gcdemu_installer.deb
```

---

### Post by msambenny on 2010-06-15
Can someone tell me how to upgrade my ubuntu system??

---

### Post by mattcaron on 2010-06-19
Try this:
```

sudo dkms remove -m vhba -v 1.2.1 --all
sudo dpkg --configure vhba-dkms

```

---

### Post by mattcaron on 2010-06-19
Another thing to note - it might be worth removing vhba-dkms first, then upgrading, then reinstalling it

---

### Post by aguai on 2010-08-23
> **bluTaz said:**
> Having some problems with updating my system. I believe it was caused when I accidentally powered off the machine while it was updating. Any suggestions will be greatly appreciated. Thanks in advance.

OUTPUT:
```

Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'cdemu' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
Setting up transmission-daemon (1.93-0ubuntu0~ppa1) ...
dpkg-statoverrides: unrecoverable fatal error, aborting:
 syntax error: unknown group 'cdemu' in statoverride file
dpkg-statoverrides: unrecoverable fatal error, aborting:
 syntax error: unknown group 'cdemu' in statoverride file
dpkg: error processing transmission-daemon (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up vhba-dkms (1.2.1-0ubuntu7) ...

Error! DKMS tree already contains: vhba-1.2.1
You cannot add the same module/version combo more than once.
ERROR: Failed to add dkms add module
dpkg: error processing vhba-dkms (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cdemu-daemon:
 cdemu-daemon depends on vhba-dkms (>= 1.1.0); however:
  Package vhba-dkms is not configured yet.
dpkg: error processing cdemu-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cdemu-client:
 cdemu-client depends on cdemu-daemon (>= 1.1.0); however:
  Package cdemu-daemon is not configured yet.
dpkg: error processing cdemu-client (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcdemu:
 gcdemu depends on cdemu-daemon (>= 1.1.0); however:
  Package cdemu-daemon is not configured yet.
dpkg: error processing gcdemu (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 transmission-daemon
 vhba-dkms
 cdemu-daemon
 cdemu-client
 gcdemu

```

try 
sudo vim /var/lib/dpkg/statoverride
remove the line with cdemu
this might not be a proper solution 
but somehow it works

---

### Post by bluTaz on 2010-10-17
hmm... I'm way late, but thanks all who gave suggestions to solving this issue. I did end up doing a fresh install, I got very frustrated on this issue here and there were other little reasons that made me decide to go ahead and do a fresh install, although I'm sure I could have avoided them all. Anyhow, thanks everyone for the suggestions.

---

### Post by kindergartencop on 2011-09-20
There seems to be a bug in the cdemu postinst scripts that somehow causes the cdemu group to be removed. Just use groupadd or vi /etc/group or use the gnome "users and groups" tool to add the "cdemu" group to the system and - viola - everything will work again.
Alternatively you may also uninstall the cdemu packages as a solution.

---

### Post by Elfy on 2011-09-20
Old thread closed.

---


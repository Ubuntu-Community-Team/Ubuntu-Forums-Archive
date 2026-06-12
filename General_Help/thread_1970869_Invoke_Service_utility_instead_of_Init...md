---
title: "Invoke Service utility instead of Init.."
date: 2012-05-01
forum: General Help
---

### Post by memristor on 2012-05-01
How do i switch a start up script to start utility instead of using init? I came across the following message in my log.

```
fsck from util-linux 2.20.1
/: clean, 306290/12664832 files, 6414265/50653952 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [170G 
[164G[ OK ]
 * Starting bluetooth daemon[164G[ OK ]
 * Starting mDNS/DNS-SD daemon[164G[ OK ]
 * Setting sensors limits        * Stopping restore software rfkill state[164G[ OK ]
[170G 
[164G[ OK ]
[COLOR="Red"][B]
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service S20network-manager start
 * Stopping System V initialisation compatibility[164G[ OK ]
initctl: Unknown job: S20network-manager
 * Starting System V runlevel compatibility[164G[ OK ]

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start S20network-manager[/B][/COLOR]
 * Starting eCryptfs[164G[ OK ]
 * Starting LightDM Display Manager[164G[ OK ]
 * Starting anac(h)ronistic cron[164G[ OK ]
 * Starting save kernel messages[164G[ OK ]
 * Starting ACPI daemon[164G[ OK ]
 * Stopping eCryptfs[164G[ OK ]
 * Starting CPU interrupts balancing daemon[164G[ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
 * Starting automatic crash report generation[164G[ OK ]
Setting up X font server socket directory /tmp/.font-unix...done.
Starting X font server: xfs.
 * Starting regular background program processing daemon[164G[ OK ]
 * Starting deferred execution scheduler[164G[ OK ]


```

---

### Post by matt_symes on 2012-05-02
Hi

What version of *buntu are you using ? (Ubutnu, Kubuntu, l(x)ubuntu ?). What release of *buntu are you using ? 

```
cat /etc/lsb-release
```

Certainly on Ubuntu precise, network manager has already been converted to an upstart job.

```
matthew@matthew-Aspire-7540 ~ % ls /etc/init/*network-manager*
/etc/init/network-manager.conf
matthew@matthew-Aspire-7540 ~ % 
```

and is no longer a system V job

```

matthew@matthew-Aspire-7540 ~ % ls /etc/rc?.d/*network-manager*
zsh: no matches found: /etc/rc?.d/*network-manager*
matthew@matthew-Aspire-7540 ~ %
```

Can you post the output of these two commands back here

```
ls /etc/init/*network-manager*
```

 ```
ls /etc/rc?.d/*network-manager*
```

between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

Kind regards

---

### Post by memristor on 2012-05-02
Hello matt_symes,

Thanks for your interest! Sorry i should have included information about my distribution with original post. I have recently upgraded to Precise Pangolin from previous version.  

Here is the output of the command:
[COLOR="blue"]cat /etc/lsb-release[/COLOR]
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

```

Here is the output from:
[COLOR="blue"]ls /etc/init/*network-manager*[/COLOR]
```
/etc/init/network-manager.conf   /etc/init/network-manager.conf.dpkg-dist
/etc/init/network-manager.conf~

```

And the last command:
[COLOR="Blue"]ls /etc/rc?.d/*network-manager*[/COLOR]
```
/etc/rc0.d/K20network-manager  /etc/rc4.d/S20network-manager
/etc/rc1.d/K20network-manager  /etc/rc5.d/S20network-manager
/etc/rc2.d/S20network-manager  /etc/rc6.d/K20network-manager
/etc/rc3.d/S20network-manager

```

---

### Post by memristor on 2012-05-02
Also i here is some more information if it helps. On 11.10 i was having long shutdown times due to network manager. I had followed the instructions here

[http://askubuntu.com/questions/87576/slow-shutdown-due-to-modemmanager-and-nm-dispatcher-action](http://askubuntu.com/questions/87576/slow-shutdown-due-to-modemmanager-and-nm-dispatcher-action)

```
The report does mention an edit one can make to /etc/init/network-manager.conf, ie. add as shown

stop on runlevel [06]  
I believe adding the line was effective
```

---

### Post by memristor on 2012-05-04
Anyone?

---

### Post by hawkmage on 2012-05-04
Sinnce Ubuntu 6.10 the init process has been using Upstart instead of SysV.  The /etc/rc#.d/ with the K and S links to the /etc/init.d/ scripts is the Sys V init system.

Did you link the /etc/rc#.d/?##network-manager to the network manager script in /etc/init/?

WHat do you get if you run:
```
ls -l /etc/rc?.d/*network-manager*
```I am not sure how you would fix this, my first through would be to delete the links in /etc/rc#.d for network-manager and then remove and reinstall network-manager but I have not tested this.

---

### Post by memristor on 2012-05-05
Thanks for your reply hawkmage.
Here is what i got from your command

```
lrwxrwxrwx 1 root root 25 Nov 18 01:21 /etc/rc0.d/K20network-manager -> ../init.d/network-manager
lrwxrwxrwx 1 root root 25 Nov 18 01:21 /etc/rc1.d/K20network-manager -> ../init.d/network-manager
lrwxrwxrwx 1 root root 25 Nov 18 01:21 /etc/rc2.d/S20network-manager -> ../init.d/network-manager
lrwxrwxrwx 1 root root 25 Nov 18 01:21 /etc/rc3.d/S20network-manager -> ../init.d/network-manager
lrwxrwxrwx 1 root root 25 Nov 18 01:21 /etc/rc4.d/S20network-manager -> ../init.d/network-manager
lrwxrwxrwx 1 root root 25 Nov 18 01:21 /etc/rc5.d/S20network-manager -> ../init.d/network-manager
lrwxrwxrwx 1 root root 25 Nov 18 01:21 /etc/rc6.d/K20network-manager -> ../init.d/network-manager

```

---

### Post by memristor on 2012-05-08
Any suggestions?

---


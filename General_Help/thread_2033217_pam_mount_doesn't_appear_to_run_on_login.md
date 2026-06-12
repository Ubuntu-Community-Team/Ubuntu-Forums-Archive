---
title: "pam_mount doesn't appear to run on login"
date: 2012-07-25
forum: General Help
---

### Post by TheAbyssDragon on 2012-07-25
I'm trying to get pam_mount to mount 3 cifs shares when a user logs in to a Xubuntu 12.04 install. Unfortunately I've been unable to resolve the problem on my own, so I'm looking for some help.

First off, I have the following pam_mount.conf.xml:
```

<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<!--
	See pam_mount.conf(5) for a description.
-->

<pam_mount>

		<!-- debug should come before everything else,
		since this file is still processed in a single pass
		from top-to-bottom -->

<debug enable="0" />

		<!-- Volume definitions -->

<volume user="*" fstype="cifs" server="10.0.0.10" path="%(USER)" mountpoint="~/Personal" />
<volume user="*" fstype="cifs" server="10.0.0.10" path="media" mountpoint="~/Media" />
<volume user="*" fstype="cifs" server="10.0.0.10" path="software" mountpoint="~/Software" />


		<!-- pam_mount parameters: General tunables -->

<!--
<luserconf name=".pam_mount.conf.xml" />
-->

<!-- Note that commenting out mntoptions will give you the defaults.
     You will need to explicitly initialize it with the empty string
     to reset the defaults to nothing. -->

<mntoptions allow="*" />
<mntoptions require="" />

<logout wait="0" hup="0" term="0" kill="0" />


		<!-- pam_mount parameters: Volume-related -->

<mkmountpoint enable="1" remove="true" />


</pam_mount>

```

I've been distro hopping recently, but I know that this exact file used to work on Ubuntu (11.04 I think) and more recently on LMDE.

My auth.log file looks like this:
```

Jul 25 18:01:56 vali lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jul 25 18:01:56 vali lightdm: pam_mount(pam_mount.c:476): warning: could not obtain password interactively either
Jul 25 18:01:56 vali lightdm: pam_mount(mount.c:69): Messages from underlying mount program:
Jul 25 18:01:56 vali lightdm: pam_mount(mount.c:73): mount error(101): Network is unreachable
Jul 25 18:01:56 vali lightdm: pam_mount(mount.c:73): Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
Jul 25 18:01:56 vali lightdm: pam_mount(pam_mount.c:521): mount of lightdm failed
Jul 25 18:01:56 vali lightdm: pam_mount(mount.c:69): Messages from underlying mount program:
Jul 25 18:01:56 vali lightdm: pam_mount(mount.c:73): mount error(101): Network is unreachable
Jul 25 18:01:56 vali lightdm: pam_mount(mount.c:73): Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
Jul 25 18:01:56 vali lightdm: pam_mount(pam_mount.c:521): mount of media failed
Jul 25 18:01:56 vali lightdm: pam_mount(mount.c:69): Messages from underlying mount program:
Jul 25 18:01:56 vali lightdm: pam_mount(mount.c:73): mount error(101): Network is unreachable
Jul 25 18:01:56 vali lightdm: pam_mount(mount.c:73): Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
Jul 25 18:01:56 vali lightdm: pam_mount(pam_mount.c:521): mount of software failed
Jul 25 18:01:56 vali lightdm: pam_mount(pam_mount.c:476): warning: could not obtain password interactively either
Jul 25 18:01:56 vali lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jul 25 18:01:56 vali dbus[984]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.16" (uid=104 pid=1411 comm="/usr/sbin/lightdm-gtk-greeter ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1332 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jul 25 18:01:57 vali lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "chris"
Jul 25 18:02:05 vali lightdm: pam_unix(lightdm:session): session closed for user lightdm
Jul 25 18:02:05 vali lightdm: pam_mount(mount.c:69): umount messages:
Jul 25 18:02:05 vali lightdm: pam_mount(mount.c:73): umount: /var/lib/lightdm/Software: not found
Jul 25 18:02:05 vali lightdm: pam_mount(mount.c:752): unmount of software failed
Jul 25 18:02:05 vali lightdm: pam_mount(mount.c:69): umount messages:
Jul 25 18:02:05 vali lightdm: pam_mount(mount.c:73): umount: /var/lib/lightdm/Media: not found
Jul 25 18:02:05 vali lightdm: pam_mount(mount.c:752): unmount of media failed
Jul 25 18:02:05 vali lightdm: pam_mount(mount.c:69): umount messages:
Jul 25 18:02:05 vali lightdm: pam_mount(mount.c:73): umount: /var/lib/lightdm/Personal: not found
Jul 25 18:02:05 vali lightdm: pam_mount(mount.c:752): unmount of lightdm failed
Jul 25 18:02:05 vali lightdm: pam_unix(lightdm:session): session opened for user chris by (uid=0)

```

From that point forward, there are no mentions of pam_mount. So it appears that the module is running for the user lightdm (and failing) but not running for a user that logs in.

After doing some googling, I took a look at a few files in /etc/pam.d/ but pam_mount.so seems to be present where needed.

So at this point I'm at a loss. Does anyone know why pam_mount would run for 'lightdm' but not for 'chris'? Have I misdiagnosed the problem and should look somewhere else?

Thanks in advance.

---

### Post by hintze on 2012-07-31
thats strange. libpam_mount doesnt work for me neither. I am using 12.04 with unity.. on another machine, the same setup just works fine with several users.. 

the only thing i get with ```
cat /var/log/auth.log | grep pam_mount
``` is the following:

```
Jul 31 12:54:52 DeepThought lightdm: pam_mount(mount.c:69): umount messages:
Jul 31 12:54:52 DeepThought lightdm: pam_mount(mount.c:73): umount: /home/user/folder1: not found
Jul 31 12:54:52 DeepThought lightdm: pam_mount(mount.c:752): unmount of folder1 failed
Jul 31 12:54:52 DeepThought lightdm: pam_mount(mount.c:69): umount messages:
Jul 31 12:54:52 DeepThought lightdm: pam_mount(mount.c:73): umount: /home/user/folder2: not found
Jul 31 12:54:52 DeepThought lightdm: pam_mount(mount.c:752): unmount of folder2 failed
```

thats all for one logout/login again. network is reachable and i can manually access the folder via fuse (smb) and gvfs. i dont get it. as i said, the exact same setup works on another machine.

but concerning your log, i only see entrys for user "lightdm", which is why you specified in the pam_mount.conf.xml for user to be *, so everyone. try changing this to your username solely. furthermore your log states that the network is not reachable? 

another question: do you have some cifs-related packages installed? im not sure which one youll need, but sth. like smbclient or cifsutils should be installed..

---

### Post by chrisdee on 2012-08-16
Any news on this ??

my pam_mount_conf.xml file worked fine on 10.04, but now with 12.04 the exact same file doesnt work.

---

### Post by albandy on 2012-08-16
I moved to gvfs-mount, and if you are using likewise it pass automatically your credential to shares.

I'm connected to an active directory ldap using likewise. Then I mount the network shares using a script with gvfs-mount:

gvfs-mount smb://fileserver.mydomain/$USER

---

### Post by chrisdee on 2012-09-14
> **albandy said:**
> I moved to gvfs-mount, and if you are using likewise it pass automatically your credential to shares.

I'm connected to an active directory ldap using likewise. Then I mount the network shares using a script with gvfs-mount:

gvfs-mount smb://fileserver.mydomain/$USER

Thanks. I will try that.

---

### Post by TheAbyssDragon on 2012-10-18
Sorry, I stopped following this after several days of no response.

I think it's failing to reach the network, because there is no network when lightdm authenticates. The problem is that it does appear to be running at all for my actual user account, at least as far as the logfile is concerned.

This pam_mount.conf.xml works flawlessly under other distros.

UPDATE: If I run 'mount', I get the following output:

//10.0.0.10/chris on /home/chris/Personal type cifs (rw)
//10.0.0.10/media on /home/chris/Media type cifs (rw)
//10.0.0.10/software on /home/chris/Software type cifs (rw)
/home/chris/.Private on /home/chris type ecryptfs

So is my encrypted container overwriting the folder that the network mounts are in?

---

### Post by OO-Dragon on 2013-01-20
> **albandy said:**
> I moved to gvfs-mount, and if you are using likewise it pass automatically your credential to shares.

I'm connected to an active directory ldap using likewise. Then I mount the network shares using a script with gvfs-mount:

gvfs-mount smb://fileserver.mydomain/$USER

Where did you run put the script to run for all users?

---


---
title: "Server issues"
date: 2012-05-04
forum: General Help
---

### Post by sgrabowski on 2012-05-04
Hi all. I'm at my limit for my linux capabilities and need some pointers as how to fix these problems with my 12.04 Server:

1. I have set up unattended updates and now they are failing because there's a problem with unmet dependencies:

```

stefan@orieta:~$ sudo apt-get upgrade
Reading package lists...
Building dependency tree...
Reading state information...
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 samba : Depends: samba-common (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.1 is installed
         Depends: libwbclient0 (= 2:3.6.3-2ubuntu2) but 2:3.6.3-2ubuntu2.1 is installed
E: Unmet dependencies. Try using -f.

```

So I tried that, but it seems to be having issues with Twonky Server. I have completely removed the twonky install, so I don't understand why I am getting this issue:

```

stefan@orieta:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  fakeroot libc6-i386 lib32gcc1 dkms
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  samba
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools ldb-tools ctdb
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
27 not fully installed or removed.
Need to get 0 B/8,041 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 164188 files and directories currently installed.)
Preparing to replace samba 2:3.6.3-2ubuntu2 (using .../samba_2%3a3.6.3-2ubuntu2.1_amd64.deb) ...
PID file /var/run/mediaserver.pid not found, stopping server anyway...
twonkystarter: no process found

Stopping twonkywebdav
twonkywebdav: no process found
Stopping twonkyproxy
twonkyproxy: no process found
invoke-rc.d: initscript nmbd, action "stop" failed.
dpkg: warning: subprocess old pre-removal script returned error exit status 3
dpkg - trying script from the new package instead ...
PID file /var/run/mediaserver.pid not found, stopping server anyway...
twonkystarter: no process found

Stopping twonkywebdav
twonkywebdav: no process found
Stopping twonkyproxy
twonkyproxy: no process found
invoke-rc.d: initscript nmbd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/samba_2%3a3.6.3-2ubuntu2.1_amd64.deb (--unpack):
 subprocess new pre-removal script returned error exit status 3
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
Twonky server not found.

Twonky server not found.

Errors were encountered while processing:
 /var/cache/apt/archives/samba_2%3a3.6.3-2ubuntu2.1_amd64.deb
stefan@orieta:~$ 

```

2. I have a drive in the server what will not go into standby. I have set up HDPARM to send the three data drives to standby after 10 minutes of inactivity, but /dev/sdb1 refuses to go into standby, even after using the '-y' flag.

Any advice or pointers on these two issues would stop me pulling my hair out, and end up with the server I've always wanted!!

---

### Post by CharlesA on 2012-05-04
Have did you install and remove twonky? it looks like apt still thinks it is installed.

Try this:

```
sudo apt-get purge samba && sudo apt-get install samba
```

---

### Post by sgrabowski on 2012-05-05
Thanks for the pointer, but I'm still getting errors:

```

stefan@orieta:~$ sudo apt-get purge samba && sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot libc6-i386 lib32gcc1 dkms
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  samba*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
27 not fully installed or removed.
After this operation, 23.4 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 164187 files and directories currently installed.)
Removing samba ...
PID file /var/run/mediaserver.pid not found, stopping server anyway...
twonkystarter: no process found

Stopping twonkywebdav
twonkywebdav: no process found
Stopping twonkyproxy
twonkyproxy: no process found
invoke-rc.d: initscript nmbd, action "stop" failed.
dpkg: error processing samba (--purge):
 subprocess installed pre-removal script returned error exit status 3
update-alternatives: using /usr/bin/smbstatus.samba3 to provide /usr/bin/smbstatus (smbstatus) in auto mode.
Twonky server not found.

Twonky server not found.

Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by CharlesA on 2012-05-05
What happens when you try to purge twonky?

The system still thinks it is installed and that is probably why it is failing.

---

### Post by HermanAB on 2012-05-05
Hmm, the first thing to do when you installed a server, is to turn auto-screwups/updates off.

You have to evaluate each update on another machine (physical or virtual) first, before you apply it to a critical machine.

---

### Post by sgrabowski on 2012-05-05
CharlesA: Twonky was installed via a shell script so purging twonky bring up unable to locate package error. I have removed all the files referenced in it's install log, including the init.d reference.

HermanAB: This is my only ubuntu machine, and its only a home media server, so cannot not really be classed as critical. I just want to get it working properly.

---

### Post by CentrumSilver on 2012-07-11
Hi!
  I had this issue as well and came to this thread.  I fixed my issue by simply doing
sudo apt-get autoremove libwbclient0

I could install the stuff I needed after this.. but I didn't have the other dependency.. just wanted to pass this along for reference is all...

---

### Post by aknock on 2013-01-05
I had the same problem (preceded by 12.04 MySQL dependency woes).  I had removed all Twonky files referenced in the twonky.sh installer, and having resolved the dependency issues still found that the Twonky messages referenced above were being shown when doing an unrelated update (in this case updating Cups).

By grepping 

```
grep -R 'Twonky' /etc/init.d/* 
```

I found loads of references to Twonky, all symlinks through to /lib/init/upstart-job which had been entirely replaced with the twonky.sh installer. :o

I then move upstart-job out of the folder and ran

```
apt-get install upstart --reinstall
```

which reinstates /lib/init/upstart-job and allowed me to upgrade using apt-get without any errors.  

Be warned that you must verify that upstart-job is indeed 'corrupt' before doing this - as I understand it upstart is a pretty critical process and not to be messed with unless you are sure that it has definitely broken.  At this point I haven't verified that there are no ongoing issues, though getting apt-get back in operation at a minimum is somewhat helpful and I have been available to reboot without major issues.

---


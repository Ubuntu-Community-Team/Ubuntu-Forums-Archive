---
title: "Automount sshfs"
date: 2012-08-24
forum: General Help
---

### Post by hgaronfolo on 2012-08-24
Hi,

I've been trying to automount my ssh server at startup, but I can't get it working.

I use the following script to mount the ssh:
#!/bin/bash 
if sshfs -o idmap=user server@server: /home/herbert/Server
then
zenity --info --timeout 1 --text "Server mounted."
fi

I've tried inserting the script into rc.local. I have tried to execute it through .config/autostart and I have also tried mounting it through fstab.. None of it worked :(

If I run the following: sudo /etc/init.d/rc.local start
The server mounts fine, but it just wont mount on bootup.

Can someone please walk me through the best way to automount with sshfs on Lubuntu?

Thank you so much.

---

### Post by dozdozez on 2012-08-24
I would write the script in a separate file in /etc/init.d/
This script should have a start option to mount and a stop option to umount and a text interface.
Then execute:
```
update-rc.d <script> enable
```
this command should create links in /etc/rc?.d/ so i would test that
```
ll -rt rc2.d
```
you shold find there a link to your script whose name begins by S and a number. This means that when system enters in runlevel 2 this service will start.

But you may prefer to put your script to run when XFCE starts: 
Menu > Settings > Settings Manager > Session and Startup > Application Autostart >Add...

good luck!

---

### Post by Morbius1 on 2012-08-24
>  Can someone please walk me through the best way to automount with sshfs on Lubuntu?I don't know if there is a "best" way but there is "another" way - Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

It talks specifically about Samba share mounting but Gigolo can automount using several protocols.

---

### Post by dozdozez on 2012-08-24
Or maybe using fstab. Here explains how to do it:

[http://ubuntuforums.org/showthread.php?t=430312](http://ubuntuforums.org/showthread.php?t=430312)

/etc/fstab is the file where you say to the computer whre to mount things, so I think that this may be a good way.

---

### Post by nerdux on 2012-08-24
Assuming you're using certificates to ssh into your server, I'd bet your problem is related to the fact that /etc/rc.local is sourced as root when launched from the init sequence.

If this is it you have two alternatives to work it out:
1) Generate a certificate for the user root on your local computer and ssh-copy-id it to the authorized keys on server@server. This way your remote directory will be mounted locally as root.
2) Modify your rc.local script to run the sshfs command as your herbert user, that is:
```
sudo herbert -c "sshfs -o idmap=user server@server: /home/herbert/Server"
```Doing it this way, your remote directory will be mounted as herbert locally.

Good luck!

---


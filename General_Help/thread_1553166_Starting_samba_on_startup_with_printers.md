---
title: "Starting samba on startup with printers"
date: 2010-08-14
forum: General Help
---

### Post by dnpate on 2010-08-14
Using 10.04.  I use one machine mostly as a printer server:  If it goes down for whatever reason I want to restart without having to enter any password.  Samba seems to start and allow file shares, but does not start the printer sharing so I must manually enter "sudo restart smbd" to allow the printer sharing.  From reading the various threads I guess that the samba "start command" is before the printers are "initialized" and thus are not "setup".  So how can I make the samba "startup" last after everything else?  I am not enough familiar with all of the commands to understand the thread posting to make it work.  Thanks for any help.
David

---

### Post by Morbius1 on 2010-08-14
You are correct. CUPS is starting after smbd. 

Here's the fix from the bug report ( look for the "patch" icon ): [https://bugs.launchpad.net/ubuntu/lucid/+source/upstart/+bug/494141](https://bugs.launchpad.net/ubuntu/lucid/+source/upstart/+bug/494141)

Edit **/etc/init/smbd.conf** and change this:
> description "SMB/CIFS File Server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

[COLOR=Blue]start on local-filesystems
[/COLOR]stop on runlevel [!2345]

respawn

pre-start script
    RUN_MODE="daemons"

    [ -r /etc/default/samba ] && . /etc/default/samba

    [ "$RUN_MODE" = inetd ] && { stop; exit 0; }

    install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -Fto this:
> description "SMB/CIFS File Server"
author      "Steve Langasek <steve.langasek@ubuntu.com>"

[COLOR=Blue]start on (local-filesystems and stopped rc)[/COLOR]
stop on runlevel [!2345]

respawn

pre-start script
    RUN_MODE="daemons"

    [ -r /etc/default/samba ] && . /etc/default/samba

    [ "$RUN_MODE" = inetd ] && { stop; exit 0; }

    install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -F

---

### Post by dnpate on 2010-08-14
thanks for the fix, but I kept looking and this worked also.

"I have the same problem too. I solved it by adding

sleep 60
restart smbd

to /etc/rc.local.
[https://bugs.launchpad.net/ubuntu/lucid/](https://bugs.launchpad.net/ubuntu/lucid/) source/upstart/ bug/494141"

---


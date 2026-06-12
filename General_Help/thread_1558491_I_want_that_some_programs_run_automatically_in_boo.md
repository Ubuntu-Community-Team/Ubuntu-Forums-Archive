---
title: "I want that some programs run automatically in boot"
date: 2010-08-22
forum: General Help
---

### Post by payaa on 2010-08-22
I hire a VPS what comes with Ubuntu 10.04 (minimal).

So if I reboot the VPS the mysql and ventrilo server dont start automatically.

How can I make it to start automatically these programs? Please? I have only command line (PuTTY).

Thx!

---

### Post by d3v1150m471c on 2010-08-22
use your start up programs gui and add them that way or add the commands to ~/.bashrc.

Note: You may want to append an ampersand to the bashrc commands.

---

### Post by payaa on 2010-08-22
Hi! Thx for reply!

I must tell U I'm a very-very noob in Ubuntu and linux systems.

Where is my startup programs gui???

I'm only have commandline but not desktop.

---

### Post by richs-lxh on 2010-08-22
If you only have the terminal and no desktop, you can add programs in the /etc/rc.local file.

> sudo nano /etc/rc.local

Then just add the ones you want, and reboot.

It looks like this:

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


Add your applications before "exit 0".

---

### Post by payaa on 2010-08-22
Thx!

I found it. Here is my rc.local:
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


So, how can I add coz the ventrilo in root/ventri/ventrilo_srv. And mysql?

---

### Post by richs-lxh on 2010-08-25
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/etc/init.d/mysql start
/where/you/installed/ventrilo_srv
exit 0

The ventrilo_srv command depends on where you installed it. For example:
> /home/ventrilo/ventrilo_srv

Somebody on Linux Forums created a script you can run from init.d
> /etc/initd.d/ventrilo start
[http://www.linuxforums.org/forum/debian-linux-help/79952-ventrilo-start-up-script.html#post416352](http://www.linuxforums.org/forum/debian-linux-help/79952-ventrilo-start-up-script.html#post416352)

Sorry i've never used Ventrilo and got the info via Google.
[http://www.ventrilo.com/setup.php](http://www.ventrilo.com/setup.php)

---


---
title: "How to Do a Remote Shutdown for a PC on a LAN"
date: 2011-08-06
forum: General Help
---

### Post by Karlas on 2011-08-06
So yeah,the title says it all,is there anyway to do it?
Thanks

---

### Post by ratcheer on 2011-08-06
If it is a Linux (or other UNIX-like) OS and you have ssh access and root access, you can give the remote PC the command "init 0". That is a zero.

Tim

---

### Post by Karlas on 2011-08-06
Yes the other computer has Ubuntu too,can you explain a bit more?
Thanks.

---

### Post by juhaszjozsef on 2011-08-06
On the remote machine (which you want to power off) install openssh-server:

```
apt-get install openssh-server

```
On your computer open up a terminal and:

```
ssh -l yourusername_on_the_remote_computer IP_OF_REMOTE_COMPUTER

```
eg:
```
ssh -l john 192.168.1.100
```
There will be a warning about adding the computer to the trusted ones.
Enter: yes

Then:
```
sudo halt
```

You can execute any command just like you sit in front of the remote computer...

Good luck!

---

### Post by MDguy on 2011-08-06
On the computer you want to shut down, install openssh-server.
```
sudo apt-get install openssh-server
```

To shut down the computer remotely:

Open a terminal (ctrl+alt+t) and type:
```
ssh <username>@<machine ip address>
```

Replace <username> and <machine ip address> with the username and ip address of the machine you want to shut down.  If you don't know the ip address, type "ifconfig" into the terminal (on the machine you want to turn off remotely)

Once your have logged in successfully with ssh, run:
```
init 0
```
Alternatively, you can run "sudo shutdown -h now" or "sudo halt".

---

### Post by Karlas on 2011-08-06
Ok I got the idea,1 more question,I could just run downstairs and check my other computers IP,but is there anyway to see it without doing that?Im using wlan.

---

### Post by juhaszjozsef on 2011-08-06
You can check it via your router's web interface.
You can also use the hostname of the machine or assign a fix address to the computer via the router's DHCP fixed leases table.

---

### Post by pqwoerituytrueiwoq on 2011-08-06
set a static ip address or use the computer's name
eg
ssh [EMAIL="me@lucid-desktop.local"]me@lucid-desktop.local[/EMAIL]
instead of 
ssh me@10.0.0.50
my computer name is *lucid-desktop* you add the *.local* to it and you will have a name instead of a ip address to connect to

---

### Post by Karlas on 2011-08-06
Oh Is there a way to find out username and hostname of that computer?????

---

### Post by Karlas on 2011-08-06
ssh: Could not resolve hostname xxx: Name or service not known

---

### Post by pqwoerituytrueiwoq on 2011-08-06
the default name is *username-deskop* or* username-laptop*
open your system monitor

edit 
your host name is set in these 2 files
/etc/hosts
/etc/hostname
edit them both to change your computers name (no spaces allowed)
restart the networking service after changing or reboot

---


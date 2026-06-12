---
title: "SSH login refused"
date: 2011-06-28
forum: General Help
---

### Post by sneakyimp on 2011-06-28
I cannot login to my Ubuntu 11.04 machine on my LAN using a terminal program from another machine.  I've managed to give my Ubuntu desktop a static IP address, but when I try to login from my other machine (Windows 7 using putty) I get 'connection refused'.

Where can I change this?  I've tried looking for 'ssh' in the main menu with no results.  'remote' turns up a few different control panels but none seem to address this.  'login' returns only the login screen.

Any help would be much appreciated.

---

### Post by spiky001 on 2011-06-28
Hi have you installed open ssh server on the machine you want to ssh into, have you tried ssh from another ubuntu machine?

---

### Post by seawolf167 on 2011-06-28
Install openssh server if you haven't already

```
sudo apt-get install openssh-server
```

If you want to change your port or config settings you can do that by editing this file

```
gksu gedit /etc/ssh/sshd_config
```

But if you leave it as is, the default port is 22, so from your Windows 7 box, go grab a copy of [Putty]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html"), enter the IP address of your remote machine and hit open to connect.

---

### Post by e79 on 2011-06-28
> **seawolf167 said:**
> Install openssh server if you haven't already

```
sudo apt-get install openssh-server
```If you want to change your port or config settings you can do that by editing this file

```
gksu gedit /etc/ssh/sshd_config
```But if you leave it as is, the default port is 22, so from your Windows 7 box, go grab a copy of [Putty]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html"), enter the IP address of your remote machine and hit open to connect.

+ 1

And to actually connect from the remote machine to your Ubuntu 11.04 :

from another linux distro, fire up a terminal and type :
# ssh user@ip_adress

from a windows box :
Download and install Putty as suggested and possibly WinSCP for easy file transfer over SSH.[URL="http://www.putty.org/"]
[/URL]

---

### Post by sneakyimp on 2011-06-29
Installing openssh did it.  I was under the mistaken impression that would be installed by default.  THANKS.

---

### Post by seawolf167 on 2011-06-29
> **sneakyimp said:**
> Installing openssh did it.  I was under the mistaken impression that would be installed by default.  THANKS.

No problem, glad it is working. The openssh *client* is installed by default, but the openssh *server* needs to be installed on new installations.

---


---
title: "how to get rid of / break dependances"
date: 2010-11-14
forum: General Help
---

### Post by arapaho on 2010-11-14
I'd like to uninstall openssh-client. I tried to uninstall openssh-client from Synaptic, but a weird thing happens. When I mark completely remove openssh-client Synaptic automatically marks openssh-server and ssh packets for installation. I don't wont neither of this services. This command doesn't work:
```
sudo apt-get purge openssh-client
sudo apt-get purge openssh-server ssh
```
When I purge openssh-client the second is installed, when I purge openssh-server ssh the first is installed. In synaptic when I type ssh I find this:
libssh-4
python-paramiko
libgnome-keyring0
gnome-keyring
libpam-gnome-keyring
x11-session-utils
ssh-skpass-gnome
libkdesu5
When I want to uninstall libssh-4 it wants to remove kdebase and kde programs. Although I use gnome I also use some KDE programs.
So, then I thought maybe to install ssh first and then uninstall all, but when I want uninstall ssh it wants to uninstall ubuntu-desktop.:confused:

---

### Post by 3rdalbum on 2010-11-14
Why do you want to remove the SSH client? It is taking up no memory unless used, and less than a megabyte on disk. Removing it also removes programs that have SSH features too, so you really don't want to remove it.

---

### Post by arapaho on 2010-11-14
I don't need it and from security point of view it is good to remove services that are not used.

---

### Post by blueridgedog on 2010-11-14
The client is not a server process and is used in the event that you want to use ssh to connect to a server.

---

### Post by matt_symes on 2010-11-14
Hi

A number of things can use ssh: scp rsync, remote desktop, etc. I would keep it.

Read this for ssh server. It shows techniques it lock down the server

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Kind regards

---

### Post by arapaho on 2010-11-14
I see. So, there is nothing to worry about with openssh-client. Thank you.

---


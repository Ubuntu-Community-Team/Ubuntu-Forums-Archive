---
title: "How to mount a remote filesystem locally via the Terminal."
date: 2011-02-23
forum: General Help
---

### Post by Katreyo on 2011-02-23
Hey guys, Gnome allows you to mount a remote filesystem to a local mount point via Places -> connect to a remote server.

My question is how can I do this via the command line? I use SSH to connect to the remote computer, it mounts nicely and is browsable in the gui.

I hear alot about a third party application called sshfs or something. I figure if the GUI can do this I do not need to install this, and would like not to.

I would like to know this because I will be creating a bash script to mount the system on startup.

I need to do this with the following criteria.
Protocol: SSH
Port: 22
Server: example.server.com
Username: ssh-user
Password: ssh-pass

Thank you for your time.

---

### Post by tredegar on 2011-02-23
You need to search on **nfs over ssh**
There are lots of HOWTOs out there.

Or just use [sshfs]("http://loki-render.berlios.de/index.php/docs/05x/19-howto-use-fusesshfs-with-an-ubuntulinux-farm") which will work fine from the command line.

---

### Post by Wtower on 2011-02-23
Also the following may be helpful:

[https://help.ubuntu.com/community/SSH/TransferFiles](https://help.ubuntu.com/community/SSH/TransferFiles)
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---


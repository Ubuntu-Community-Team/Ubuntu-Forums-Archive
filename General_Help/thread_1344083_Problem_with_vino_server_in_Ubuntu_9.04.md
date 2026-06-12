---
title: "Problem with vino server in Ubuntu 9.04"
date: 2009-12-02
forum: General Help
---

### Post by lz1dsb on 2009-12-02
Hi folks, 
I'm experimenting a bit with ways to access the Ubuntu desktop remotely these days and I got into this problem: I'm using Ubuntu 9.04 and a vino server. The most simple configuration ever, as the vino server is quite easy to configure and integrated into GNOME. I'm using the vino server flawlessly in Ubuntu 8.04 on another machine. So I'm quite confused why this isn't working here in Jaunty. Basically I start the server from the menu System -> Preferences -> Remote Desktop. The first strange thing is that I don't have tabs in the vino-server configuration window, so I can't control whether the server is supporting encryption or not, and some additional configs. But when I open the Configuration Editor in the remote desktop section I see all options. There I choose that I don't want to have encryption since I'm using the free RealVNC client which doesn't support encryption. When I try to connect I get the following error on the VNC client:"No matching security types" and I'm unable to establish the connection. I tried to reinstall the vino package, but the result is the same. I noticed the following error messages in the log:
/var/log/dpkg.log
2009-12-02 21:32:08 status half-configured vino 2.26.1-0ubuntu1
2009-12-02 21:32:20 status half-installed vino 2.26.1-0ubuntu1
2009-12-02 21:32:20 status config-files vino 2.26.1-0ubuntu1
2009-12-02 21:32:20 purge vino 2.26.1-0ubuntu1 2.26.1-0ubuntu1
2009-12-02 21:32:20 status config-files vino 2.26.1-0ubuntu1
2009-12-02 21:32:20 status config-files vino 2.26.1-0ubuntu1
2009-12-02 21:32:20 status config-files vino 2.26.1-0ubuntu1
2009-12-02 21:32:21 status config-files vino 2.26.1-0ubuntu1
2009-12-02 21:32:21 status config-files vino 2.26.1-0ubuntu1
2009-12-02 21:32:21 status not-installed vino <none>
2009-12-02 21:33:08 startup archives unpack
2009-12-02 21:33:09 install vino <none> 2.26.1-0ubuntu1
2009-12-02 21:33:09 status half-installed vino 2.26.1-0ubuntu1
2009-12-02 21:33:09 status unpacked vino 2.26.1-0ubuntu1
2009-12-02 21:33:09 status unpacked vino 2.26.1-0ubuntu1
2009-12-02 21:33:11 startup packages configure
2009-12-02 21:33:11 configure vino 2.26.1-0ubuntu1 2.26.1-0ubuntu1
Does anyone know what "half-installed" and "half-configured" mean? It doesn't seem to be right... How can I debug the vino server in more detail?

Regards,
Boyan

---

### Post by lz1dsb on 2009-12-02
I also noticed something else which I forgot to mention. When I disable the vino server, I still see ports 5900 and 5800 as open from the output of "nmap localhost". So whatever the vino server is enabled or disabled, those ports are staying open. When I try to access the machine via the browser on port 5800, I only get 
ISD 001.000
 This doesn't seem to be right... Any ideas.

---


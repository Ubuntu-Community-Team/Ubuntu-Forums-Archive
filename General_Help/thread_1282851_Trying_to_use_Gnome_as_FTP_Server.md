---
title: "Trying to use Gnome as FTP Server"
date: 2009-10-04
forum: General Help
---

### Post by madmatter23 on 2009-10-04
Hello,

I'm following a 6 step tutorial in order to set up my installation of GNOME (2.26.1) as a file server. I've made it to step 6 and hit a snag setting up the shell access. I'm hoping that someone can tell me where I've gone wrong.

Here's a link to the tutorial: 
[http://www.intac.net/build-your-own-server/](http://www.intac.net/build-your-own-server/)

The tutorial is based off of xUbuntu, so maybe that's where I'm running into trouble?

I've gotten as far as installing openssh-server and x11nvc, but the following terminal commands aren't working out.

After typing "vncpasswd ~/.vnc/passwd", I get a message saying "bas: vncpasswd: command not found." The message also informs me that the program 'vncpasswd' can be found in tightvncserver and vnc4-common software packages.

Typing "echo 5900 > ~/.vnc/port" results in a message saying "bash: /root/.vnc/port: No such file or directory".  

Can someone please let me know what I'm doing wrong?

Thanks!

---

### Post by fluffman86 on 2009-10-04
sudo apt-get install tightvncserver 

will install a VNC server and set up the password right after.  If it doesn't set up the password, just run

vncpasswd

---


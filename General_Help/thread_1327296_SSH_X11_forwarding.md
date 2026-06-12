---
title: "SSH X11 forwarding"
date: 2009-11-15
forum: General Help
---

### Post by iguanodon on 2009-11-15
I'm trying to run a GUI application on a remote host and display it on my Jaunty box.  The remote host is running CentOS 5.3.  I open a terminal on the Jaunty box , ssh to the CentOS box and launch the app, but I get "Error: Unable to initialize gtk, is DISPLAY set properly?"  I have tried 'ssh -X', 'ssh -Y', and even manually setting the DISPLAY variable on the remote box to point to the Jaunty box. Here is the X11 config from /etc/ssh/sshd_config on the Jaunty box:

X11Forwarding yes
X11DisplayOffset 10

and on the CentOS box:

X11Forwarding yes
X11DisplayOffset 10
#X11UseLocalhost no

I've tried setting 'X11UseLocalhost yes' but it didn't help.

If I do 'ssh -v -X' it shows "debug1: Requesting X11 forwarding with authentication spoofing."

What else can I check ?

---

### Post by chuck_theobald on 2011-06-17
Any ideas on this one? Two years and counting.

---

### Post by Habitual on 2011-06-18
[http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html](http://tldp.org/HOWTO/XDMCP-HOWTO/ssh.html)

---

### Post by iguanodon on 2011-06-21
> **chuck_theobald said:**
> Any ideas on this one? Two years and counting.

I think in my case the problem was a botched installation of X11 on the remote (CentOS 5.3) box.  I had originally set up the box without any GUI because it always ran headless.  At some point I wanted to run GUI apps so I installed X11 through yum.  That worked fine if I had a monitor attached but the remote display thing never worked.  I ended up retiring that box and replacing it with one running CentOS 5.5.  This time I selected X11 and Gnome with the original installation and the remote display works fine.  I must have missed some piece of the puzzle when installing X11 after the OS install.  I would like to think that yum would take care of that but it seems to have missed something.

---


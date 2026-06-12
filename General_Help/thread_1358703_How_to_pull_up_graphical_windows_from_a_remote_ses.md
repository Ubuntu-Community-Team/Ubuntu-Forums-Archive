---
title: "How to pull up graphical windows from a remote session?"
date: 2009-12-18
forum: General Help
---

### Post by cknight on 2009-12-18
At the moment, I've got an ssh connection from my home laptop to my linux machine at work.  How can I get graphical programs launched on my work machine to display on my home machine?  I'm sure this is possible and have a high level understanding of what needs to be done, but I just can't figure it out.

For example, after ssh'ing to work.computer, I tried exporting my DISPLAY (on work.computer) using the following values:
```
export DISPLAY some.ip.address:0.0 (as taken from http://www.whatsmyip.org)
export DISPLAY 192.168.1.2:0.0 (as taken from inet addr in ifconfig)
```
However, if I then launch xterm on the work computer, nothing happens on my home computer.  Any advice/help?  Thanks

---

### Post by lykwydchykyn on 2009-12-18
You have to make sure:
 - X forwarding is enabled on the server end in /etc/ssh/sshd_config
 - X forwarding is enabled on the client end in /etc/ssh/ssh_config

You can force X forwarding enabled on the client end with the -X switch on ssh, but it has to be enabled on the server end also to work.  Not sure if this is default in Ubuntu, but at one time it wasn't as I remember having to manually enable it.

After that, there's nothing else to do.  Just launch the apps and they run.  Don't mess with DISPLAY, it should be set automatically.

---

### Post by cknight on 2009-12-18
> **lykwydchykyn said:**
> You have to make sure:
 - X forwarding is enabled on the server end in /etc/ssh/sshd_config
 - X forwarding is enabled on the client end in /etc/ssh/ssh_config

You can force X forwarding enabled on the client end with the -X switch on ssh, but it has to be enabled on the server end also to work.  Not sure if this is default in Ubuntu, but at one time it wasn't as I remember having to manually enable it.

After that, there's nothing else to do.  Just launch the apps and they run.  Don't mess with DISPLAY, it should be set automatically.

Brilliant, thanks!  The '-X' flag was all that I was missing.

---


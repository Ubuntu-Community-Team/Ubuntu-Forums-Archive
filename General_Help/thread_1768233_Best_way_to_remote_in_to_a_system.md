---
title: "Best way to remote in to a system?"
date: 2011-05-26
forum: General Help
---

### Post by Roasted on 2011-05-26
In the past, VNC has been a bust for me. I've set up VNC on some Ubuntu machines and it never fully works. For example, if I'm remoting in from system A to system B, when I click on things on system A I never see them show up. However, if I'm in the same room as system B, I can see the windows and menus opening accordingly, which is something I don't see via the remote session.

What's the best way to get this job done? Would VPN be a better option or something?

Also - side question - does anybody know how to check the smart status of a hard drive via terminal?

---

### Post by JRV on 2011-05-26
I like to use XDMCP.

To enable XDMCP server in Ubuntu 9.04 (Jaunty) and before:

   gksudo gedit /etc/gdm/gdm.conf.custom

For Ubuntu 9.10 (Karmic) and after: 

   gksudo gedit /etc/gdm/custom.conf

Add the following lines:

[xdmcp]
Enable=true
MaxPending=4
MaxSessions=16
MaxWait=15

Then, restart gdm with the command:

   sudo /etc/init.d/gdm restart

or reboot the PC.
-------------------------------------------------------


To use an XDMCP client you must install Xephyr with the command:

   sudo apt-get install xserver-xephyr

XDMCP will then be available after login from the command line, I use:

 Xephyr :1 -query HOSTNAME -fullscreen -once

In Ubuntu 9.04 and before a XDMCP client is available from the gdm login screen, installing Xephyr and logging in is not necessary.

XDMCP is broken in Ubuntu 10.10 (Maverick), the Xephyr client will work but the server will not.

---

### Post by hwttdz on 2011-05-26
I go for ssh with x forwarding.  Super mature protocol, no issues. 

sudo smartctl --all /dev/disk

---

### Post by Roasted on 2011-05-26
> **hwttdz said:**
> I go for ssh with x forwarding.  Super mature protocol, no issues. 

sudo smartctl --all /dev/disk

Is there anything I need to install or configure, or is running that command all I need?,

---

### Post by Lars Noodén on 2011-05-27
> **Roasted said:**
> Is there anything I need to install or configure, or is running that command all I need?,

To forward X, you don't need anything installed on the remote machine except for OpenSSH-server.

If you tunnel X from your server, the graphical programs you run there will be displayed on your local machine.  So instead of the regular SSH connection, add **-X**

```

  ssh -l user [-X](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Remote_Processes#X11_Forwarding) server.example.org

```

It can be kind of slow with high-latency connections, but is otherwise fast.

---

### Post by linuxinstalledfromhdd on 2011-05-27
> **Roasted said:**
> In the past, VNC has been a bust for me. I've set up VNC on some Ubuntu machines and it never fully works. For example, if I'm remoting in from system A to system B, when I click on things on system A I never see them show up. However, if I'm in the same room as system B, I can see the windows and menus opening accordingly, which is something I don't see via the remote session.

What's the best way to get this job done? Would VPN be a better option or something?

Also - side question - does anybody know how to check the smart status of a hard drive via terminal?

It really depends on your level of experience with troubleshooting network connections on VPN and using RDC or Vino.  

My suggestion to more unexperienced userrs is to give Teamviewer 6 a try at least, because it connects to everything, not just Ubuntu.  Windows, MAC, Android, Linux. Everything. It's free for non-commercial use too. It would be the same LogMeIn or GoToMeeting for windows, if you are more familiar with Windows systems and remote desktop connections.

---


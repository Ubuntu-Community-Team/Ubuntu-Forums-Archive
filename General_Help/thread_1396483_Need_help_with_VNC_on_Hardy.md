---
title: "Need help with VNC on Hardy"
date: 2010-02-02
forum: General Help
---

### Post by asmith20002 on 2010-02-02
Hello. 

I have a VPS and I'm running ubuntu 8.04 LTS and I've setup a webserver and my site is running fine. I connect to my ubuntu terminal via PuTTy. 
I need to install a windows program (via wine), and I need to see the installation windows. So I need to see my linux desktop.

I read on the web that Hardy has already VNC installed and I ran this command to activate it: 

```

gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true 
```

and in /etc/ssh/sshd_config
I had made x11 forwarding to no. (when setting up my webserver), I changed that back to 'yes' and after that I upgraded my linux.

I installed tightVNC viewer. but I can't connect, I get 'invalid protocol'. 

I'm so newbie on linux. Please help me how to get this done.
Thanks for your time
I also want to roll back any changes after I'm done with my installation.

---

### Post by gmargo on 2010-02-02
I believe you are confusing VNC with Remote Desktop access.

On your server, install either **vnc4server** or **tightvncserver**.

Then start the vncserver, which will run a whole desktop on a virtual screen.

Use your local vncviewer with a -via option to display the remote desktop.
The vncviewer will establish an SSH connection and tunnel all the traffic over it.

---


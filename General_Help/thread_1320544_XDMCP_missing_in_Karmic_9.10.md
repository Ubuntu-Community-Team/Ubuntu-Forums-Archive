---
title: "XDMCP missing in Karmic 9.10?"
date: 2009-11-09
forum: General Help
---

### Post by PeggySue on 2009-11-09
Hi,
I was using XDMCP in 9.04 but this appears to have been removed from 9.10 with no hints as to what the replacement is, if any.  Following the threads suggest I should be using ssh but I have tried setting up ssh from my 9.10 laptop to my 9.10 desktop and can't get to a login screen.  I can log on to a terminal on the desktop machine but can't open an X window to run GUI applications.  
Using ssh user@remote -X doesn't give errors but just returns me to the terminal.  I was hoping for a login window!  Any ideas?

Also; any ideas why the Ubuntu team think it is a good idea to remove features without suggesting how to work around the chaos this causes?  I would love to know how to make inputs to the people that make these decisions.

Thanks.

---

### Post by sefs on 2009-11-09
You can still turn it on and off by manually editing /etc/gdm/gdm-custom.conf for the time being.

---

### Post by PeggySue on 2009-11-09
Thanks sefs.

I don't have a gdm-custom.conf in /etc/gdm. I do have a custom.conf but this doesn't mention XDMCP.  Thanks for the guidance that XDMCP can be reenabled and I will google gdm to find out more.

---

### Post by sefs on 2009-11-09
Yes that's it ... it's custom.conf now.

and enabling xdmcp is as easy as opening this file and placing in it...

```

[xdmcp]
Enable=true

```

May need to reboot too I believe.

---

### Post by skotos on 2009-11-10
Well, I have even added the empty sessions from /usr/share/doc/gdm/examples/custom.conf under a newly created /etc/gdm/custom.conf (because I did not have it), but no way to successfully open a remote XDMCP session.

And... UDP port 177 is not blocked by the firewall...
Any idea on what to look for?

---

### Post by kisuke on 2009-12-03
Hi,

my (server) /etc/gdm/custom.conf file:

> 
# GDM configuration storage
[xdmcp]
Enable=true

[chooser]

[security]

[debug]


with that, xdmcp work but only for one session, then is necesary restart gdm (in the server), with jaunty it work fine..., with karmic gdm looks good but work horribly, bye!

---

### Post by PeggySue on 2009-12-04
Thanks for the inputs.

I also have a secure shell login with X now.

I can't decide which is best ssh or XDMCP!!

---

### Post by nickmcg on 2009-12-08
> **PeggySue said:**
> Thanks for the inputs.

I also have a secure shell login with X now.

I can't decide which is best ssh or XDMCP!!
How did you get your secure login shell?

Thanks

Nick

---

### Post by PeggySue on 2009-12-09
The secure shell was easy but I can't remember the detail off hand.  I'm sure it was just install openssh-server and openssh-client and log in using ssh -X username@192.168.1.3 with a yes to the first question!

The things that made me think were starting X-Window applications over ssh.  It's the -X switch. 
And dynamic IP addresses which I still haven't bothered to fix because they nearly always come up the same each time.

The basic link is
[http://principialabs.com/beginning-ssh-on-ubuntu/]("http://principialabs.com/beginning-ssh-on-ubuntu/") 

I also bookmarked these:[https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto]("https://help.ubuntu.com/community/SSH?action=show&redirect=SSHHowto") for the Ubuntu view and
[URL="http://support.suso.com/supki/SSH_Tutorial_for_Linux#X11_Session_Forwarding"]
http://support.suso.com/supki/SSH_Tutorial_for_Linux#X11_Session_Forwarding[/URL] for X11 forwarding.

The other thing of note was choosing between password authentication and public key. It's all in the links.


For info; I also find NFS usefull for sharing files.[http://ubuntuforums.org/showthread.php?t=249889]("http://ubuntuforums.org/showthread.php?t=249889")

Hope this helps.

---

### Post by nickmcg on 2009-12-11
Thanks for that PeggySue - I'd got to ssh -X user@machine, but from your post, I (mis)read that you'd managed a secure XDMP-type connection.

Useful links tho' - especially the publickey / password information

Cheers

Nick

---

### Post by staffann on 2009-12-26
I''ll continue on this thread rather than starting a new one if you don't mind. I want to use Xming on my windows laptop to log into my Ubuntu 9.10 server. I can do that using ssh (puttylink) and open an x-terminal. After searching this forum I found that if I start gnome-panel I almost get the normal desktop.

The problem is that there isn't any windows handler - no frames around the windows that I open so I cannot drag and close them easily. Is there a way of fixing that?

---

### Post by staffann on 2009-12-30
I'll anwser my own question: Using
```
gnome-session
```
seems to work fine.

---

### Post by onurgu on 2010-01-26
I was looking for an answer here. I was about to create /etc/gdm/custom.conf myself but I saw that there is /etc/gdm/gdm.schemas

When I open it, I saw that there is a section for XDMCP. I just enabled it from there.

Thanks for the help though.

---


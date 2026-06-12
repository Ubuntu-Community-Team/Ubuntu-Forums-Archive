---
title: "vpnc working under Virtualbox under Windows but not on Linux host"
date: 2010-08-21
forum: General Help
---

### Post by megathaum on 2010-08-21
I'm trying to use vpnc to connect to our company's VPN. I first tested it on a Windows host under Virtualbox everything works straight away. But when I want to use the same version of vpnc  (0.5.3) with the same conf file on a Linux host directly it always ends in "No response from target". I have searched hi and low on the internet for anything related to this error message and tried the typical solutions to no avail.

But since it works under Virtualbox it can't be a configuration issue. So I thought of firewall settings but iptables -L on returns an empty list even.

Anyone has an idea what else it might be? What is the difference between running vpnc under Virtualbox on a Windows host and running it directly on Linux??

---

### Post by luisito on 2010-08-21
I don't know why the windows version would work and the linux wouldn't in your case. If the reason you can't connect is some firewall problem, it may work to use ssh tunneling. This is the magic solution that someone told me today and worked for me. If you run in your computer
ssh -L 5901:localhost:5901 -l <yourloginname> <theservername>

Then you can connect to your local host instead to the server in the VNC client, with a command like vncviewer localhost:1 or whatever the command is for vpnc.

---

### Post by gaussian on 2010-08-21
> **luisito said:**
> I don't know why the windows version would work and the linux wouldn't in your case. If the reason you can't connect is some firewall problem, it may work to use ssh tunneling. This is the magic solution that someone told me today and worked for me. If you run in your computer
ssh -L 5901:localhost:5901 -l <yourloginname> <theservername>

Then you can connect to your local host instead to the server in the VNC client, with a command like vncviewer localhost:1 or whatever the command is for vpnc.

Little confusion here: VPNC <> VNC. Have used both, your advise is good for VNC. Very understandable though, acronyms :mad:

As for original problem: sometimes magically things start working if you add:
```

NAT Traversal Mode cisco-udp

```

into your /etc/vpnc.conf

---

### Post by megathaum on 2010-08-23
Thank you guys for your suggestions. The problem is indeed with vpnc and not VNC. I have tried adding that line in vpnc.conf, unfortunately the magic didn't happen :(

Any other ideas?

---

### Post by gaussian on 2010-08-24
I think it could still be Ubuntu Firewall. After this I am out of ideas. I would just try by first doing:
```

sudo service ufw disable

```

And then try to connect. If it works after this, then the problem is probably Ubuntu's Firewall. Obviously you want to enable the firewall after the test. And if it works after disabling the firewall, you'll need to figure out what ports to open.

And yes, I did read the part about it working on Virtualbox. But it never hurts to try.

---

### Post by megathaum on 2010-08-24
No, it never hurts to try and i'm frustrated enough to try any suggestion (even more than once). 
So 
sudo service ufw disable
gives the following error
"Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service ufw disable
The script you are attempting to invoke has been converted to an Upstart job, but disable is not supported for Upstart jobs."
:lolflag:

Anyway, I tried sudo ufw status and it returns "Status: inactive" so I suppose it is not the firewall ...

---

### Post by gaussian on 2010-08-25
Ok. I am out of ideas on how to fix things, but maybe try the following to help with the diagnosis:

1. Try debug mode in vpnc:
```

sudo vpnc --debug 2

```

You can change 2 to 3 or 99 too. 

2. See if anything happens in dmesg-logs when you try to use vpnc:
```

sudo dmesg -c
sudo vpnc
dmesg

```

Note: the first command here clears the log. You might not want to do that, instead you can record in your mind what was the last entry in dmesg before you gave the "sudo vpnc"

These might give you ideas on what to google.

---

### Post by megathaum on 2010-11-11
Problem solved. 

Following this wiki [http://www.gentoo-wiki.info/Vpnc](http://www.gentoo-wiki.info/Vpnc) I added to my conf file
Local Port 10000
And all worked splendidly. I'm sure I tried this before but maybe meanwhile I changed something else. Anyway, all's well that ends well.

:popcorn:

---


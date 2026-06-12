---
title: "Questions about the firewall"
date: 2011-04-03
forum: General Help
---

### Post by PCaddicted on 2011-04-03
Hello,
I have installed the graphic user interface for IPtables and enabled this firewall.However,I find it a bit strange.What is the difference between rejecting and denying the traffic?If I want to configure IPtables as two-way,how can I define which of my apps can connect to the internet and which can't?If this firewall is enabled,does it really run in the background,protecting the user,or does it run only when its GUI is opened?

---

### Post by 5149.5 on 2011-04-03
Thee are a few GUIs for firewall. Which one are you using?

---

### Post by PCaddicted on 2011-04-03
I typed sudo apt-get install gufw in the terminal in order to install the GUI.
So...it's the GuFW interface,as it says at Help>About

---

### Post by ajgreeny on 2011-04-03
If you have no server applications running you probably do not need to do anything at all, not even run gufw, assuming that is what you ran.

There is a lot of misunderstanding about firewalls and other security measures that can be taken in Ubuntu, but I have always just installed the system and used it.  When I had a dual boot with windows I occasionally ran clamav on my data files which could be used by both OSs, but now I don't do anything after installing the OS.

The firewall, iptables, runs all the time in the background in a Ubuntu installation; the only reason you might need to configure it any further is if you have a server, eg mail server, running which needs ports constantly open and listening for connections.

See [https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security) for lots more info.

---

### Post by WorMzy on 2011-04-03
DROP (I'm guessing that's what you meant by deny) = Discard the packets and pretend they never arrived.
REJECT = Acknowledge the packets were received, send back an error packet, then discard the received packets.

You can probably restrict outbound connections, though I haven't set any up myself. Check google for a tutorial on it if you're interested.
The iptables daemon is running even when the GUI isn't.

---

### Post by bodhi.zazen on 2011-04-03
> **PCaddicted said:**
> Hello,
I have installed the graphic user interface for IPtables and enabled this firewall.However,I find it a bit strange.What is the difference between rejecting and denying the traffic?If I want to configure IPtables as two-way,how can I define which of my apps can connect to the internet and which can't?If this firewall is enabled,does it really run in the background,protecting the user,or does it run only when its GUI is opened?

Linux does not use application firewalls, ie you do not restrict internet access by application.

You can restrict outbound traffic, but you have to understand how a firewall works.

Yes, on linux the graphical applications (gufw, firestarter, etc) are intended as configuration tools. You configure your firewall and then close the graphical application.

---

### Post by PCaddicted on 2011-04-04
Thus it is impossible to configure IPtables so that it displays a warning when an app is trying to connect to the Internet,isnt it?

---

### Post by bodhi.zazen on 2011-04-04
> **PCaddicted said:**
> Thus it is impossible to configure IPtables so that it displays a warning when an app is trying to connect to the Internet,isnt it?

iptables does not perform "application filtering", no, this is a windows "security" method.

You will get various opinions, and I do not use Windows much, but last time I looked, it was rather trivial to circumvent this "technology" in Windows.

---

### Post by WorMzy on 2011-04-04
If you want to prevent specific applications from accessing the internet, I think you need to look at SELinux, AppArmor or Tomoyo Linux. I don't use these, so I may have misunderstood their purpose, but at a glance it seems like this is the sort of thing they do.

---

### Post by PCaddicted on 2011-04-09
Does AppArmor have a GUI?

---

### Post by WorMzy on 2011-04-09
As far as I know -- no. I think all three I mentioned are configured by CLI only. There's a bunch of tools available to help you manage profiles in the apparmor-utils package though.

---


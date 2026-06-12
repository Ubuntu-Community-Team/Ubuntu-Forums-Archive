---
title: "How do I enable Gufw tray icon in Ubuntu Lucid Lynx (10.04)"
date: 2010-11-11
forum: General Help
---

### Post by agentfortyseven on 2010-11-11
Hi everyone,
I was just wondering if there's a way to enable tray icon for Gufw in Ubuntu 10.04. I remember there used to be an option for doing that in Ubuntu 9.10. Any suggestions?

---

### Post by Frogs Hair on 2010-11-11
Install firewall configuration from the repository, which is the gui for the firewall . It will appear under the administration menu , next , enable it , then you can drag the icon where you like.

---

### Post by marquinos on 2010-11-12
Hi! You'll have again for Ubuntu 11.10 :)

---

### Post by endotherm on 2010-11-12
> **agentfortyseven said:**
> Hi everyone,
I was just wondering if there's a way to enable tray icon for Gufw in Ubuntu 10.04. I remember there used to be an option for doing that in Ubuntu 9.10. Any suggestions?

I don;t have gufw on this box, but if I recall correctly, the tray applet ran whenever it was running, and the trick to keep it running was to set it to launch at startup and to minimize (to the tray) on close.

---

### Post by agentfortyseven on 2010-11-12
Hey guys,
Thanks for your replies. Well I've figured out the best and the easiest way of doing that.
All you need to do is: 
1) Go to main menu < system < administration.
2) You'll see Gufw icon in the list.
3) Just right click on that icon and choose add to panel. (you might add it to desktop if you like)

What do you say guys? Isn't that easy?:)
Please do tell me if this method is not good enough?

P.S : If only Gufw had animated icon, SIGH:neutral:

---

### Post by agentfortyseven on 2010-11-12
> **Frogs Hair said:**
> Install firewall configuration from the repository, which is the gui for the firewall . It will appear under the administration menu , next , enable it , then you can drag the icon where you like.
Thats another cool suggestion.

---

### Post by agentfortyseven on 2010-11-12
> **endotherm said:**
> I don;t have gufw on this box, but if I recall correctly, the tray applet ran whenever it was running, and the trick to keep it running was to set it to launch at startup and to minimize (to the tray) on close.
Well I might very well enable it on startup, but there isn't any option that minimizes it to tray. This one looks a bit difficult though as starting Gufw requires sudo privilege, so you'll be prompted for a password on system startup.

---

### Post by endotherm on 2010-11-12
> **agentfortyseven said:**
> Well I might very well enable it on startup, but there isn't any option that minimizes it to tray. This one looks a bit difficult though as starting Gufw requires sudo privilege, so you'll be prompted for a password on system startup.
yeah, thats the downside to it. 
I am not sure where you are at with your ubuntu experience, so I'll offer this advice. take it or leave it. 
you don;t really need gufw running on the regular. you only need it when you want to make a change to your firewall configuration. gufw is a frontend that ultimately configures the netfilter firewall in your kernel. the firewall is running as long as your system is, so most people only need gufw once in a blue moon. 

additionally, I don;t know what kind of rig you have, but unless you have special services you want to expose to some groups but block to others (for instance allowing http access to the public intranet, but restricting ssh access to a local subnet, or blocking it entirely), then you likely don't need a firewall at all. by default ubuntu ships with no open ports, so unless you install network services, there really isn't anything to block or allow.

---

### Post by agentfortyseven on 2010-11-13
> **endotherm said:**
> you don;t really need gufw running on the regular. you only need it when you want to make a change to your firewall configuration. gufw is a frontend that ultimately configures the netfilter firewall in your kernel. the firewall is running as long as your system is, so most people only need gufw once in a blue moon. 
I've heard that over a million times before. But I prefer to see my Gufw icon in the tray irrespective of whether it makes any difference or not. I prefer it that way:P

---

### Post by aaron@roydhouse.com on 2011-03-15
The real answer is that older versions of gufw used to include options to appear in the system try (e.g. 9.04 version, certainly the 0.20.7 version). These option were under preferences. Now these options have been removed. Apparently the-power-that-be didn't like you running it all the time in the system tray.

Here are the way the preferences used to look in 2009:
[http://www.blog.arun-prabha.com/2009/06/05/gufw-firewall-for-ubuntu-linux/](http://www.blog.arun-prabha.com/2009/06/05/gufw-firewall-for-ubuntu-linux/)

I would like the system tray option back. Not because I want to change rules frequently, but because the system tray icon told me if ufw was enabled or not. Occasionally I have to temporarily disable it to allow some activity. There is no temporary disable option, and your choice persists even after a reboot. A couple of times now I have found my firewall has been disabled for some time. This didn't happen when I has the system tray gufw option, because it provided a visual indicator of it was enabled or disabled.

I guess we need to locate an old version or patch ourselves a fork to get the system tray enabled/disabled indicator back.

---


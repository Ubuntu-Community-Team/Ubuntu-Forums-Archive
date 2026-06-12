---
title: "Network Manager Applet Install Killed Network Manager"
date: 2011-10-29
forum: General Help
---

### Post by demonboy on 2011-10-29
I've been having problems with my Broadcom BCM4313 creating an ad hoc network. I came across [this]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/830178") bug report and a workaround, which involves installing a new version of Network Manager Applet, network-manager-applet 0.9.1.90-0ubuntu6. I downloaded it and had to make it (never done this before) and it involved installed a number of additional files. These included packages like 'libnm-glib', 'lib-notify-dev' 'libpolkit-backend-dev-1', amongst others.



Once completed it has wiped my Network Manager icon from the top bar. I'm writing this from another computer as I'm unsure what to do next. I cannot connect that computer in any other way other than my usual 3G dongle.

When I type 'nm-applet' in Terminal I get:

```

...using gtk+ 2.x and gtk+ 3 in the same process is not supported
Trace/breakpoint trap...

```
I guess the error message is fairly obvious but what is the solution? What should I uninstall? I notice GTK2 has more dependencies. Was GTK3 installed when I updated the applet? 

I've looked at my dpkg.log file and there are literally hundreds of packages installed in this process, so going through them individually is not practical.

What should I do? How do I uninstall what I have just installed?

---

### Post by gandaran on 2011-10-29
> I guess the error message is fairly obvious but what is the solution? What should I uninstall? I notice GTK2 has more dependencies. Was GTK3 installed when I updated the applet? 
Ubuntu 11.10 uses GTK3
> What should I do? How do I uninstall what I have just installed?
depends on what type of package you used to install, you said you had to make it so I'm assuming it was compiling source code, to remove you have to compile the package again but when comes to the part of 'make install' you use 'make uninstall' command instead.

---

### Post by demonboy on 2011-10-30
That's great, gandaran, didn't realise it would be that simple. I thought there were dependencies on both versions because I'm sure the gwibber client, for example, uses GTK2. At least this gets me back to my original state and sorted my mess, so thanks for that. 

Sadly it looks like I'm going to have to do without an ad hoc network until there is a solution that comes with an auto update. I have little inclination to waste another two days trying to get one set up with the result of trashing my installation!

Thanks for your time.

---


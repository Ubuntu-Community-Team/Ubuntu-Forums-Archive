---
title: "Unable to get Firestart to start on start-up"
date: 2010-07-20
forum: General Help
---

### Post by unknown user on 2010-07-20
I have been unable to Get my Firestarter Firewall to start on system start up. I have done a Google search and found out that I need to add it to System>Preference>Sessions>Startup Programs. I have added the following command line (sudo/usr/sbin/firestarter), but it will not start on my system start up. 

Any ideas?

---

### Post by davidmohammed on 2010-07-20
this is a relatively [old thread]("http://ubuntuforums.org/showthread.php?t=542756") - but hopefully will point you in the right direction.

---

### Post by philinux on 2010-07-20
> **unknown user said:**
> I have been unable to Get my Firestarter Firewall to start on system start up. I have done a Google search and found out that I need to add it to System>Preference>Sessions>Startup Programs. I have added the following command line (sudo/usr/sbin/firestarter), but it will not start on my system start up. 

Any ideas?

Its a gui for configuring iptables which is the firewall. Better is gufw from synaptic. You do not need the gui to run at startup. Also if you have a router then you have a hardware firewall.

---

### Post by unknown user on 2010-07-21
I have been reading the links and have now got my Firestarter to start on boot up by adding (gksu "firestarter --start-hidden" &) to System>Preference>Sessions>Startup Programs>Add. All I need to do now is find out how to get Firestarter to start without adding my password. Sure that will be next. Does it matter that I added gksu and not sudo?

---

### Post by davidmohammed on 2010-07-21
the last post in the link I gave you made it clear which file you need to run that command from.  You can't do it via "startup programs" without editing your sudoers file - bad idea from a security point of view.

Have you tried the method described in the first post?  Seems simple enough to me.

---

### Post by bodhi.zazen on 2010-07-21
> **unknown user said:**
> I have been unable to Get my Firestarter Firewall to start on system start up. I have done a Google search and found out that I need to add it to System>Preference>Sessions>Startup Programs. I have added the following command line (sudo/usr/sbin/firestarter), but it will not start on my system start up. 

Any ideas?

Disclosure - Firestarter is an old application, I suggest you use a different application to manage your firewall (iptables).

You do not need Firestarter to "run". Firestarter is a configuration tool, you run it , configure your firewall, and close the application. There is no need to open or run the program unless you need to change/edit your firewall configuration.

Running firestarter all the time, as root, to monitor your network traffic is a security risk, use an alternate application such as wireshark or snort.

I know that is not the answer you are looking for, but it is the best advice I can give you.

---

### Post by unknown user on 2010-07-22
Hi davidmohammed, your link was of great help along with the ones that were within it and I thank you for it.

bodhi.zazen, thanks for that I willlook into it. I have the firewall (iptables)fixed and running now (or I beleive I do), via the link posted above.:D

---

### Post by unknown user on 2010-07-29
Firestarter is now starting when I boot the system up. I had to use gksudo rather than sudo in the command line

---

### Post by philinux on 2010-07-29
> **unknown user said:**
> Firestarter is now starting when I boot the system up. I had to use gksudo rather than sudo in the command line

**But it is totally unnecessary** and it is an old app. gufw is now the application to use.

IPTABLES is THE firewall gufw is a front end to change settings therefore does not need to run at startup. IPTABLES runs at startup in the background for you.

This is not Windows.

---

### Post by 3rdalbum on 2010-07-29
> **unknown user said:**
> Firestarter is now starting when I boot the system up. I had to use gksudo rather than sudo in the command line

I don't think you're listening to what is being said. Firestarter is merely the configuration utility. The underlying firewall runs as soon as the kernel starts running.

It's like when you're using Windows Firewall, you don't need to keep the settings window open, because it's just the settings window. Well, Firestarter is just the settings window for the Linux kernel firewall.

---

### Post by mwelchuk on 2010-08-12
> **philinux said:**
> **But it is totally unnecessary** and it is an old app. gufw is now the application to use.

I disagree. In very simple situations you are completely right, but gufw does not offer some of the configuration options that Firestarter does. For instance, Firestarter can be used to configure NAT for network connection sharing by clicking a few buttons - gufw doesn't seem to be able to do this.

---

### Post by bodhi.zazen on 2010-08-12
> **mwelchuk said:**
> I disagree. In very simple situations you are completely right, but gufw does not offer some of the configuration options that Firestarter does. For instance, Firestarter can be used to configure NAT for network connection sharing by clicking a few buttons - gufw doesn't seem to be able to do this.

Well, at some point you will have to face the music, firestarter is an unmaintained application.

My understanding is you will no longer be able to run firestarter on Ubuntu 10.10.

You will, in the long run, need to find an alternate application or learn iptables.

for the average desktop user, ufw is sufficient, gufw if you want a graphical interface. The vast majority of desktop users are not configuring NAT on their desktop computer.

Server side there are several far superior tools, many web based, some whole distros specifically tailored to serve as a gateway. Personally if you are using firestarter on a gateway computer, that implies you have X and a graphical desktop installed and IMO that is a significant security risk.

Again there are several superior tools, more secure, maintained, graphical, web based, and distro based.

---

### Post by Veld on 2010-08-12
Hello. First of all, I'm sorry if I shouldn't be posting in a thread marked as "solved".  I'm completely new to Ubuntu (well, Xubuntu in my case) and Linux in general, and I'm a bit confused (even after having read half a dozen topics on this subject and reading some documentation). So, if I understand correctly, Ubuntu already has a firewall by default which is iptables, and it runs on the background even for regular users? Firestarer and UFW are simply GUIs which make it easier to configure the firewall, right? :s

---

### Post by bodhi.zazen on 2010-08-12
> **Veld said:**
> So, if I understand correctly, Ubuntu already has a firewall by default which is iptables, and it runs on the background even for regular users? Firestarer and UFW are simply GUIs which make it easier to configure the firewall, right? :s

That is basically correct.

iptables runs as root and affects all users, unless you write a rule or rules that specifically apply to a specific user or group.

By default, there are no listing services (open ports) so there is nothing to firewall so iptables allows all traffic.

If you install a server or feel for some reason you want to configure a firewall, ufw and gufw are the default configuration tools. 

See :

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

Basically, ```
sudo ufw enable
``` is sufficient (if not over kill) for 99.99 % of desktop users.

Firestarter is an old old application and is no longer maintained. There have been no updates or bug fixes since 2005. Firestarter and ufw also conflict. So if you are new to Ubuntu , using firestarter is not, IMO, the best option.

Many "fanbois" (no offense intended) say firestarter has not been updated because there are no problems, which is not the case :

[Firestarter Bug List]("https://bugzilla.gnome.org/buglist.cgi?quicksearch=firestarter") 

As you can see, firestarter is essentially a dead project. It is at the end of life and, as I indicated, my understanding is it will not run on Ubuntu 10.10.

I suggest you read the security sticky at the top of the security forums.

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by Veld on 2010-08-12
Right. I get it now. Thanks!

---


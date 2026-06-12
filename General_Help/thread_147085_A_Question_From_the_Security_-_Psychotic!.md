---
title: "A Question From the Security - Psychotic!"
date: 2006-03-19
forum: General Help
---

### Post by Hangetsu on 2006-03-19
I've been very security-conscious with my PCs for the longest time, and have invested a lot of money over the years on anti-virus, anti-spyware, anti-rootkit, firewalls, etc. for my Windows machines.  I've made the move to Linux (after several dual-boot uses), and I'm definitely not looking back.

However, my knowledge of keeping a Linux box secure is not nearly as good as my knowledge for a Windows machine.  For example:

1) What should be my tools to watch over my machine?  I have chkrootkit thus far, and I'm considering BitDefender Linux and Firestarter (my router has a NAT firewall that seems to be "stealthing" my machine pretty well with Linux, so not sure if Firestarter is needed).

2) Where can applications be started?  In Windows, you would look at your registry, services, and startup to identify everything that should be running on your box.  How do I keep an eye out for rogue processes?

3) I never plan to connect to this machine from an outside one - is there anything I can do to prevent any type of outside telnet or other session to my machine?

4)  Is there a site that has all of these questions (and more answered)?

Thanks much for your help all, and I look forward to the reply!

---

### Post by ComplexNumber on 2006-03-19
> (my router has a NAT firewall that seems to be "stealthing" my machine pretty well with Linux, so not sure if Firestarter is needed). linux may well be significantly more secure than windows will ever be, but that is not to say that linux never gets hacked or has viruses. they're relatively extremely rare on linux, but its better to be safe than to be sorry. anyway, getting to the point...even though your ports are stealthed, thats not to say that you shouldn't use a software firewall as well as a router. i recommend that you use _both_. firestarter is a good and easy to use fiewall, so i would use that if i were you.

> 
2) Where can applications be started? In Windows, you would look at your registry, services, and startup to identify everything that should be running on your box. How do I keep an eye out for rogue processes? in general, you look though the /var/log/messages (i think). maybe someone can correct me on this. also, you can look through the list of running processes using the gnome-system-monitor.


> 3) I never plan to connect to this machine from an outside one - is there anything I can do to prevent any type of outside telnet or other session to my machine? make sure you have all unecessary daemons and services switched off. 

> 
4)  Is there a site that has all of these questions (and more answered)? these may be of use:
[http://www.linuxsecurity.com/]("http://www.linuxsecurity.com/")
[http://www.linux-sec.net/]("http://www.linux-sec.net/")

---

### Post by DarthMandeep on 2006-03-19
Please tell me you never paid money for any Norton software.

1) Anyways, I always suggest a software firewall in addition to a hardware firewall. Another layer of security is a good thing, especially if you are on a network with other users whose machines are running insecure software. Antivirus software like ClamAV, AVG for Linux, and F-Prot for Linux will help protect your Windows machines, so a scan every once in a while on network shares is a good idea. Some really useful tools if you have a network are nmap, nessus, and ethereal. The first two scan for open ports and vulnerable services. The last sniffs ethernet traffic. You could use Bastille to tighten the hatches on your system.

If you want to be really paranoid, or are running a server, look into Snort.

2) Applications can be monitored with the "top" and "ps aux" commands. System daemons (background processes) are located in the /etc/init.d/ directory. All the files in that directory are scripts to run services.

3) If you have a nat router and a software firewall, you don't need to worry about any network services on your desktop. Unless you've got uPnP on your router or are forwarding ports to services. If you're not using them get rid of telnet and ssh.

4) Give me a minute to sort through my bookmarks. 

Really though. If you have a NAT router and are using a modern, up-to-date distro and don't run apps as root, you've nothing to fear.

Unless you're running a server, like me :(

---

### Post by Hangetsu on 2006-03-19
Norton, ugh.  I used that back in 2000 when there wasn't much else, but I've been using Kaspersky or NOD32 off and on.  I was considering BitDefender on Linux as they've been pretty good lately - maybe I'll rethink that as I've seen F-Prot mentioned more than a few times.

No server services yet, although I expect I'll want to put a web server up locally every now and again to test out some Java code.  Nine times out of ten though, no server services will be running.

Thanks for the replies thus far!

---

### Post by jerrykenny on 2006-03-19
Go to system administration  login-screen-setup, and make sure remote logins are disabled.

Locally, you need to make sure your pc boots from the hard drive first, and you have a password on your BIOS.

Monitor the sytem from a terminal by entering the "top" command,   more usefull really for killing runaway processes 'though.

---

### Post by az on 2006-03-19
[QUOTE=Hangetsu]
1) What should be my tools to watch over my machine?  I have chkrootkit thus far, and I'm considering BitDefender Linux and Firestarter (my router has a NAT firewall that seems to be "stealthing" my machine pretty well with Linux, so not sure if Firestarter is needed).[/QUOTE]

What do you run?

[QUOTE=Hangetsu]
2) Where can applications be started?  In Windows, you would look at your registry, services, and startup to identify everything that should be running on your box.  How do I keep an eye out for rogue processes?[/QUOTE]

It depends on the package.  If it is an officially supported ubuntu package, it should have a menu entry.  If it is from universe, it may not have a menu entry in gnome, but you can install the "menu" package and that will create a Debian menu in you gnome menu where you will be able to see everything that has a debian menu included in the package.  You can also look at the contents of any package by listing the files.  Use synaptic or
dpkg -L (package)

Also, everything that is in the repositories is uploaded as source and then built.  There is a vre low probability that there is anything nasty there.  Do not install software from other sources, or, if you really must, which are distributed in binary-only form.


[QUOTE=Hangetsu]3) I never plan to connect to this machine from an outside one - is there anything I can do to prevent any type of outside telnet or other session to my machine?
[/QUOTE]

Don't install telnet, ssh or any other shell server.  The ssh client is installed by default, which means you can connect to other machines.  Since the server is not install by default, no one can connect to you.

---

### Post by airtonix on 2006-07-26
ummm you already have a software firewall running , firestarter is just a frontend. just though you may need this distinction, before wildly proclaiming that your system is a french whore to every internet packet.

proof : i installed open-ssh-server, and i had to open port 22, using the firewall config GUI called "firestarter". If i did not use the gui, i would have had to use ugly ipchain type commands. no thanks.

But as afar as using Bitdefender, mmmm. Clamav not good enough, I wanted on access scanning, which as far as i know isn't a feature of clamav. But as an another option check out Avast, as bitdefender is not free.

Check that your isp also scans incoming mail for viri before they get to your home network

---

### Post by ifokkema on 2006-07-28
System -> Administration -> Services shows a list of daemons running on your PC and allows you to turn them off using the GUI.

---


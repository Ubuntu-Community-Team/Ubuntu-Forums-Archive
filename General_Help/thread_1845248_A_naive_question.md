---
title: "A naive question"
date: 2011-09-16
forum: General Help
---

### Post by &gt;hankim&lt; on 2011-09-16
hello,

If I expose this doubt it's because I ignore much of how linux works so try not to scandalise but...

How secure is actually it? I feel like it's much more malleable than other OS, and so I also feel that for someone who knows how to work it, he could get through your sistem like the fish swim on water! I also know that the community looks after the common welth, but just in case someone would want to scan you or whatever he could find the way...

am I right?

---

### Post by sanderd17 on 2011-09-16
See security by obscurity vs security by design: 

[http://en.wikipedia.org/wiki/Security_through_obscurity](http://en.wikipedia.org/wiki/Security_through_obscurity)
[http://en.wikipedia.org/wiki/Security_by_design](http://en.wikipedia.org/wiki/Security_by_design)

Since Linux is open source, we only use the qualitative security by design. Closed source programs hide themselves behind obscurity and when a hole is discovered, they are far more vulnerable.

---

### Post by madjr on 2011-09-16
> **>hankim< said:**
> hello,

If I expose this doubt it's because I ignore much of how linux works so try not to scandalise but...

How secure is actually it? I feel like it's much more malleable than other OS, and so I also feel that for someone who knows how to work it, he could get through your sistem like the fish swim on water! I also know that the community looks after the common welth, but just in case someone would want to scan you or whatever he could find the way...

am I right?

i think this should answer your questions in a simple manner:
[http://www.pcworld.com/businesscenter/article/202452/why_linux_is_more_secure_than_windows.html](http://www.pcworld.com/businesscenter/article/202452/why_linux_is_more_secure_than_windows.html)

also linux provides **encryption** if you need that extra mile.

and remember that linux is the most used **server** OS for several good reasons.

---

### Post by &gt;hankim&lt; on 2011-09-16
convinced! I've probably seen too many movies of people hacking the central bank database or something hahaha
cheers!

---

### Post by haqking on 2011-09-16
Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

rootsudo **(must read)**
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

Remember that ports are closed by default on Linux and so a firewall does nothing unless you choose to install or start services that listen on them, and even then your home router will or should protect you anyways unless you forward to a given port on your machine.

Security is never a product, it is a process and the User is the number 1 security flaw, vigilence at all times and if you think you shouldnt do something or not sure if something sounds or looks right then dont do it ! and never authorise anything unless you know what it is !

Have fun

Regards

haqking

---

### Post by IWantFroyo on 2011-09-16
As long as you have a screen lock and a good password, your system is secure from the average nosy people. Once you encrypt the HDD and get a firewall up, it starts getting really secure.

For extra paranoia points, you can use Seahorse to encrypt individual files, too.

---

### Post by SavageWolf on 2011-09-16
I'm sure some arrogant jerk somewhere has a signature saying something about security...

---

### Post by IWantFroyo on 2011-09-16
> **SavageWolf said:**
> I'm sure some arrogant jerk somewhere has a signature saying something about security...

Careful mate. That applies to a lot of people. [-X

---

### Post by haqking on 2011-09-16
> **IWantFroyo said:**
> Careful mate. That applies to a lot of people. [-X


I almost jumped on it seeing as i have a security sticky link in mine, then i realised he was aiming it in humor at his own signature ;-)

---

### Post by IWantFroyo on 2011-09-16
> **haqking said:**
> I almost jumped on it seeing as i have a security sticky link in mine, then i realised he was aiming it in humor at his own signature ;-)

I thought the same thing. It sure looked like he was making a jab at you.

Well, anyways, back on topic.

There are a lot of things you can do to make Linux more secure, but you usually don't need to. The very fact that it isn't Windows renders all (known) viruses in the field useless.

---


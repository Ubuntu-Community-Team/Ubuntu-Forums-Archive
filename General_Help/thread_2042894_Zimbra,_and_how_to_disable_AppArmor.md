---
title: "Zimbra, and how to disable AppArmor?"
date: 2012-08-15
forum: General Help
---

### Post by feihong88 on 2012-08-15
Could AppArmor be the culprit?  Would I need to disable?

[http://www.zimbra.com/forums/installation/56367-my-notes-installing-zimbra-ose-ubuntu-server-10-04-lts.html]("http://www.zimbra.com/forums/installation/56367-my-notes-installing-zimbra-ose-ubuntu-server-10-04-lts.html")

I followed these instructions to the T on installing DNS on UBUNTU 10 Lucid Lynx.  However, when I get to step 18, and I have to restart bind9, the process fails to start.

I can't seem to find a solution, but need to get Zimbra running ASAP.  I have read that if I cannot my internal DNS mail servers from the UBUNTU box, I shouldn't install Zimbra…

Could AppArmor be the one that is blocking me from accomplishing this goal?

Thanks all,

Rich

---

### Post by oldos2er on 2012-08-15
Post moved to its own thread.

---

### Post by TheFu on 2012-08-15
> **feihong88 said:**
> Could AppArmor be the culprit?  Would I need to disable?

[http://www.zimbra.com/forums/installation/56367-my-notes-installing-zimbra-ose-ubuntu-server-10-04-lts.html](http://www.zimbra.com/forums/installation/56367-my-notes-installing-zimbra-ose-ubuntu-server-10-04-lts.html)

I followed these instructions to the T on installing DNS on UBUNTU 10 Lucid Lynx.  However, when I get to step 18, and I have to restart bind9, the process fails to start.

I can't seem to find a solution, but need to get Zimbra running ASAP.  I have read that if I cannot my internal DNS mail servers from the UBUNTU box, I shouldn't install Zimbra&#8230;

Could AppArmor be the one that is blocking me from accomplishing this goal?

Thanks all,

Rich
I am a long-time Zimbra admin, so I'm fairly certain you are only having DNS issues, not apparmor issues.  However, you can remove apparmor just by using 
```
apt-get purge apparmor
```If this is for home, just use a simple /etc/hosts file instead of a DNS for Zimbra. It is really picky about that during installation or upgrades.  It wants 2 lines and 1 FQDN in the file. Nothing more or install will fail.  Something like:
```

127.0.0.1       localhost
10.1.1.43    mail.domain.com
```Post install you can put 5 or 12,000 entries into the hosts file if you like, but at every update, you'll want to swap back to the 2 line hosts file.

The most important thing related to Zimbra is that your DNS MX records must be in-place before the installation and pointing towards this server. If you already have a email server running, just make the Zimbra one extremely low priority behind your current primary and secondary servers. When you get it running well, you can swap that single parameter and go live.  At home, I don't use an internal DNS for Zimbra - it isn't needed.  It isn't needed for a small network either.

For a large business, zimbra is complex enough that a consultant might be a good idea if you are in a hurry.

I won't review some complex installation how-to, sorry. That feels to much like "work" to me.  If you post exact error messages here, I might be able to figure them out.  

Did you post your question on the Zimbra forums?  They are pretty good over there too.

--Later edit --
I skimmed those directions - you are stuck on the storage setup, not zimbra.  Nothing about the storage is Zimbra specific.  Do you have the same storage setup that the how-to expects?  Same hardware, same partitioning, same amounts?

---


---
title: "Troubleshooting Question"
date: 2010-04-02
forum: General Help
---

### Post by arkestler on 2010-04-02
Hi,

I have a firewall/content filter set up with Squid/Dansguardian/Shorewall and the recent iTunes update to version 9.1 now does something weird in that any computer that is on the network can no longer access the iTunes store.  I am having a problem tracking down the problem.  I have check the access.log for squid and dansguardian, but it is not showing that anything was blocked from the client computer.  If I move the client computer to another network without the ubuntu box as the firewall everything works fine.  My question is, where else can I look other than the squid access.log, dansguardian access.log, system.log and message.log?

Thanks for any help!

Andrew

---

### Post by Sin@Sin-Sacrifice on 2010-04-02
It's probably itunes. You know how proprietary softare goes.

---

### Post by arkestler on 2010-04-02
I'm looking for real help in troubleshooting the firewall.

If I was looking for a response like that one I would have asked Apple.

---

### Post by Sin@Sin-Sacrifice on 2010-04-02
That's exactly what I was saying to do. Since an update of itunes it doesn't work and it worked before that??? Hmm... troubleshooting done?

---

### Post by arkestler on 2010-04-02
As I stated in the original post, if the client computer with iTunes installed is removed from the Firewall-ed network and put behind a regular old router, it works fine.

Therefore the problem is that the ubuntu setup is blocking it somehow.

If you are not going to offer any suggestions on how to troubleshoot traffic through the ubuntu box, then please stop wasting my time.

---

### Post by t4thfavor on 2010-04-02
Turn on max logging in shorewall, for the ip of the itunes box, and then read all 6 million pages of logs, to see what is being dropped. I bet they added some control interface or something where they need to connect into your pc from the outside, and you now have to forward the port.

---

### Post by arkestler on 2010-04-07
where and how would the drop be listed?  loc / fw / net ?

---


---
title: "being hitted by outsiders as stated by firestarter."
date: 2010-04-21
forum: General Help
---

### Post by neerajmourya on 2010-04-21
Hi, all
i m new to ubuntu, i have just installed firestarter, it is telling me i m being hitted.
i have attached an event log file. please help me what should i do?

---

### Post by mcduck on 2010-04-21
Nothing really, the very purpose of a firewall is to stop packages from outside, which it obviously is doing now.

That doesn't even mean that the packages would be anything dangerous to you, even if there was no firewall stopping them, as there would still have to be some service on your computer listening for incoming connections at those ports, and that service would have to be badly configured or in some other way vulnerable for the connection to be dangerous.

In other words, firewall log showing blocked connections is just a sign that the firewall is working, as long as you aren't getting large amounts of incoming connections from single source or anything like that.

---

### Post by 3rdalbum on 2010-04-21
> **neerajmourya said:**
> Hi, all
i m new to ubuntu, i have just installed firestarter, it is telling me i m being hitted.
i have attached an event log file. please help me what should i do?

Short answer: Do nothing.

Long answer: Everyone gets attempted incoming connections. You've already got a firewall and in addition you probably don't have anything listening on those ports anyway, so you're not at risk. The log entries that you see are completely "normal"; they are often virus-infected Windows PCs trying to scan for other vulnerable Windows PCs and this is to be expected in this day and age. Your firewall is blocking the connections.

Incidentally, this is why I don't approve of new users being told to install Firestarter - the logging capabilities of Firestarter are worrying to anyone who doesn't know much about firewalls and TCP/IP.

---

### Post by neerajmourya on 2010-04-21
Thanks a lot for your help.

---


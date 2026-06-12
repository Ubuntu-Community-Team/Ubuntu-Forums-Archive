---
title: "Adding hotmail &amp; yahoo chat accounts to thunderbird 15"
date: 2012-08-31
forum: General Help
---

### Post by hyfanious on 2012-08-31
Hi,
How can I register my Hotmail / Yahoo _**CHAT**_ accounts in Thunderbird 15?
Thanks in advance

---

### Post by Frogs Hair on 2012-08-31
A regular Hotmail account can be added like any other account from Edit > Account Settings > Account Actions. The chat Account option is also listed under Account Actions.

---

### Post by hyfanious on 2012-08-31
yeah but it has no option to select for hotmail / yahoo accounts!
all the available options is:
Facebook Chat
Google Talk
IRC
Twitter
XMPP

what should I do?

---

### Post by B Crowther on 2012-09-03
Yep, I agree with your frustration. Hotmail and Yahoo would be the obvious two to include, you would think.

---

### Post by Scabby_al on 2012-09-05
> **B Crowther said:**
> Yep, I agree with your frustration. Hotmail and Yahoo would be the obvious two to include, you would think.

It is possible to add providers for other chat protocols but none have been developed as of yet. I'm looking for Windows Live support myself.

---

### Post by hyfanious on 2012-09-14
any solution?!?

---

### Post by rndlusr on 2012-09-15
They're working on it:
> **[Instant Messaging]("https://wiki.mozilla.org/Features/Thunderbird/Instant_messaging_in_Thunderbird") **

 Preparing an add-on to leverage libpurple to support more chat  protocols (Yahoo, MSN, ICQ... are on the potential list of supported IM) 
-- [https://wiki.mozilla.org/Thunderbird/StatusMeetings/2012-08-28](https://wiki.mozilla.org/Thunderbird/StatusMeetings/2012-08-28)libpurple is the library Pidgin is built on. It supports all the major protocols. The confusing thing is that Instantbird, where Thunderbird's chat module comes from, just switched away from libpurple because of legal problems:> as Thunderbird can’t use libpurple which has an incompatible license, we  had to finish sooner, rather than later, some major architectural  changes to ensure that our chat back-end doesn’t depend on libpurple at  all. That’s right, Instantbird 1.2 is no longer based on libpurple (but  still uses it to support many protocols of course).
-- [http://blog.instantbird.org/2012/08/instantbird-1-2-released/](http://blog.instantbird.org/2012/08/instantbird-1-2-released/)So they reimplemented some protocols in Javascript but are still planning to support Yahoo and others via libpurple and a Thunderbird add-on. I don't know why the licensing problems wouldn't apply to an add-on as well.

---


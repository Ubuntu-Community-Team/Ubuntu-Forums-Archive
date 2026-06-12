---
title: "Firefox always starts in offline mode, internet is fine"
date: 2010-07-23
forum: General Help
---

### Post by bakegoodz on 2010-07-23
I don't have any connection issues, but Firefox always starts in offline mode. I can uncheck it and everything works fine. If I close and reopen it Firefox switches back to offline mode.

---

### Post by RabbitWho on 2010-07-23
Please open Firefox and type into address bar [about:config]("http://about%3Cb%3E%3C/b%3E:config")
if is the first time you are using [about:config]("http://about%3Cb%3E%3C/b%3E:config") on Firefox, a warning window come in front of you, please confirm the "promise".
 Then search ( type the parameter name into the "filter row" field ) for the Firefox config param named:
 network.online
 double click on the filtered row and set it to true
 Quit and restart Firefox
 There is also a knowed bug [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/191889](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/191889) about this issue.
 Hope this helps


source: 

[https://answers.launchpad.net/ubuntu/+faq/96](https://answers.launchpad.net/ubuntu/+faq/96)

---

### Post by lovinglinux on 2010-07-24
Try [https://addons.mozilla.org/en-US/firefox/addon/13233/](https://addons.mozilla.org/en-US/firefox/addon/13233/)

---

### Post by bakegoodz on 2010-07-25
Annoying little bug. That add-on keeps it from going into offline mode. Thanks!!!

---

### Post by lovinglinux on 2010-07-25
> **bakegoodz said:**
> Annoying little bug. That add-on keeps it from going into offline mode. Thanks!!!

You are welcome.

---


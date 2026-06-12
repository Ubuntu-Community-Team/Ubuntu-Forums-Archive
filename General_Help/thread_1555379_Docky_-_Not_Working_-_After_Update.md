---
title: "Docky - Not Working - After Update"
date: 2010-08-18
forum: General Help
---

### Post by HeatR216 on 2010-08-18
Today, Tuesday the 18th of August, 2010 I updated my Ubuntu 10.04 x86 laptop through the normal update manager in System>Administration>Update Manager. After doing so, Docky stopped working. I rebooted and now it wont even start. It will briefly show in System Monitor but never open. I also tried uninstalling it with "Ubuntu Software Center" as well as with Ubuntu Tweak; no change. Can someone please help or at least confirm that they have the same problem. Thanks

---

### Post by blitzxp on 2010-08-18
Yup, I'm having the same issue..I updated a few hours ago and just now restarted, to find my docky bar is missing... Is there any way to downgrade? I updated through this ppa::
[http://ppa.launchpad.net/docky-core/ppa/ubuntu](http://ppa.launchpad.net/docky-core/ppa/ubuntu)

edit:: There's version 2.0.5 through Synaptic which can be forced, but I'll just wait and hope not to lose my settings  :/

---

### Post by fuzzynoise84 on 2010-08-18
looks like it was a mistake from programmers, try to update now. I had the same issue.

---

### Post by blitzxp on 2010-08-18
> **fuzzynoise84 said:**
> looks like it was a mistake from programmers, try to update now. I had the same issue.

Confirmed, working OK now.. :)

---

### Post by mokoda on 2010-08-18
> **HeatR216 said:**
> Today, Tuesday the 18th of August, 2010 I updated my Ubuntu 10.04 x86 laptop through the normal update manager in System>Administration>Update Manager. After doing so, Docky stopped working. I rebooted and now it wont even start. It will briefly show in System Monitor but never open. I also tried uninstalling it with "Ubuntu Software Center" as well as with Ubuntu Tweak; no change. Can someone please help or at least confirm that they have the same problem. Thanks

I have the same problem!!:cry:

---

### Post by mokoda on 2010-08-18
> **HeatR216 said:**
> Today, Tuesday the 18th of August, 2010 I updated my Ubuntu 10.04 x86 laptop through the normal update manager in System>Administration>Update Manager. After doing so, Docky stopped working. I rebooted and now it wont even start. It will briefly show in System Monitor but never open. I also tried uninstalling it with "Ubuntu Software Center" as well as with Ubuntu Tweak; no change. Can someone please help or at least confirm that they have the same problem. Thanks

ran update again and all is well !! Thanks

---

### Post by beolandin on 2010-08-18
I have heard abouth update.
Is it possible to run update on a wubi-installation?

---

### Post by Chonnawonga on 2010-08-19
Mine's still not working, even after update. :(

---

### Post by HeatR216 on 2010-08-19
> **Chonnawonga said:**
> Mine's still not working, even after update. :(
Try running update again. It should work

---

### Post by Chonnawonga on 2010-08-19
Thanks for the advice. Turns out I needed to clear out some bad files. This helped:
```
rm -Rf ~/.local/share/docky
```

---


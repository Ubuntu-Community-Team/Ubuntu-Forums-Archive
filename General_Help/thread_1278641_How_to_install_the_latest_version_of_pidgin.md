---
title: "How to install the latest version of pidgin?"
date: 2009-09-29
forum: General Help
---

### Post by JigglyWiggly_ on 2009-09-29
So I am not a total idiot, but there are a few problems I go to this page [http://www.pidgin.im/download/ubuntu/](http://www.pidgin.im/download/ubuntu/)
Which in itself works however this line
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
```

Does not do anything, as in the keyserver.ubuntu.com times out... Is there a .deb file for this?

---

### Post by thoriumchameleon on 2009-09-29
Have you tried using Add/Remove Programs? Pidgin should be included there. At least I know it is in 8.04 or higher...

---

### Post by XDevHald on 2009-09-29
Easier to grab it from the repo list **apt-get install pidgen** as both website and synaptic run the updated 2.6.2 for this software. Also the server may be handling a heavy traffic flow, give it some time.

Hope this helps.

---

### Post by JigglyWiggly_ on 2009-09-29
When I open it, it shows an outdated 1.2x version

---

### Post by jmszr on 2009-09-29
JigglyWiggly,

You can install the .deb from here: [http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

Edit: Make sure and uninstall the one you have now first.

---

### Post by XDevHald on 2009-09-29
> **JigglyWiggly_ said:**
> When I open it, it shows an outdated 1.2x version

This can't be from synaptic as it's updated through the repositories from the pidgen devs. 

Here's the mirror source: [http://archive.getdeb.net/getdeb/ubuntu/jaunty/pi/](http://archive.getdeb.net/getdeb/ubuntu/jaunty/pi/)

---

### Post by JigglyWiggly_ on 2009-09-29
Eh, when I go there and download pidgin-dbg_2.6.2-1~getdeb1_amd64.deb, the package installer loads but says
```

Error: dependency is not satisfiable: pidgin (=1:2.6.2-1~getdeb1)|finch (=1:2.6.2-1~getdeb1)| libpurple0 (=1:2.6.2-1~getdeb1)

```
I have no idea what that means :? (I am on jaunty 64)

Oh wait I just looked at the synaptic package manager and it shows 1:2.5.5-1ubuntu, but I still want the newest 2.6.x version

---

### Post by JigglyWiggly_ on 2009-09-29
Ehhh when I even try to install pidgen in synaptic(or terminal) I get this:

The following packages have unresolvable dependencies. Make sure that all requried repsitories are added and enabled in the preferences.
```

Depends: pidgin-data (<1:2.5.5-zz) but 1:2.6.1-1ubuntu~pidgin1.904 is to be installed.
```

Wait nevermind I got it, I just removed it from the software sources and I went into synaptic and installed the latest version of Pidgin.

Cheers.

---

### Post by XDevHald on 2009-09-29
Glad to see it was resolved. 

**TOPIC CLOSED**

---

### Post by korin43 on 2009-09-29
You can install Pidgin from the developers PPA without adding the key, it'll just complain.

---


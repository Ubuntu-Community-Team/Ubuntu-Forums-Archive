---
title: "Firestarter"
date: 2004-10-20
forum: General Help
---

### Post by Burgundavia on 2004-10-20
I recently installed Firestarter on the RC. However, the default is to run under the root user, which of course is disabled. I am stumped on how sudo this application from a graphical prompt. 

Burgundavia

---

### Post by cybrjackle on 2004-10-20
Applications -&gt; System Tools -&gt; "right click" on Firestarter Firewall Tool and choose "Properties" in the "Command:" change "gksu" to "gksudo", so it will look like this:

```

gksudo /usr/sbin/firestarter

```

---

### Post by Burgundavia on 2004-10-20
Thanks for the quick response. I had figured there would be a program like that, but I am still getting used to the sudo idea.

Burgundavia

---

### Post by cybrjackle on 2004-10-20
no problem

---

### Post by HungSquirrel on 2004-10-20
[quote=Burgundavia]Thanks for the quick response. I had figured there would be a program like that, but I am still getting used to the sudo idea.[/quote]
If you fear change like I do, you can set your root password with *sudo passwd root* and use su like other distros.

---

### Post by Burgundavia on 2004-10-20
I have never feared change, and thanks for the info. I have just upgraded from RH8.0, so I am a little behind on some of these "new fangled apps"

Burgundavia

---

### Post by usultis on 2007-08-10
Hi I've added a screencast [http://wikisos.org/wiki/Ubuntu_7.04:How_to_setup_Internet_connection_sharing](http://wikisos.org/wiki/Ubuntu_7.04:How_to_setup_Internet_connection_sharing) that shows how to install firestarter and enable Internet connection sharing

---


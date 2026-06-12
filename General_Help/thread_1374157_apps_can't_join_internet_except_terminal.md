---
title: "apps can't join internet except terminal"
date: 2010-01-06
forum: General Help
---

### Post by inf-h4x0r on 2010-01-06
Hi

I'm using a pppoe internet connection, when enter connection manually everything works fine but when connect automatically on startup (put script in ect/init.d/) the connection is ok and works, but applications can't join internet like firefox, chrome,... . only terminal and lynx browser can use internet! ping responds are OK

poor english, sorry

---

### Post by inf-h4x0r on 2010-01-06
who can resolve this?

---

### Post by beany1 on 2010-01-06
just a suggestion, is it something to do with your privileges? like is the script running at startup as root so only sudo can use internet? or something? does the script let you connect manually and use internet normally when you open it?

---

### Post by inf-h4x0r on 2010-01-06
nothing, running programs as root has no difference with normal access. in both can't use internet.
yes, when run script manually (after poff -a) works fine and apps can use internet.

---

### Post by inf-h4x0r on 2010-01-07
anybody there?

---

### Post by inf-h4x0r on 2010-01-08
does no one have an idea?

---

### Post by inf-h4x0r on 2010-01-09
:-"

---

### Post by beany1 on 2010-01-21
hi, erm, you could try putting the script in /usr/bin and use Startup Applications in system/preferences to add it to startup? thats what id try next!

---

### Post by inf-h4x0r on 2010-01-28
> **beany1 said:**
> hi, erm, you could try putting the script in /usr/bin and use Startup Applications in system/preferences to add it to startup? thats what id try next!
I try this method but no result

---


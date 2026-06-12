---
title: "mono &amp; nant problem"
date: 2011-03-11
forum: General Help
---

### Post by jarredverne on 2011-03-11
Hi, I have caused myself a problem on my Ubuntu 10.04

*I have first installed mono + nant by using apt-get
*uninstalled nant-0.85
*downloaded source from nant website and manually installed it
* now mono command works, but nant says: "exec: 2: /usr/local/bin/mono: not found"

I can run mono applications normally by "mono" command, but I can not use nant now, I think there is a problem with the path,
but I could not find any solution to correct the path

(btw, I've tried to reinstall nant by using apt-get, not working)

when I do:

$which mono

I get the answer:

/usr/bin/mono


I hope you can help me, thanks
Jarred

---

### Post by directhex on 2011-03-11
The problem is with your hand-built nant, due to a nant bug which assumes frameworkAssemblyDirectory and prefix is the same for nant and the installed Mono framework.

You'll need to hack on NAnt.exe.config to add some .. where needed.

---


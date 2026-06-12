---
title: "iptables --connlimit module"
date: 2006-02-02
forum: General Help
---

### Post by ReMuSoMeGa on 2006-02-02
Sorry, not sure if this is the correct place to post this.

Does anyone know where I can get iptables "connlimit" module?
I have iptables installed on my server, i just need connlimit. Thanks in advance.

---

### Post by heimo on 2006-02-03
I can only give some links and general instructions:
[http://www.netfilter.org/documentation/HOWTO//netfilter-extensions-HOWTO-2.html#ss2.1](http://www.netfilter.org/documentation/HOWTO//netfilter-extensions-HOWTO-2.html#ss2.1)
[http://www.netfilter.org/downloads.html#svn](http://www.netfilter.org/downloads.html#svn)

AFAIK, connlimit is not part of Linux (yet?), so you need to patch and compile. Install subversion (sudo apt-get install subversion), make sure you have kernel sources in /usr/src/, check out iptables sources and patch-o-matic, patch kernel using patch-o-matic, compile.

---


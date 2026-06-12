---
title: "Synaptic not finishing installation"
date: 2006-02-06
forum: General Help
---

### Post by MLesniak on 2006-02-06
Hello,

when I install a packet using synaptic I just does not finish installation. An example should clarify this. I'm installing libnet-irc-ruby (but the problem occurs with other packages, too). On the synaptic terminal is a message like (translated from german, so maybe not exactly...)
```
Unpacking libnet-irc-ruby (aus .../libnet-irc-ruby_0.14-4_all.deb) ...
Configuring libnet-irc-ruby (0.14-4) ...
```
On the terminal I've started synaptic's from I can read
```
no statusfd changes/content updates in terminal for 60seconds
no statusfd changes/content updates in terminal for 60seconds
no statusfd changes/content updates in terminal for 60seconds
no statusfd changes/content updates in terminal for 60seconds
no statusfd changes/content updates in terminal for 60seconds
...
```

I have no glue where the problem can be.

Thanks for any help,
  Michael

---

### Post by MLesniak on 2006-02-06
Ciao,

just in case someone has the same problem. I used the *fish*-Shell and when started from it, synaptic freezes directly after configuring packages. 

Starting bash before making a *sudo synaptic* solves this problem.

  M.

---


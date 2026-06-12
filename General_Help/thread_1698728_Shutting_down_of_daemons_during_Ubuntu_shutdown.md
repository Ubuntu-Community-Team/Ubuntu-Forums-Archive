---
title: "Shutting down of daemons during Ubuntu shutdown"
date: 2011-03-02
forum: General Help
---

### Post by Tronman on 2011-03-02
Hello,

I'm interested in finding out, specifically, what causes daemon's to be shutdown when I shutdown Ubuntu?

I'm use Ubuntu which is why I'm posting here, but I suppose this knowledge could apply to other Disto's too.

Perhaps I'm better off to explain with an example:

I wrote a C++ that queries a Mysql database. I want it to run every time the computer is shutdown.

I've verified the program works fine, and I've verified that I can run a program on shutdown of the computer by putting it in /etc/rc0.d

The problem is that by the time rc0.d runs my program, mysql has already been shutoff, and it can't connect.

So what I'm wondering is, is there a script or something at a higher level that goes around turning things like daemons as the System shutdowns, but before any of the scripts in rc0.d are run? (It doesn't look like anything in here is shutting down mysql). Something that actually calls mysql shutdown?

If so, I'm hoping someone could point me to it and I can add my program to be run before mysql shuts down.

Otherwise, I might end up having to get the source code compile by own /sbin/shutdown and tweak it from there. Granted I might end up doing this anyway because there's more stuff I want to customize during shutdown (e.g. abort it under certain conditions), but I'm hoping not to go that far just yet.

Any suggestions, please let me know. Thanks!

---


---
title: "Strange srcds freeze"
date: 2011-01-24
forum: General Help
---

### Post by kossolax on 2011-01-24
Hello,

I've recently changed my root server for a new one, with new hardware, supposed to be more performant. This said, I've some problems of freeze on my srcds install (css).
I moved every file, expect apache, php, sendmail conf for a fresh install (I was using lampp, now, I'm using apt-get install.) My old server was in 32bits, my new one in 64bits. 
I was using Ubuntu 8.04 with a nx-server running with a gnome desktop to lunch game server. I never had lag, or problem with it.
Now, I'm using Ubuntu 10.04 with a x2go-server running with a gnome desktop...

Well, about the freeze, I've no idea where they can come, but I've done some test:
- Disabled apache during a CSS-match, no freeze
- Enabled after 25min of a CSS-match, a freeze of 2-3seconds occurred.
- Disabled. No more freeze.

[IMG]http://img6.imageshack.us/img6/5404/netgraphs.jpg[/IMG]


Here is my apache/mysql/php config: [http://www.kossolax.be/conf/](http://www.kossolax.be/conf/)

Another side is, my mail server. I don't know if it's linked. But it can send mail to outgoing email. But it cannot distribute it to local user.


This said, I after search, on some map with trigger_push, the server have some freeze with x2go session suspended, but not if it's running.
(DataTable warning: player: Out-of-range value (2000.000000) in SendPropFloat 'm_vecBaseVelocity', clamping.)

since, I really help, and really need to fix this as fast as possible. _I'm offering 50$ Paypal_, to the one who'll find me how to fix.

Thank you for reading.

---


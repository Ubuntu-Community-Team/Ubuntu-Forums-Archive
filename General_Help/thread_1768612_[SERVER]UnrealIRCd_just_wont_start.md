---
title: "[SERVER]UnrealIRCd just wont start?"
date: 2011-05-27
forum: General Help
---

### Post by Jragon on 2011-05-27
Hi!

For some odd reason each time I try to start UnrealIRCd nothing happens... Apart from:

root@jragonserver:/home/ircd/Unreal3.2# ./unreal start
Starting UnrealIRCd
 _   _                      _ ___________  _____     _
| | | |                    | |_   _| ___ \/  __ \   | |
| | | |_ __  _ __ ___  __ _| | | | | |_/ /| /  \/ __| |
| | | | '_ \| '__/ _ \/ _` | | | | |    / | |    / _` |
| |_| | | | | | |  __/ (_| | |_| |_| |\ \ | \__/\ (_| |
 \___/|_| |_|_|  \___|\__,_|_|\___/\_| \_| \____/\__,_|
                           v3.2.8.1
                     using TRE 0.7.5 (LGPL)

* Loading IRCd configuration ..
[warning] unrealircd.conf:255: listen with SSL flag enabled on a non SSL compile
[error] unrealircd.conf:322: link hub.mynet.com with SSL option enabled on a non-SSL compile
[error] unrealircd.conf:322: link hub.mynet.com with ZIP option enabled on a non-ZIP compile
[error] unrealircd.conf:538: tld::motd: ircd.motd.fr: No such file or directory
[error] unrealircd.conf:539: tld::rules: ircd.rules.fr: No such file or directory
[error] unrealircd.conf:738: set::kline-address must be an e-mail or an URL
[error] 5 errors encountered
[error] IRCd configuration failed to pass testing
Possible error encountered (IRCd seemingly not started)
=====================================================
Check above for possible errors, and this output of
ircd.log. If you cannot solve the problem, read
Unreal.nfo on where to get support
=====================================================
d
root@jragonserver:/home/ircd/Unreal3.2#

If you could help, that would be awesome

Thanks

Jragon/

---

### Post by Jragon on 2011-05-27
Anyone?

---


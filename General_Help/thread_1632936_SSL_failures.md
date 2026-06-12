---
title: "SSL failures"
date: 2010-11-28
forum: General Help
---

### Post by Emmental on 2010-11-28
I'm having an ongoing problem with SSL occasionally ceasing to function on Ubuntu 10.04 64bit. This has been happening intermittently for about 2 months. I posted previously thinking this was a Privoxy problem, but after more investigation it seems to be related to SSL.

When this failure occurs it causes the folllowing:

- Cannot make any connections to services using SSL. This is not just limited to web sites.
- Cannot connect to a web proxy server running on the same machine.
- Other machines on the network cannot connect to the web proxy server running on the machine in question

However, existing SSL connections still function, for example a connection to an IRC server over SSL still works, but no new connection can be made. In other words, SSL seems to be dead for new connections, both incoming and outgoing.

I have strong suspicions that these failures are cause by Update Manager, though I don't know why this would be. The failures always happen at the time Update Manager runs. Today when it failed I checked the connection as Update Manager was working and the connection was still OK, but as soon as Update Manager finished the update SSL stopped functioning.

The frequency of the failures is intermittent. Sometimes it will go for a week or two with no failure, and sometimes it will fail several days in a row.

The only way I have found to get SSL working again is a reboot.

Does anyone have any ideas as to what the problem might be?

Thanks.

---


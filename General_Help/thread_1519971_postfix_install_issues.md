---
title: "postfix install issues"
date: 2010-06-28
forum: General Help
---

### Post by VRage on 2010-06-28
Hi I'm rather new to linux and am experiencing issues while trying to follow the postfix guide at: [http://wiki.mediatemple.net/w/Installin](http://wiki.mediatemple.net/w/Installin) … buntu_9.10

Towards the end under "Configuring Courier", when I test the TLS and SMTP-AUTH, after inputting "telnet localhost 25" in the terminal, half the time I immediatly get  the message:

"Connection closed by foreign host."

while the other half of the tries, I get to write the "ehlo localhost" command which doesn't seem to do anything and seconds later I get the same "Connection closed by foreign host."

So the full output is:
Trying 127.0.0.1...
Connected to localhost.localdomain.
Escape character is '^]'.
ehlo localhost
Connection closed by foreign host.


I'm a bit lost here... any ideas on what could be wrong? Or a good place to start troubleshooting?

Thanks in advance for your time.

---


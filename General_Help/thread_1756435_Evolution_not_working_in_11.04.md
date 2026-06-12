---
title: "Evolution not working in 11.04"
date: 2011-05-12
forum: General Help
---

### Post by SimonFr on 2011-05-12
I upgraded to 11.04 this morning, and since then Evolution has failed to connect to my IMAP server. I've tried resetting the configuration and starting from fresh, and it still fails.  Watching what it's doing with tcptrack, it seems to open a connection to the HTTP proxy - and nothing else. It's not configured with an HTTP Proxy, although the underlying system knows about it. 

How can I get Evolution to talk IMAP to an IMAP server, and not use the HTTP Proxy to do so?

Additional: I'm still unsure why it's using the HTTP Proxy, but using strace on Evolution shows that it's ignoring the imap server it's been told about, and is attempting to connect to localhost instead (this didn't show up on tcptrack because I was watching eth0). /etc/hosts and /etc/resolv.conf are correct.

---

### Post by SimonFr on 2011-05-13
> **SimonFr said:**
> 
Additional: I'm still unsure why it's using the HTTP Proxy, but using strace on Evolution shows that it's ignoring the imap server it's been told about, and is attempting to connect to localhost instead (this didn't show up on tcptrack because I was watching eth0). /etc/hosts and /etc/resolv.conf are correct.

Evolution appears to have been trying to use a socks proxy, because 'use the same proxy for all protocols' had been set in System->Preferences->Network Proxy. Different behaviour from Maverick, where it didn't obey this directive.

---


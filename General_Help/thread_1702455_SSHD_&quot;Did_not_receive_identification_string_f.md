---
title: "SSHD: &quot;Did not receive identification string from [ip]&quot; and ISA proxy server"
date: 2011-03-07
forum: General Help
---

### Post by LLMNSTR on 2011-03-07
Hi,

I'm having a small problem with OpenSSH. At work, I am behind a Microsoft ISA proxy server which is filtering some websites. To circumvent this, I am using PuTTY + NTLMaps (for authentication with the proxy server) to try to connect to my OpenSSH server at my home.

I have configured OpenSSH to use port 443, as the ISA server only allows encrypted traffic over port 443. I can connect to the OpenSSH server through the internet, using NTLMaps (even though it's not necessary, I still pipe it through to make sure there's no problem there) perfectly fine. I can even do it using a friend's proxy server. But when I try to connect through the ISA proxy server at work, I get the error "Did not receive identification string from [ip]" in my /var/log/auth.log.

NTLMaps logs show that the ISA proxy is successfully authenticated to, and that a connection is successfully established, and then closed seconds later once I get the "server unexpectedly closed network connection" error from PuTTY. Basically, it looks like the ISA server is doing something funny.

Any thoughts?

---


---
title: "Can't login to Empathy via Facebook"
date: 2012-06-30
forum: General Help
---

### Post by Baldrick_NZ on 2012-06-30
Hi all,

All was well last night, but now I can't login to FB chat using Empathy. I've tried re-applying my user name and password, and purging and re-installing Empathy, but still no joy.

Can anyone please help sort this out?

Kind regards.

---

### Post by xanhellx on 2012-06-30
-I'm having the same issue and tried the same. Any other  suggestion guys?

---

### Post by UUser123 on 2012-08-01
Did either of you manage to get it working? I'm having the same problem.


Details:
~  I installed Ubuntu 12.04  32 bit a week ago. (I have windows 7 on another partition)

~  I added Windows Live account information to empathy - No problems, works every time.

~  I added Facebook Chat to empathy - Constantly getting network error;  Failed to connect every time.

~  Tried reinstalling empathy - No change.

~  Added a rule on my routers firewall to allow outward traffic from  port 5222 - No longer get network error however now it just keeps trying  to connect.

~  Checked the debug logs and it gets to this point:

_end_element_ns: Received stanza
* features xmlns='http://etherx.jabber.org/streams'
    * starttls xmlns='urn:ietf:params:xml:ns:xmpp-tls'
    * mechanisms xmlns='urn:ietf:params:xml:ns:xmpp-sasl'
        * mechanism
            "X-FACEBOOK-PLATFORM"
        * mechanism
            "DIGEST-MD5"
_write_node_tree: Serializing tree:
* starttls xmlns='urn:ietf:params:xml:ns:xmpp-tls'
_end_element_ns: Received stanza
* proceed xmlns='urn:ietf:params:xml:ns:xmpp-tls'

I'm guessing it's failing to proceed for some reason?

~  I switched Facebook Chat for Jabber with my Facebook details so that I could get the advanced settings.

~ Tried using port 443 (With a firewall rule allowing outward traffic)  with old-ssl - Back to Network error. Debug seems to suggest it all goes  wrong with an error for the ssl handshake, an unexpected packet, I  think.


So that is about as far as I've gotten. I really don't know what to try next so any advice would be appreciated.

Thanks.

---


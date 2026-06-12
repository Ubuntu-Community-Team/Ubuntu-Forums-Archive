---
title: "Pidgin 2.10.3 on Ubuntu 12.04 - Gmail Talk (XMPP)"
date: 2012-07-16
forum: General Help
---

### Post by ernz on 2012-07-16
Version 2.10.3 of Pidgin gets a bit upset about default gmail settings in Ubuntu 12.04. Here are the settings which I finally found to work without causing a connection failure. Under the account settings:

**_BASIC TAB_**

**Protocol:** XMPP
**Username: **ernz (without the @domain.com part)
**Domain: **gmail.com
**Resource: **<BLANK>
**Password:** <YOUR PASSWORD> (If using 2-step authentication, you'll need the application specific password from Google > Account > Security > Authorising applications)
**Remember Password:** Yes
**Local Alias:** <YOUR NAME>

_**ADVANCED TAB**_

**Connection Security: ** Require encryption
**Allow plaintext auth...:** No
**Connect port:** 5222
**Connect server:** talk.google.com
**File transfer proxies:** proxy.eu.jabber.org (Or default)
**BOSH URL:** <BLANK>

**_PROXY TAB_**

**Proxy Type:**Use GNOME Proxy Setting

**_VOICE AND VIDEO TAB_**

**Use silence suppression:** No

I hope this helps anyone experiencing the same connection problems as I did. There are lots of conflicting how-tos out there to fix this but this is the resolution for there versions. It would be really nice if this worked out of the box with Google Talk default configuration settings.

- ernz

---

### Post by northcamel on 2012-10-04
help me much, thank you very much!:guitar:

---

### Post by Datalocust on 2012-10-24
I found the problem I was having was also similar...

Remove the @ symbol from before gmail.com for the DOMAIN and add talk.google.com as the Connect Server.

~Datalocust

---

### Post by kayncz on 2012-10-28
I have problem with IPv6. I'm using IPv6 tunnel by [http://www.sixxs.net/](http://www.sixxs.net/). So turn off this tunnel problem solved. For me:

```
sudo aiccu stop
```

---

### Post by farimah on 2013-02-14
If it does not solve my problem(same as mention) what I can do to understand where I have problems?



edit: my problem solved! I have some problems with my net service! :)

---


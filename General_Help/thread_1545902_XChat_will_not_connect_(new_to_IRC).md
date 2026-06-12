---
title: "XChat will not connect (new to IRC)"
date: 2010-08-04
forum: General Help
---

### Post by jrcantwell85 on 2010-08-04
I'm new to IRC and after some research I decided to go with XChat. Problem is I'm trying to connect to irc.mozilla.org using port 6667. The mozilla IP is 65.245.208.156 which it is trying to use. I only receive a "connection timed out" error. I'm also new to Ubuntu switching from Windows and I'm pretty sure there is no anti-virus or firewall installed. I've done several searches on Google and nothing has helped. Any suggestions?

---

### Post by jrcantwell85 on 2010-08-04
I guess no one has a clue...?

---

### Post by Hanzerik on 2010-08-04
irc.mozilla.org did not work for me...timed out. Maybe the irc server is down. As far as firewalls/antivirus goes, I would say most Linux folks don't use them foe everyday use. If you run an Email server then yes I would st up some type of virus/spam checking, but to not protect your server, but to help stop viruses/spam from leaving your server to remote email recipients. I don't use IPTables on my machines since they are already behind a hardware firewall.

---

### Post by jrcantwell85 on 2010-08-04
I just checked to see if I could connect to another IRC server and I can connect to the Ubuntu servers just fine. Here are my setting for Mozilla:

Server: irc.mozilla.org/6667
Using global user information
Character Set: UTF-8

All other fields have been left blank.

---

### Post by howefield on 2010-08-04
> **jrcantwell85 said:**
> Server: irc.mozilla.org/6667
Using global user information
Character Set: UTF-8

All other fields have been left blank.

Try simply putting in irc.mozilla.org for the server field and for character set use IRC (Latin/Unicode Hybrid)

---

### Post by jrcantwell85 on 2010-08-04
I've done both of those things and it still will not connect. Thanks for the suggestions. This is a quote from Mozilla's IRC site:

[SIZE=2]"All channels use the UTF-8 character set unless otherwise specified in [brackets]"

That is why I changed to that character set, but still to no avail.
[/SIZE]

---

### Post by jrcantwell85 on 2010-08-04
Would Mozilla's port scanning have something to do with it?

> When you connect to our IRC server, you will get portscanned from 63.245.208.159, 63.245.212.23, or 63.245.216.214.  This is       an unfortunate but necessary step in order to cut down on the number of viruses and other       malicious users attempting to communicate via our IRC servers.  The portscan is checking       for common ports used by known viruses and open proxy servers to ensure that your machine       is not infected before allowing you to remain connected.  By connecting to our IRC servers,       you agree to have your computer portscanned by our server.  If you don't like this, don't connect.

---

### Post by jrcantwell85 on 2010-08-04
The issue has been resolved. Future note:

If you are connecting to irc.mozilla.org use a secure connection (SSL) on port 6697.

---


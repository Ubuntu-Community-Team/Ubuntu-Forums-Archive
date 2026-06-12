---
title: "Software for https -&gt; http translation"
date: 2009-10-26
forum: General Help
---

### Post by Krislarsen on 2009-10-26
I am looking for some software that can do https -> http translation.

The scenario:

Client --http--> Internet --http--> Firewall/router --http--> Network camera
The network camera is http only, and I want to avoid plain text authentication over Internet.


I want to do this:

Client --https--> Internet --https--> Firewall/router --https--> https-to-http-server --http--> Webcamera

or:

Client --https--> Internet --https--> https-to-http --http--> Firewall/router --http--> Webcamera

What kind of server software is suitable for the https-to-http translation?

---

### Post by ScarySquirrel on 2010-04-23
[Mezcal HTTP/S]("http://backtrack.offensive-security.com/index.php/Tools")
Check it out on [bt4]("http://www.backtrack-linux.org/").

---


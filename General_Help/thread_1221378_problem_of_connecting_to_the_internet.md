---
title: "problem of connecting to the internet"
date: 2009-07-23
forum: General Help
---

### Post by abhi90 on 2009-07-23
hello friends!
Actually I tried to connect to the internet but I cant.
When I start my modem, first it will **check**, then I see the **autoeh0** is connected.
It shows 100mbps speed but when I start **Mozilla firefox **then the whatever site I want to see doent open...

**Can anyone give me the manual setting to connect to the internet that requires _username_ and _password_.** I have a broadband connection.(**ADSL**)

---

### Post by quixote on 2009-07-24
Do you have a wired or wireless connection?  eth0 (wired) doesn't usually require username and password, at least on a home network.

There's an excellent thread about manually connecting wireless interfaces by [wiemann01]("http://ubuntuforums.org/showthread.php?t=318539").

---

### Post by wojox on 2009-07-24
Open Terminal:

```
sudo pppoeconf
```

---


---
title: "Connection Problem in Vidalia  &amp; Tor"
date: 2010-01-14
forum: General Help
---

### Post by Richiegs on 2010-01-14
Every time I run Tor using Vidalia, it fails to work by saying   p, li { white-space: pre-wrap; }  "Vidalia was unable to authenticate to the Tor software. (Control socket is not connected.)
 Please check your control port authentication settings." 

The control port is set to 127.0.0.1 : 9050.
How do I fix it?
Which port can I use besides 9050?


Please help



Thank you in advance.


Richie

---

### Post by familiarmoniker on 2011-06-26
hi Richiegs,
I know I'm responding a bit late, but if this didn't come in time to help you maybe it will help another person. What you want to do is go to the terminal and type:
```
sudo /etc/init.d/tor restart
```
and you should get an output that looks something like this:
```
Jun 25 12:55:05.274 [notice] Opening Socks listener on 127.0.0.1:9050
Jun 25 12:55:05.274 [notice] Opening Control listener on 127.0.0.1:9051
done.
```
You want to use the latter of these two numbers (in this case 9051).
Hope this helps!:)

---

### Post by miko5054 on 2011-06-26
i had the same problem 
i solved it by edit the tor config file

on terminal
```
sudo gedit  /etc/tor/torrc

```

than edit port 9050 TO 9051
and on vidalia setting as well TO 9051

miki

---


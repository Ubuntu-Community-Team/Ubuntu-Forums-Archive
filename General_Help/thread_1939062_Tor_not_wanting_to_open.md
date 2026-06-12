---
title: "Tor not wanting to open"
date: 2012-03-10
forum: General Help
---

### Post by joelstitch on 2012-03-10
When I open Vidalia I get this error:

```
Vidalia detected that the Tor software exited unexpectedly.
 Please check the message log for recent warning or error messages.

```And this is what the log says:

```
Mar 10 20:23:33.142 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Mar 10 20:23:33.142 [Warning] Permissions on directory /var/run/tor are too permissive.
Mar 10 20:23:33.143 [Warning] Before Tor can create a control socket in "/var/run/tor/control", the directory "/var/run/tor" needs to exist, and to be accessible only by the user account that is running Tor.  (On some Unix systems, anybody who can list a socket can conect to it, so Tor is being careful.)
Mar 10 20:23:33.143 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Mar 10 20:23:33.143 [Error] Reading config failed--see warnings above.
```

---

### Post by 2F4U on 2012-03-11
There are a couple of similar posts here on the forum which you might want to check:

[http://ubuntuforums.org/showthread.php?t=1849649](http://ubuntuforums.org/showthread.php?t=1849649)
[http://ubuntuforums.org/showthread.php?t=1255475](http://ubuntuforums.org/showthread.php?t=1255475)
[http://ubuntuforums.org/showthread.php?t=1242868](http://ubuntuforums.org/showthread.php?t=1242868)
[https://answers.launchpad.net/ubuntu/+source/tor/+question/94995](https://answers.launchpad.net/ubuntu/+source/tor/+question/94995)

---

### Post by joelstitch on 2012-03-11
I changed the porton Vidalia from 9050 to 9051 and now I get this:

```
Mar 11 09:09:27.096 [Notice] We now have enough directory information to build circuits.
Mar 11 09:09:27.097 [Notice] Bootstrapped 80%: Connecting to the Tor network.
Mar 11 09:09:28.407 [Notice] Bootstrapped 85%: Finishing handshake with first hop.
Mar 11 09:09:36.447 [Notice] Bootstrapped 90%: Establishing a Tor circuit.
Mar 11 09:09:38.356 [Notice] Tor has successfully opened a circuit. Looks like client functionality is working.
Mar 11 09:09:38.360 [Notice] Bootstrapped 100%: Done.
Mar 11 09:09:50.010 [Notice] New control connection opened.
Mar 11 09:09:50.229 [Notice] New control connection opened.
```

---

### Post by 2F4U on 2012-03-11
You don't say whether it is working or not. From the log file snippet I would guess that it works. If it works, it would be nice if you could mark the thread as solved.

---

### Post by joelstitch on 2012-03-11
I uninstalled everything (tor, Vidalia and polipo) and then reinstall them and fixed the port that Vidalia was using (it was using port 9050 and tor was using 9051).And that did the trick.

---

### Post by joelstitch on 2012-03-12
I'm still having the issue. Now when I click on Start Tor I get this:

 p, li { white-space: pre-wrap; }```
Mar 12 15:13:59.076 [Notice] Tor v0.2.2.35 (git-73ff13ab3cc9570d). This is experimental software. Do not rely on it for strong anonymity. (Running on Linux i686)
Mar 12 15:13:59.077 [Notice] Initialized libevent version 1.4.13-stable using method epoll. Good.
Mar 12 15:13:59.077 [Notice] Opening Socks listener on 127.0.0.1:9050
Mar 12 15:13:59.077 [Warning] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Mar 12 15:13:59.077 [Notice] Opening Control listener on 127.0.0.1:9051
Mar 12 15:13:59.077 [Notice] Closing partially-constructed listener Control listener on 127.0.0.1:9051
Mar 12 15:13:59.078 [Warning] Failed to parse/validate config: Failed to bind one of the listener ports.
Mar 12 15:13:59.078 [Error] Reading config failed--see warnings above.
```

I have it setup to use port 9051.

---

### Post by joelstitch on 2012-03-12
> **fshepherd said:**
> I recommend 'IT' another epic read and very good. And it helps to have read 'IT' although not essential by several means if you plan to look over article because there's a lovely tie in. 
 
[cancer sign]("http://www.dnjtw.com")

What!?

---

### Post by ottosykora on 2012-03-12
> **joelstitch said:**
> I uninstalled everything (tor, Vidalia and polipo) and then reinstall them and fixed the port that Vidalia was using (it was using port 9050 and tor was using 9051).And that did the trick.

In case of TOR, do please an exception and do not take the versions from the normal repository.
Go to torproject.org, get tor from there and follow closely the instruction given there.

***You do not need polipo or privoxy, tor does all the work*** and may use socks as well.

Note: if you install the tor from the ppa of torproject.org, then it is setup to run at startup, so may not be able to control it by vidalia any more then. In such case you do not need vidalia too.

You need Torbutton for firefox and remove all addons from it.

You can change it however and then install and use vidalia to start, stop , configure it.

Best however, use the tor bundle browser, as it is getting more and more difficult to make the standard firefox browser to be secure enough for use with tor.
Using standard set firefox makes the use of tor a joke, tor simply not needed then.

---


---
title: "Deb repository 'us.archive.ubuntu.com' is off line."
date: 2012-08-21
forum: General Help
---

### Post by bartonski on 2012-08-21
I tried to do an apt-get update on my lucid box, and go the following message, among others:

```

Err http://us.archive.ubuntu.com lucid Release.gpg                                                             
  Could not connect to us.archive.ubuntu.com:80 (91.189.91.30). - connect (113: No route to host) [IP: 91.189.91.30 80]

```

The host is ping-able, but I can't reach it via http or https.

```
$ ping us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.91.29) 56(84) bytes of data.
64 bytes from likho.canonical.com (91.189.91.29): icmp_seq=1 ttl=44 time=56.3 ms
64 bytes from likho.canonical.com (91.189.91.29): icmp_seq=2 ttl=44 time=58.3 ms
64 bytes from likho.canonical.com (91.189.91.29): icmp_seq=3 ttl=44 time=62.7 ms
64 bytes from likho.canonical.com (91.189.91.29): icmp_seq=4 ttl=44 time=56.3 ms
```

Pretty much everything in my sources.list points to this host. Is there a different server that I can/should point to?

---

### Post by SeijiSensei on 2012-08-21
If you use one of the GUI package managers, you can browse the list of servers and pick a different one.  I never use the main server but take everything from a mirror at a local university.

Find the menu item in the package manager that lets you configure software sources, pick your country (US, I'd imagine), and browse the server list.  I generally try to pick a server that's geographically near me.

---

### Post by bartonski on 2012-08-21
That did the trick. There's actually an option for 'pick the best server' based on ping times. It might be slightly more rude geographically (I got the university of Minnesota server, which isn't the closest, but a short ping time suggests that it's running along the lowest latency path, which might or might not be just as important).

Ps. Is there a way to do the same configuration on the command line?

---


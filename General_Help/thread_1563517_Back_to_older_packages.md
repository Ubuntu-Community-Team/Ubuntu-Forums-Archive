---
title: "Back to older packages"
date: 2010-08-29
forum: General Help
---

### Post by aparigraha on 2010-08-29
I got some dependency problems that are related to me trying out some ppa's. I narrowed it down to two packages:

[B]libsoprano4
soprano-daemon[/B]

I try to force older versions of the two packages but that just leads to the package manager wanting to remove a heck of a lot of programs that depend on them. So my question is...

Do I really have to remove all those programs and reinstall them again, and if so - what is the sweet command line for that?

**[COLOR="Red"]EDIT:[/COLOR]**
Solved that issue by turning to a terminal (**Synaptic didn't do it **for some reason):

Finding out which version of libsoprano4 and soprano-daemon I had, and which I wanted:

```
apt-cache policy libsoprano4 soprano-daemon
```

when I found out which versions I wanted (2.4.2) I just:

```
sudo apt-get install soprano-daemon=2.4.2+dfsg.1-0ubuntu1.1 libsoprano4=2.4.2+dfsg.1-0ubuntu1.1
```

Nothing but libsoprano4 and soprano-daemon changed or got removed.

---


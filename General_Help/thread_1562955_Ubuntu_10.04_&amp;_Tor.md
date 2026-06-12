---
title: "Ubuntu 10.04 &amp; Tor"
date: 2010-08-28
forum: General Help
---

### Post by dowtish on 2010-08-28
Trying to install Tor as instructed by their website:

*[http://www.torproject.org/docs/debian.html.en#ubuntu](http://www.torproject.org/docs/debian.html.en#ubuntu)*

When I get to the command:

*apt-get update*

[FONT=Verdana]I receive the following message:
[/FONT]
[I]E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory[/I]

What am I overlooking!

Cheers in advance

---

### Post by Spice Weasel on 2010-08-28
Sudo, sudo sudo.

*sudo apt-get update*

---

### Post by dowtish on 2010-08-28
> **Spice Weasel said:**
> Sudo, sudo sudo.

*sudo apt-get update*

It's the simple things in life! LOL

---


---
title: "easy question, profile location"
date: 2009-09-07
forum: General Help
---

### Post by stozi on 2009-09-07
This is from the Midori Browser FAQ:
> Flash/ Netscape plugins don't work

You need to set MOZ_PLUGIN_PATH, for example like this:

export MOZ_PLUGIN_PATH="/usr/lib/mozilla/plugins:/opt/mozilla/lib/plugins"
You can either run that above line and run Midori in the same terminal afterwards or, for the long term, put it in ~/.bash_profile or /etc/profile.d or your respective distribution's place for this.

there's an /etc/profile, but no sign of a .d on it. I think ~ means /home/username right? There's .bashrc, .bash_history and .bash_logout there, but no .bash_profile. 

Where should I put that line?

---

### Post by winotree on 2009-09-07
Is there a .profile??  I have one with some bash commands in it.  ;)

---

### Post by stozi on 2009-09-07
yes! so I should add 

export MOZ_PLUGIN_PATH="/usr/lib/mozilla/plugins:/opt/mozilla/lib/plugins"

to /home/me/.profile ?

---

### Post by loomsen on 2009-09-07
Hi.

.d directories (or more likely, the files inside) are sourced in the matching file.

So, /etc/apt/sources.list.d/bla.list will be sourced in /etc/apt/sources.list

---

### Post by stozi on 2009-09-08
got er working, thank yee all.

---


---
title: "Killall command: &quot;No process found&quot;?"
date: 2011-09-25
forum: General Help
---

### Post by Splat_NJ on 2011-09-25
While trying to have Deluge utilize the "Execute" plugin to close Deluge after a file downloads I stumbled upon the killall command. Here's the command I tried in terminal and it seems to work, yet it gives me a "no process found" response: 

killall /usr/bin/python /usr/bin/deluge-gtk

Why does it close/kill Deluge (what I want), yet give me the response? Is there a better way to do what I want? Thanks.

---

### Post by cgroza on 2011-09-25
Because you are passing 2 process names to it.
It kills python first, taking deluge with it, and then you try to kill deluge again...

---

### Post by Splat_NJ on 2011-09-25
> **cgroza said:**
> Because you are passing 2 process names to it.
It kills python first, taking deluge with it, and then you try to kill deluge again...

I figured that but wasn't 100%. Actually, I just tried my command in Deluge and it did not work. Maybe the -q option is needed....  don't know, but there's gotta be a way to do this. I hope. :)

---


---
title: "Can't load GNOME - log in issue"
date: 2011-02-20
forum: General Help
---

### Post by ep1centre on 2011-02-20
Hi,

I've been slowly changing over to ubuntu and my home server was the last standing windows machine i own, i set about installing Ubuntu server yesterday but i didn't realise it was a terminal only distribution and even though I'm (very) slowly getting to grips with Linux I'm still no where near comfortable enough to set up and use a terminal only distribution.

Anyway after realising my mistake in tying to use the server edition I thought I'd install 10.10 and set that up as a server, after all its just a simple print and file server - no luck  - I thought well maybe being the latest distribution it doesn't support my old PIII machine, so I'll install the more stable 10.04LTS so i did, however same problem, it installs and starts up great but whenever i get to the log in screen i enter my details it starts to load as normal but then the screen goes pixelated and it just resets back to the log in screen again, I'm stuck in this loop.

Hope somebody can help.

Regards, 

Luis.

---

### Post by ep1centre on 2011-02-20
Can anyone help with this issue please, its frustrating, I've tried starting up in "safe mode" and running the package repair tool!

---

### Post by Habitual on 2011-02-20
ep1centre:

Try this. at a terminal prompt login as your normal user.
mv ~/.config ~/.config.org
mv ~/.gcponf ~/.gconf.org

Logout and log back in using GDM.

Let us know...

---


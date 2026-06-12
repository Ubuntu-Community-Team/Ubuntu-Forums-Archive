---
title: "Global proxy setting"
date: 2011-11-21
forum: General Help
---

### Post by neocortex on 2011-11-21
Hello ALL!
I am back to Ubuntu, after long affair with Debian testing, and a bit of flirt with Fedora. I just wanted to try new Unity, despite many complains. Really, I do not think it is worse than Gnome 3 (at least from my experience with Fedora)! However, anyone is entitled to have some opinion!

The reason I am writing is to ask how to set up proxy globally -- using System Settings -> Network?! It seems that this is broken! If not, where I am doing wrong? It's a bit tedious to set up proxy for Firefox, and other stuffs, one-by-one... :(

Best,
PM

---

### Post by lechien73 on 2011-11-21
I've had problems with this as well. The solution for me was to install dconf-tools:

```
sudo apt-get install dconf-tools
```

Then run the editor:

```
dconf-editor
```

Navigate to **System -> Proxy**. Set the mode to Manual, and then the proxies to what you need. I only set the http proxy, and left the others blank with a 0 in the port field.

If you did an upgrade, and have an older version of Firefox or Chrome installed, then these may still use the gconf method of accessing proxy information, in which case running:

```
gconf-tools
```

and configuring the proxies there might help.

---

### Post by neocortex on 2011-11-22
> **lechien73 said:**
> 

Then run the editor:

```
dconf-editor
```

Navigate to **System -> Proxy**. Set the mode to Manual, and then the proxies to what you need. I only set the http proxy, and left the others blank with a 0 in the port field.


Hello and thanks!
However, this seems to be broken too: when I try to select mode, and to change it, dconf messes up. Other fields are possible to change, but this isn't.
Why System Settings -> Network -> Proxy is not working?!?

Best,
PM

---

### Post by lechien73 on 2011-11-22
It is possible to change, it's just that the description is so long, it obscures the field.

If you're using expo or multiple workspaces, then a slightly unorthodox solution would be to massively increase the size of dconf-editor so that it spans multiple workspaces as in the attached screenshot.

Doing this, I was able to change the setting. It is a bug, and the window behaviour in dconf-editor has been reported in Launchpad.

---

### Post by neocortex on 2011-11-22
;) Oh my God, this sounds so upside-down: bug in Network -> Proxy which can be tweaked with the also buggy dconf-editor! Wow!
This sounds so complicate...

PM

---


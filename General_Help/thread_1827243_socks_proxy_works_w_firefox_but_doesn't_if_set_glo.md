---
title: "socks proxy works w/ firefox but doesn't if set globally"
date: 2011-08-17
forum: General Help
---

### Post by adempewolff on 2011-08-17
I've set up an ssh/socks proxy, using this command (with a real ip and port of course):

ssh -ND 1080 [email]austin@xxx.xxx.x.xx[/email] -p xxxx

Now it works swimmingly when I tell firefox to use the proxy directly though preferences:advanced:network:settings

However, if I use the global proxy settings window.  Neither firefox, nor anything else work.

Furthermore, if I use the global proxy settings window to direct http traffic through my other proxy solution ssh/privoxy, firefox will do so when I tell it to use system settings.

I attached screenshots of the settings windows below.  I can't for the life of me figure out what I am doing wrong.

---


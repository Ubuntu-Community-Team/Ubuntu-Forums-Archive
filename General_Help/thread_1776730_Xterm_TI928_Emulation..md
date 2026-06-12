---
title: "Xterm TI928 Emulation."
date: 2011-06-06
forum: General Help
---

### Post by collisionystm on 2011-06-06
My company currently has a Centos box running Acobol. We access it via telnet to do our daily work. In order to save money, I want to start loading computers with ubuntu. The only thing that has stopped me is finding a suitable client for replacing our current windows program. 

We use Reflection.

It telnets to the box using a TI928, VT407 emulation I believe. Anyways, it lets us capture keys like F1, F8, F10 ...etc in order to navigate menus durring the telnet session.

I did find that I can use X-Term to accomplish this by doing the following:

telnet to Server

enter ```
export TERM=xterm
```

However, this must be done everytime and Xterm isnt the best tool to use.

Any suggestions? :confused:

---


---
title: "x11vnc: monitor of server dimmed -&gt; client black. Using client does't prevent dimming"
date: 2012-02-09
forum: General Help
---

### Post by aapo4 on 2012-02-09
Computer A is running Ubuntu and x11vnc-server running. If mouse/keyboard is not used , screen dimms automatically (I think this is kinda default).

Then I use Computer B to connect with vnc-client. (Of course this happened first time when I was far away from server.) Connection works as expected, screen of the Computer A goes on and cursor is moving as expected. But immediately I stop moving mouse or typing, server's screen goes black, and so goes vnc-client. Is this normal?

I hope there are some other way than disable automatic dimming.  Computer A is not always running x11vnc-server, but I start it over ssh, so one workaround could be to turn display on same time, but how to do that over ssh?

---


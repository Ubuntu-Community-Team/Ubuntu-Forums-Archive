---
title: "Tmux configuration"
date: 2012-07-17
forum: General Help
---

### Post by StormeRider on 2012-07-17
I'm looking to customize my tmux config a bit. I have the following .tmux.conf:

[http://paste.ubuntu.com/1097451/](http://paste.ubuntu.com/1097451/)

The biggest problem I'm having right now is that if I want to switch to the next/prev window I do ctrl-a n or ctrl-a p. If I forget to release the ctrl key and do ctrl-a-n or ctrl-a-p, then tmux doesn't recognize that and ignores it. I'm more used to screen which doesn't care and interprets them both equally. 

It's a minor thing, but I spend all day inside of tmux, so I'd really love to sand off this burr and work easier.

I also want to bind a key to toggle window notifications, which would be something along the lines of:
```
bind-key = set-window-option monitor-activity
```
Does that look right?

---


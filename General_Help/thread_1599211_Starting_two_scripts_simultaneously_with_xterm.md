---
title: "Starting two scripts simultaneously with xterm"
date: 2010-10-17
forum: General Help
---

### Post by JohnElway on 2010-10-17
I recently switched from using gnome-terminal to using xterm, and I'm trying to update all my bash aliases accordingly. I have one alias that opens a script, gives it a second to initialize, then starts a second script (they're a server-client pair of scripts that must run together). Since gnome-terminal has tabs I was able to do this:

```
alias startgame='gnome-terminal --tab -t server.py -e "python server.py & sleep 1" --tab -t client.py -e "python client.py"'
```

How would I achieve something similar in xterm? I was thinking that the smartest solution would be something involving 'screen', but I'm not sure how to do this or if it's even possible. If not, how would I open two xterms simultaneously and have them run different commands?

---


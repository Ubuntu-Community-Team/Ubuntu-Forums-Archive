---
title: "Help getting terminal to open on startup"
date: 2009-07-30
forum: General Help
---

### Post by cody7002002 on 2009-07-30
I've been using [this]("http://webupd8.blogspot.com/2009/05/ubuntu-embed-terminal-into-you-desktop.html") guide to embed the terminal into my desktop. All goes well but I want to make it work on startup. I followed the directions making a script
I named it .start_terminal.sh
```
#!/bin/bash
sleep 20 && gnome-terminal --window-with-profile=trans777 --geometry 67x30+10+30 &
```
and saved it in my Home folder. I then went to startup applications and added a new program and browsed to where the script was located /home/cody/.start_terminal.sh and saved. When I restarted my computer the terminal does not come up.

Is it possible that this is interfering with my conky startup script? It uses this script
```
#!/bin/bash
sleep 35 &&
conky
```

Any help is appreciated. Maybe there's in error in my first script somewhere? I'm new to this stuff

---

### Post by cody7002002 on 2009-07-30
I figured it out, I had to make the script executable =)

---


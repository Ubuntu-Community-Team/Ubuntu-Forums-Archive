---
title: "Proper way to start a new x-server?"
date: 2011-07-03
forum: General Help
---

### Post by Gfurst on 2011-07-03
Hey people, as the title says i want to figure out how to properly start  a new x-server(duh!), but i have few a couple questions to be more  direct. The main purpose is to play games and such, also other utilities  such as connect through ssh to another pc.

Now to the questions:
-Does the use of a new x-server really improves game perfomance? In my  tries i couldn't notice, but the obvious advantage of return to regular  desktop without quiting the game seems not that great when switching  between servers lagged a lot( in the tries).

-I've had success with the following:
```
xinit -- :1 vt8
```
Which creates a new server 1 with default client on key F8 (vt8), this  opens the new x-server with a default small console and mouse.
By enter the game onto console it opens successfully, not. It opens okay  and seems to play nice, the problem is with sound which doesn't play in  new x-server. Instead it plays on the first server, I suppose this is  caused by something with Pulseaudio, just a small config setting of  such. So what is it and how to fix it?

-This is question is more about learning, how to properly use the new  x-server, start a display manager and use it such as SSH to connect to  other machine, or simply to start in a lighter environment.
I found a little application x.game that has the purpose of starting a  game in a new x-server with openbox( window manager?), but it doesn't  work as intended.
So how to properly start a new server? ( really general question, if you  want i can be more direct on what i want to know about it)

---

### Post by Gfurst on 2011-07-08
No one? bummer... I guess not many people here are helpers, many new ubuntu users?

Anyway, any suggestion to another section more relevant and that would get more attention? 
If i find out the mysterious mechanics with dazziling solutions I'm sure to post a compiled how-to guide.

---


---
title: "Multiple keyboard-layouts for different users SSH"
date: 2011-02-07
forum: General Help
---

### Post by bartol_78 on 2011-02-07
Hello everybody,

I work in a company where the Ubuntu server is managed by different people around the world.

Day-to-day admin : me in France with an Azerty keyboard
Level 1 24/7 support : team in US with a Qwerty keyboard

Of course there's commands like sudo dpkg-reconfigure console-setup but this one affects the whole system.

I've searched quite a lot on how to change the keyboard layout for one person only, but it always relates to the Gnome interface. 

So I'd like to know if you knew a way to locally change the keyboard layout, only the SSH connection of the user ?

Maybe in the startup scripts of the bash session, or even better, when the user types his user login (so it detects his language and automatically switches to the right keyboard).

Thank you very much !

---

### Post by yota on 2011-02-07
AFAIK the keyboard layout is not a server setting, but a client setting...

I've just tryed this from my ubuntu machine, connecting to an ubuntu server:
```

me@machine# setxkbmap it
me@machine# ssh user@server
user@server# --- <-- this is the key left of the right shift on an italian keyboard
user@server# exit

me@machine# setxkbmap us
me@machine# ssh user@server
user@server# /// <-- this is the same key as before, but with us layout

```

So, long story short, the US team should have no issue as long as they have the keyboard correctly configured on their side.

---

### Post by bartol_78 on 2011-02-07
Thank you for your answer.

Actually, they can't change the keyboard mapping on the server they come from. And they connect to this server via VMWare console...

So basically, it would be the change the keyboard mapping of the user session connected to the console, without root privileges...

---

### Post by yota on 2011-02-07
Ok, now it's clearer...

I'd suggest a "loadkeys us" if the session is a pure console session, or a "setxkbmap us" if it is a console that runs under Xorg.

You can put the command under .bashrc (for instance) of the specific user and you're done.

---

### Post by bartol_78 on 2011-02-07
Yes but as far as I understood it, the loadkeys is system-wide, so it would change OUR keyboard mapping too.

And the server is text only...

---

### Post by yota on 2011-02-08
Using SSH for remote connections would really help... why aren't you using it already?

Anyway you are right about loadkeys: it's indeed system wide since it presumes that each server has one and only one physical console attached to it at any given time.
I suppose that your options are:
[LIST][*]put the appropriate "loadkeys <language>" for each user
[*]switch to ssh for remote admin
[*]use a full blown GUI desktop environment
[/LIST]

---


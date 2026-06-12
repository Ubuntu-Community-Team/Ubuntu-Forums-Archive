---
title: "Fluxbox starup issues"
date: 2006-03-23
forum: General Help
---

### Post by jive_turkey on 2006-03-23
I'm working on setting up fluxbox, but im running into some issues. I have installed fbdesk, and i want it to load when I start fluxbox. i modified the ~./fluxbox/startup to:

[I]exec /usr/bin/fbdesk &

exec /usr/local/bin/fluxbox -log ~/.fluxbox/log[/I]

i then restarted fluxbox and i still get nothing. I know i have icons setup because if i start fbdesk manually from xterm icons come up.

Any ideas...thanx

---

### Post by taurus on 2006-03-23
Remove the "exec" in front of it!!!
```

/usr/bin/fbdesk &

```

---

### Post by jive_turkey on 2006-03-23
ok i made those changes, but when i restart fluxbox, fbdesk doesn't load.
do i need to add somthing to my init file. should i be including any headers into the startup files?

thanx

---

### Post by taurus on 2006-03-23
fbdesk creates an icon on fluxbox, right!!!  Well, did you remember to create any icon for it?  If you want to know whether it is running or not, run this command from the prompt and see if fbdesk is on the list.
```

ps -A

```
I use idesk with my fluxbox though...

---

### Post by jive_turkey on 2006-03-24
I have some icons setup for fbdesk, they are just some simple things like gaim and such, but they come up when i run fbdesk from the terminal. I've read about idesk, let me give that a try. thanks for you help.

---

### Post by jive_turkey on 2006-03-24
Well I installed idesk, but before I get into it, does anyone have any suggestions  about where I should go with it.
Thanks

---

### Post by taurus on 2006-03-24
[QUOTE=jive_turkey]Well I installed idesk, but before I get into it, does anyone have any suggestions  about where I should go with it.
Thanks[/QUOTE]
Should go for what?  Not sure exactly what you mean here...  All you have to do is put it in ~/.fluxbox/startup so idesk will start up when you log into fluxbox.  Then, create some icons for it!!!

---

### Post by jive_turkey on 2006-03-24
I created some icons for idesk, but i still cant get it to startup when i start fluxbox. I tried editing my *~/.fluxbox/startup* but I must be doing somthing wrong still. I've tried everything i could think of but i still cant get it right, how should my startup file read?

---

### Post by taurus on 2006-03-24
Well, would you mind share your ~/.fluxbox/startup then?  Maybe I can spot something for you...  Also, if you can also paste a content of one of your icons so I can see if it's right or not!

---

### Post by jive_turkey on 2006-03-24
My ~/.fluxbox/starup reads:

[I]/usr/bin/idesk&
[begin] (fluxbox)
exec /usr/local/bin/fluxbox -log ~/.fluxbox/log
[end][/I]

The icon contents from ~/.idesktop/valknut.lnk

[I]table Icon
  Caption:DC++
  Command: /usr/bin/valknut
  Icon: /usr/share/pixmaps/valknut.xpm
  Width: 30
  Height: 35
  X: 145
  Y: 230
end[/I]

---

### Post by taurus on 2006-03-24
[QUOTE=jive_turkey]/usr/bin/idesk&
[/QUOTE]
Probably need a space between idesk and &.

> 
  Command: /usr/bin/valknut

```

  Command[0]: /usr/bin/valknut

```

---

### Post by jive_turkey on 2006-03-24
I made the changes, but I still can't get idesk to load. Do you have any more ideas?

---

### Post by eivind on 2006-10-20
I've also had problems with fbdesk/fluxbox/idesk startup. For me, it doesn't help to put anything in ~/.fluxbox/startup. Instead, I do it system-wide, by editing /usr/bin/startfluxbox - as you can see, it's mostly the same file as ~/.fluxbox/startup.

I am struggling with fbdesk right now - let me see what I find out.

Otherwise, try the [fbdesk howto]("http://fluxbox-wiki.org/index.php/Howto_fbdesk") for general instructions. Good luck!

Eivind

---


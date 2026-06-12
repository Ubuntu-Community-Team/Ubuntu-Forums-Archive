---
title: "tsclient settings trumping devilspie config?"
date: 2011-06-27
forum: General Help
---

### Post by rchille on 2011-06-27
Morning all,

I have 2 1680x1050 monitors at work set in Twinview. What I'd like to do is have tsclient open a full screen on one of the monitors leaving the other screen free for local apps (IM, Chrome, email etc).

If I set tsclient t "Operate in full Screen Mode" it takes over both monitors and there is no 1680x1050 option under "Use Specified Screen Size"

I've used Devilspie in the past to do similar things, so I installed it and built the following config (Ok, I used gdevilspie ;)):

```

( if 
( begin 
( contains ( window_name ) "Terminal Server" )
) 
( begin 
( undecorate )
( geometry "1680x1050+1680+0" )
( println "match" )
)
)

```

When I "devilspie -a" It takes the current tsclient config window that I have open, strips the decor and moves it to position 0x0 of the second monitor, which is what I expect to happen.

Haowever, when I connect, tsclient still smears itself over both monitors (I still have it set to fullscreen mode).

Is there a way that I can convince tsclient that "Full Screen" is realy 1680x1050 is stead of 3360x1050?

Thanks!

---

### Post by rchille on 2011-06-27
Ug! RTFM indeed.

Turns out that rdesktop does exactly what I need with:
```
rdesktop -g 1680x1050 -a 16 [servername]
```

I'm still using devilspie to strip off the decorations and to stove rdesktop 1680 pixels over (to the second monitor)

Learn from my fail kids, I hope this helps someone!

:popcorn:

---


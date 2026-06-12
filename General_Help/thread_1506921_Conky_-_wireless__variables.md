---
title: "Conky - wireless_* variables"
date: 2010-06-10
forum: General Help
---

### Post by joshmuffin on 2010-06-10
Hey all, 
I'm trying to use wireless_essid and wireless_link_qual_perc variables in my .conkyrc but they are not working.

I know that if you run conky as root they work and I know that if compiling conky with --enable-wlan will fix it however when i try to install conky with that parameter i get an error: 

```
checking for LUA... no
checking for LUA51... no
checking for LUA51... configure: error: Package requirements (lua5.1 >= 5.1) were not met:

No package 'lua5.1' found
```

However when I enter "lua" output is:
```
Lua 5.1.4  Copyright (C) 1994-2008 Lua.org, PUC-Rio
```

any help would be much appreciated, thanks in advance.

---

### Post by stinkeye on 2010-06-10
Would the conky-all package solve your problem.
It's in synaptic and is compiled with most options.

From synaptic:```
This is a full conky with most compile options enabled:

X11, XDamage, XDBE, Xft, MPD, MOC, OpenMP, math, hddtemp, portmon, RSS,
Weather, wireless, IBM, nvidia, eve-online, Imlib2, ALSA mixer, ncurses,
apcupsd, I/O stats, argb, Lua and the cairo and imlib2 lua bindings.
```

---

### Post by joshmuffin on 2010-06-10
No luck :( I tried it just before but nothing changed. Maybe the option is enabled but my .conkyrc is wrong?

```
${color DimGray}IP $alignr ${addr wlan0}
Connected to $alignr ${wireless_essid}
Connection Quality $alignr ${wireless_link_qual_perc} 
```

Thanks for the help.

---

### Post by stinkeye on 2010-06-11
I think your missing **wlan0** in a couple of parts.
eg I just tried this on my wireless comp and it worked.
```
${color DimGray}IP $alignr ${addr wlan0}
Connected to $alignr ${wireless_essid [COLOR="Red"]wlan0[/COLOR]}
Connection Quality $alignr ${wireless_link_qual_perc [COLOR="#ff0000"]wlan0[/COLOR]}
```

If that doesn't work run **iwconfig** to see what interface your using.

---

### Post by joshmuffin on 2010-06-11
Thank you muchly.
I'm suck an idiot for missing that.
And Yeah it was wlan0 :p

---

### Post by stinkeye on 2010-06-11
> **joshmuffin said:**
> Thank you muchly.
I'm suck an idiot for missing that.
And Yeah it was wlan0 :p

I don't think you need to suck an idiot for missing that.
I'll speak to the Department of Petty Errors (DOPE)
and see if I can get it downgraded to a handshake. 8-[

---


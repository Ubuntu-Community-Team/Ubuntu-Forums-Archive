---
title: "lsof - information about opened connections"
date: 2011-08-11
forum: General Help
---

### Post by HotForLinux on 2011-08-11
I would like to know:
1)why do I have these open connections (have been opem during hours)
2)How can I know more about them
3)what action, command, program,... might have opened them
4)how can I close them

```
**$ lsof -i**
COMMAND     PID   USER   FD   TYPE DEVICE SIZE NODE NAME
.....
plugin-co  7739 user   62u  IPv4  29414       TCP mypc.local:51000->fx-in-f105.1e100.net:www (CLOSE_WAIT)
plugin-co  7739 user   63u  IPv4  29409       TCP mypc.local:55228->jujube.canonical.com:www (CLOSE_WAIT)
plugin-co  7739 user   64u  IPv4  29410       TCP mypc.local:55229->jujube.canonical.com:www (CLOSE_WAIT)
plugin-co  7739 user   65u  IPv4  29411       TCP mypc.local:55230->jujube.canonical.com:www (CLOSE_WAIT)
plugin-co  7739 user   66u  IPv4  29412       TCP mypc.local:55231->jujube.canonical.com:www (CLOSE_WAIT)
.....


``````
**$ps aux|grep 7739**
user    7739  0.0  0.9  78208  5072 ?        Sl   Aug10   0:04 /usr/lib/firefox-3.6.17/plugin-container /usr/lib/adobe-flashplugin/libflashplayer.so 7662 plugin
```

---

### Post by Habitual on 2011-08-11
It's the firefox flash plugin:
/usr/lib/**firefox**-3.6.17/plugin-container /usr/lib/adobe-**flashplugin**/libflashplayer.so

```
lsof -i :7739
```

---

### Post by HotForLinux on 2011-08-11
> **Habitual said:**
> It's the firefox flash plugin:
/usr/lib/**firefox**-3.6.17/plugin-container /usr/lib/adobe-**flashplugin**/libflashplayer.so

```
lsof -i :7739
```

What??

```

$lsof -i :7739
$

```Yes, the flashplugin, 7739, and canonical, that's all I wrote.

---

### Post by Habitual on 2011-08-11
My bad, it's not using that port. Sorry.

---

### Post by HotForLinux on 2011-11-06
> **Habitual said:**
> My bad, it's not using that port. Sorry. ???

What does that mean and what has that got to do with my questions?

---


---
title: "the right dir for your flash and java firefox plugins is.."
date: 2006-06-08
forum: General Help
---

### Post by zasf on 2006-06-08
/usr/local/firefox/plugins

```
matteo@burnt:/usr/local/firefox/plugins$ vdir
total 2.1M
-rwxr-xr-x 1 root root 2.1M 2006-06-08 23:41 libflashplayer.so
lrwxrwxrwx 1 root root   53 2006-06-08 23:48 libjavaplugin_oji.so -> /opt/jre1.5.0_07/plugin/i386/ns7/libjavaplugin_oji.so
-rwxr-xr-x 1 root root  20K 2006-05-09 03:58 libnullplugin.so
matteo@burnt:/usr/local/firefox/plugins$

```

and not 
/usr/lib/firefox/plugins
/usr/lib/mozilla/plugins
/usr/lib/mozilla-firefox/plugins

took me a couple of ours to figure out

---

### Post by givré on 2006-06-08
How did you instal firefox, is this the official package?
mine are place in  /usr/lib/firefox/plugins

EDIT: like expected

---

### Post by scxtt on 2006-06-08
that's odd, i just downloaded 1.5.0.4 and put it in /usr/lib/firefox_1.5.0.4/ then put some plugins in /usr/lib/firefox_1.5.0.4/plugins and it works fine ... you might run into problems depending on where the actual firefox binary is located ... i'm running the binary just a single level up from where my plugins folder for that ver. of firefox exists ...

---

### Post by zasf on 2006-06-09
@givré: fresh dapper release install, I tried to install firefox plugins in other dirs.. but it didn't work until I discovered /usr/local/firefox/plugins

@scxtt: I actually didn't check wich binary is in my path, but I should do it

I found other posts on this issue, so I guess it was worth to drop a line

---


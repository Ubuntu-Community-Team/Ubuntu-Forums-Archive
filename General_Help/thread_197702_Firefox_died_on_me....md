---
title: "Firefox died on me..."
date: 2006-06-16
forum: General Help
---

### Post by Lunar_Lamp on 2006-06-16
I have always used Opera on windows, but decided to give firefox an extended trial as my browser now I have fully switched to linux.  I explored around a bit, and installed a few (ok about 8 or 9, e.g. mouse gestures - and a couple of themes) firefox plugins from the site, then closed the browser to load them.

Now, firefox won't open.  Typing "mozilla-firefox" from the command line gives this error message:

```
/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/firefox/components/libdocshell.so: undefined symbol: PR_GetPhysicalMemorySize
```

I have no idea whatsoever how to fix this one...

---

### Post by th3james on 2006-06-16
try starting it in safemode:
firefox -safe-mode
that will disable extensions

---

### Post by Lunar_Lamp on 2006-06-16
[QUOTE=th3james]try starting it in safemode:
firefox -safe-mode
that will disable extensions[/QUOTE]

I can't believe I missed that in the the man pages, I specifically looked for it - heh.  Still the same problem though:

```
$ firefox -safe-mode
/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/firefox/components/libdocshell.so: undefined symbol: PR_GetPhysicalMemorySize
```


```
$ mozilla-firefox -safe-mode
/usr/lib/firefox/firefox-bin: symbol lookup error: /usr/lib/firefox/components/libdocshell.so: undefined symbol: PR_GetPhysicalMemorySize

```

---

### Post by th3james on 2006-06-16
Hmm... well, im stuck... you could try copying our all your bookmarks, and doing a complete remove and re-install in synaptic?

---

### Post by Lunar_Lamp on 2006-06-16
[QUOTE=th3james]Hmm... well, im stuck... you could try copying our all your bookmarks, and doing a complete remove and re-install in synaptic?[/QUOTE]

I tried that - and I still get the same error :-s

---

### Post by math on 2006-06-16
Weird. Try [http://www.getswiftfox.com/](http://www.getswiftfox.com/).
BTW swiftfox is much faster.

---

### Post by Lunar_Lamp on 2006-06-16
[QUOTE=math]Weird. Try [http://www.getswiftfox.com/](http://www.getswiftfox.com/).
BTW swiftfox is much faster.[/QUOTE]


I have heard rumblings of swiftfox - how does it relate to firefox?

Is it just a reworking of the source-code in a cleaner manner, whilst retaining 100% compatibility?

---

### Post by math on 2006-06-16
Swiftfox is a build of firefox optimized for a specific CPU.
The source code is the same i suppose. It's compiled with other flags.

---

### Post by Lunar_Lamp on 2006-06-16
I can't work out which one I want...

I am using a k7 kernel, with a 64bit processor running 32bit ubuntu - there is no k7 version that I can see...

---

### Post by math on 2006-06-16
Go to [http://www.getswiftfox.com/](http://www.getswiftfox.com/) -> Swiftfox 1.5.0.4 -> Athlon 64

---

### Post by Lunar_Lamp on 2006-06-16
Would that not be for a 64bit OS though?

---

### Post by math on 2006-06-16
No, every download there is a 32-bit build.

---


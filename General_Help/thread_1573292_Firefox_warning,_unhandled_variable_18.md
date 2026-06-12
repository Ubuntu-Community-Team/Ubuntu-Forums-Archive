---
title: "Firefox warning, unhandled variable 18"
date: 2010-09-12
forum: General Help
---

### Post by jquis8411 on 2010-09-12
Yesterday I just happened to decide to start Firefox from the terminal and got this warning   "  *** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()" Than I get this"*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:2533):invoke_NPP_HandleEvent: assertion failed: (rpc_method_invoke_possible(plugin->connection))" I dont think I would have ever noticed an issue if I hadn't run Firefox from the terminal. I have 64 bit Ubuntu and my version of Firefox (according to Help>about Monzilla Firefox) is version 3.6.9, Firefox for Ubuntu canonical- 1.0. Anyone have any ideas if this is even a real issue. Like I said, I may never have even noticed a problem. Thanks

---

### Post by Rubi1200 on 2010-09-12
I don't know about this particular problem, but this site has a lot of excellent information for dealing with and troubleshooting Firefox problems:
[http://firefox-tutorials.blogspot.com/](http://firefox-tutorials.blogspot.com/)

(courtesy of forum member lovinglinux)

Hope this helps :)

---

### Post by lovinglinux on 2010-09-12
I don't know exactly what that error message means, but is definitely the flash plugin causing it.

---

### Post by jquis8411 on 2010-09-12
Hey guys The link Rubi gave was a great link but unfortunately didn't specificaly help me. It's definately a flash problem that I think (I'm new to Ubuntu and firefox) is related to 32 bit flash running in my 64 bit world. My only error at this point (with a bunch of flash uninstalled is "LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
So at this point I think I need to figure out what the correct ELFCLASS libflashplayer is. I untared 10.1 flash but I dont think it did the trick sooooo...any ideas?

---

### Post by lovinglinux on 2010-09-12
> **jquis8411 said:**
> Hey guys The link Rubi gave was a great link but unfortunately didn't specificaly help me. It's definately a flash problem that I think (I'm new to Ubuntu and firefox) is related to 32 bit flash running in my 64 bit world. My only error at this point (with a bunch of flash uninstalled is "LoadPlugin: failed to initialize shared library /usr/lib/mozilla/plugins/libflashplayer.so [/usr/lib/mozilla/plugins/libflashplayer.so: wrong ELF class: ELFCLASS32]
So at this point I think I need to figure out what the correct ELFCLASS libflashplayer is. I untared 10.1 flash but I dont think it did the trick sooooo...any ideas?

The ELFCLASS error is because you are running a 32bit plugin on  64bit system. Downloading from Adobe and extracting the so file won't work, because Adobe releases only 32bit versions. so I guess your problem is because of that.

Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

BTW, thanks to you and Rubi1200 for the comments about my site.

---

### Post by jquis8411 on 2010-09-13
Well I downloaded Flashaid and followed ***all*** ; ) the directions (TYBTW) and I definately narrowed it down to shockwave flash 10.1 r82. I still get warnings, even a new one "*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() wait for reply: Connection reset by peer" But I'm starting to think this is just going to be a fact of life until adobe steps up and makes a 64 bit.

---

### Post by lovinglinux on 2010-09-13
> **jquis8411 said:**
> Well I downloaded Flashaid and followed ***all*** ; ) the directions (TYBTW) and I definately narrowed it down to shockwave flash 10.1 r82. I still get warnings, even a new one "*** NSPlugin Wrapper *** ERROR: NPClass::Invalidate() wait for reply: Connection reset by peer" But I'm starting to think this is just going to be a fact of life until adobe steps up and makes a 64 bit.

Try to re-install nspluginwrapper.

```
sudo apt-get install --reinstall nspluginwrapper
```

---

### Post by jquis8411 on 2010-09-13
haha yea I tried that after I used flashaid but in hind sight that should have been one of the first things I tried more than 6 hours ago;)

---


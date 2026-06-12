---
title: "Shockwave Flash in Firefox 1.5"
date: 2006-02-06
forum: General Help
---

### Post by wilshire on 2006-02-06
i installed the mozilla build of firefox 1.5

two things: 

it is MUCH faster at rendering pages than the official ubuntu binary for firefox 1.0.7, which always did seem a little sluggish for some reason.

shockwave flash doesn't work with it, even though i think i've got it installed. it works fine in 1.0.7 and in my other browsers (epiphany, galeon) as well. where can i find a plugin that works?

---

### Post by jrib on 2006-02-06
Unfortunately, there is no shockwave for linux.  You can send a nice email to macromedia about it as I have done, if you wish :/

---

### Post by dcstar on 2006-02-06
[QUOTE=_jason]Unfortunately, there is no shockwave for linux.  You can send a nice email to macromedia about it as I have done, if you wish :/[/QUOTE]
There **is** Shockwave FLASH for Linux.

Copy or link the libflashplayer.so, flashplayer.xpt  and/or libflash-mozplugin.so files into your new FF 1.5 plugins directory.

---

### Post by wilshire on 2006-02-06
i've already done that. it still won't work.

---

### Post by nanotube on 2006-02-06
first question to ask: is flash even enabled? in firefox, go to "about:plugins" page (enter that into the url bar). see if flash is in the list, and if it says it is enabled. 

also, you might try getting the newer flashplayer from the macromedia website, unzip, and shove the .xpt and .so into your ff1.5 plugins dir, and then try it.

---

### Post by nanotube on 2006-02-06
stupid smileys... its supposed to be "about", followed by colon (":"), followed by "plugins".

---

### Post by StarkD on 2006-02-07
[QUOTE=nanotube]first question to ask: is flash even enabled? in firefox, go to "about-plugins" page (enter that into the url bar). see if flash is in the list, and if it says it is enabled. 

also, you might try getting the newer flashplayer from the macromedia website, unzip, and shove the .xpt and .so into your ff1.5 plugins dir, and then try it.[/QUOTE]

I have the following line in about-plugins in Firefox:

```
MIME Type                       Description       Suffixes   Enabled
application/x-shockwave-flash   Shockwave Flash   swf        Yes
```

but Shockwave doesn't work for example at this webpage:
[http://www.miniclip.com/polardash/polardash.php](http://www.miniclip.com/polardash/polardash.php)

---

### Post by nanotube on 2006-02-07
hi, checked out your page
that is not flash, that appears to be straight up shockwave - which does not exist for linux. there are two players from macromedia - shockwave, and flash. this one is shockwave. so sorry, does not look like you will be able to open that one.
to test if your flash works, try going to this one:
[http://www.miniclip.com/blackknight.htm](http://www.miniclip.com/blackknight.htm)

---


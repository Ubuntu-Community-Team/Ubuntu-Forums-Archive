---
title: "Chromium temp files"
date: 2011-02-11
forum: General Help
---

### Post by arroyoss on 2011-02-11
Yesterday (Feb-10, 2011) Google Chromium browser changed its temporal dir folder to an "unknown" directory. Before I was able to download Flash Videos by just opening the /tmp folder and looking for a file with filename like "FlasXXX". Now I do not know where the browser is temporary storing the flash video. **[B][B][B][B][COLOR="Red"]I alreadey checked the directory ~/.cache/chromium/Default/Cache[/COLOR]**[/B][/B][/B][/B] and the temporary video is not there. I am using Ubuntu 10.10

Thanks for any provided help

---

### Post by williamts99 on 2011-02-12
> **arroyoss said:**
> Yesterday (Feb-10, 2011) Google Chromium browser changed its temporal dir folder to an "unknown" directory.

~/.cache/chromium/Default/Cache

---

### Post by arroyoss on 2011-02-12
Thanks for your answer but I had checked that directory looking for a filename like FlashXXX video. That is way I couldn't find it. Now tha name format is **[COLOR="Blue"]f_XXXX[/COLOR]**.

Thanks!

---

### Post by williamts99 on 2011-02-12
> **arroyoss said:**
> Thanks for your answer but I had checked that directory looking for a filename like FlashXXX video. That is way I couldn't find it. Now tha name format is **[COLOR="Blue"]f_XXXX[/COLOR]**.

Thanks!

No problem, I should have mentioned that.  It also helps to clear your cache(ctrl-shift-del) and to sort by file size, because the flash video is usually going to be one of, if not THE, largest file in there.

---


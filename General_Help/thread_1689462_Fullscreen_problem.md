---
title: "Fullscreen problem"
date: 2011-02-16
forum: General Help
---

### Post by AdamDM on 2011-02-16
Whenever I make a video fullscreen (e.g. youtube videos) it goes to fullscreen and then instantly freezes the frame. The audio continues, and the video is restored after I cancel fullscreen. Does anyone know how I can fix this or what may have caused it? I haven't done anything with ubuntu yet so I don't think I changed anything accidentally.

Also when the computer boots up I get a list of 7 different options, uncluding windows 7 as 1 option, some kind of memory test duplicated, and two different options implying load ubuntu, also duplicated - any idea what I've done here?

---

### Post by jerrrys on 2011-02-17
have you installed 'ubuntu restricted extras'  ?

---

### Post by sydbat on 2011-02-17
> **AdamDM said:**
> Whenever I make a video fullscreen (e.g. youtube videos) it goes to fullscreen and then instantly freezes the frame. The audio continues, and the video is restored after I cancel fullscreen. Does anyone know how I can fix this or what may have caused it? I haven't done anything with ubuntu yet so I don't think I changed anything accidentally.First, follow these guides...

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then install [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") in Firefox.

> Also when the computer boots up I get a list of 7 different options, uncluding windows 7 as 1 option, some kind of memory test duplicated, and two different options implying load ubuntu, also duplicated - any idea what I've done here?This list is called [GRUB]("http://en.wikipedia.org/wiki/GNU_GRUB"). The items listed are:

Ubuntu
Ubuntu Recovery
Memory test
Memory test with other options

Other OS's, in your case Windows 7

If there are more Ubuntu's listed, it is because they are older kernels, which are there in case you need them. I keep at least one older kernel, others keep them all. If you want to remove the older kernels, let us know and we can walk you through that.

Oh, and Welcome to the UF!!

---


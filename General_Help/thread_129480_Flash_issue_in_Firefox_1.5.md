---
title: "Flash issue in Firefox 1.5"
date: 2006-02-13
forum: General Help
---

### Post by Greeface on 2006-02-13
I recently installed fireofx 1.5 from a guide here, and it has worked great.  Only one problem: no flash objects show up.  I tried downloading and installing it form the Macromedia website, but it still doesn't work.

Any ideas?

---

### Post by nanotube on 2006-02-13
did you make sure that you have the files 
flashplayer.xpt
libflashplayer.so
in your /opt/firefox/plugins directory (or wherever you installed ff1.5 to)? or at least links to those two? 
from your description it seems that you neglected to put or link them there.

---

### Post by Greeface on 2006-02-14
Oh yeah, i forgot it installed to that directory.  Upon checking, however, links to both of those were there.  Would I have to put the original files in there?  Also, when I go to 'about:plugins' it says that it's installed.

thanks for the help so far

---

### Post by nanotube on 2006-02-14
well, if about:plugins says its installed, then it's there. in that case... i do not know why it does not display. are you sure it does not display any flash objects? or maybe its just some particular one that you are testing it with that does not display? (eg, try going to miniclip.com that has a bunch of flash games, to see if any of them work...)

---

### Post by aysiu on 2006-02-14
Do you have the Adblock extension in your Firefox?

If so, make sure Obj-Tabs does not have a check next to it in the Adblock preferences.

---

### Post by nanotube on 2006-02-14
ah, aysiu, good call. in fact, might be a good idea to just disable adblock (and other extensions that may have an effect on flash, such as flashblock, etc), and try it like that and see if that works...

---

### Post by Greeface on 2006-02-14
Ah, I do have AdBlock installed, and when I looked at it i realized that it was still the version for Firefox 1.07.  I updated it and now it works!   Thanks for the help, both of you.  Not having flash was getting annoying.

---

### Post by nanotube on 2006-02-15
all credit goes to aysiu on this one. :)

---


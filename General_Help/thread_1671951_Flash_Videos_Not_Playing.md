---
title: "Flash Videos Not Playing"
date: 2011-01-20
forum: General Help
---

### Post by drswingingblades on 2011-01-20
I've looked around and I cant find my exact problem anywhere.

Pandora won't work at all, but i think thats a separate problem?

the main thing is that only some youtube videos will play which gets  extremely annoying and also websites that run mostly off flash type  imagery wont load (ie buffalowildwings.com and callofduty.com)


here's my about:plugins

```
**Shockwave Flash**

 File:  libgnashplugin.soVersion:   Shockwave Flash 10.1 r999.
Gnash 0.8.8, the GNU SWF Player.   Copyright (C) 2006, 2007, 2008, 2009, 2010   [Free   Software Foundation]("http://www.fsf.org/"), Inc. 
   Gnash comes with NO WARRANTY, to the extent permitted by law.   You   may redistribute copies of Gnash under the terms of the   [GNU General Public   License]("http://www.gnu.org/licenses/gpl.html"). For more information about Gnash, see [   http://www.gnu.org/software/gnash]("http://www.gnu.org/software/gnash/").   
  Compatible Shockwave Flash 10.1 r999.   MIME Type Description Suffixes  Enabled    application/x-shockwave-flash Shockwave Flash swf Yes
```


thanks in advance for the help

---

### Post by lithopsian on 2011-01-20
What are you browsing with?  This is almost certainly related to the particular browser (Firefox and Chrome use different Flash plugins, for example) and you might get a better answer at the right browser forum.

---

### Post by drswingingblades on 2011-01-20
oh, yeah sorry.

im running 10.10 and using firefox

---

### Post by lovinglinux on 2011-01-20
Your problem is that you have Gnash plugin not the one from Adobe.

Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

---


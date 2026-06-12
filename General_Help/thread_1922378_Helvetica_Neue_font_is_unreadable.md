---
title: "Helvetica Neue font is unreadable"
date: 2012-02-08
forum: General Help
---

### Post by sphoid on 2012-02-08
I'm running kubuntu 11.11 and google chrome stable and i've been having a really hard time reading any web pages that make use of the helvetica neue font. Regardless of the color specified in the css the font is rendered in a really light grey which contrasts poorly against white and grey backgrounds (which includes the majority of the web). Viewing the font in the system settings -> Application appearance panel gives the same results leading to believe kde is not rendering the font correctly. Given that this font is highly popular for some reason I run into a lot of websites that I have to strain to read. Is this a known issue? Is there a solution for this?

---

### Post by dino99 on 2012-02-08
cant help much as i dont know this font and dont use kde, but you can search at some errors logged, and/or try other theme(s) and/or purge then reinstall all the related font package(s)

the system can be checked with:

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

---

### Post by JonUK76 on 2012-02-08
You can disable fonts without uninstalling in KDE font manager (right click font name and choose "Disable").  Worth trying just to see if your browsing experience improves - sites should default to one of the other Sans font families instead (Arial, Deja Vu, Nimbus Sans L etc.).

I don't have Helvetica Neue on any of my systems so can't comment on rendering issues on that font specifically.  Do you have [all weights]("http://www.fonts.com/font/linotype/neue-helvetica") of the font installed or just one of the "ultra light" versions?

---


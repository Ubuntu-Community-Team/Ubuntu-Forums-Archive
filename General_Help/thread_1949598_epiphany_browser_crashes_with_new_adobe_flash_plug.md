---
title: "epiphany browser crashes with new adobe flash plugin"
date: 2012-03-30
forum: General Help
---

### Post by claracc on 2012-03-30
Hello,

Today I have received the update of flashplugin-installer in order to install adobe flash player plugin 11.2.202.228 in my old laptop.

I have installed the update in my lubuntu natty pentium III, and since this moment when I run epiphany browser (2.30.6) and a flash video is in the web page, the browser crash.

Then I tried to open newspaper web pages with chromium (17.0.963.79) and in the place where there is the flash video it is said missing plugin.

What I have done is to force the version of flashplugin-installer to 10.2.159.1 which was the one available in synaptic with the new 11.2.202.228 which causes the crashes in epiphany.

I use epiphany browser in this old laptop because is the only browser with which I can surf the web with reasonable speed (cromium is too much for this laptop) and I would like to use last adobe flash plugin, ¿how can i fix the problem?, ¿is it a bug or there is something incompatible?

Thanks in advance

---

### Post by rockhen on 2012-03-31
Same problem here on Chromium, Seamonkey and Firefox on Ubuntu 11:04 and I had to downgrade Flash also](*,)

---

### Post by claracc on 2012-03-31
As I can read in the fora:

[http://ubuntuforums.org/showthread.php?t=1949107](http://ubuntuforums.org/showthread.php?t=1949107)

[http://ubuntuforums.org/showthread.php?t=1949605](http://ubuntuforums.org/showthread.php?t=1949605)

there is a problem with last adobe flash player plugin 11.2.202.228 and the browsers in ubuntu: firefox, chromium, epiphany. The problem can be worst with epiphany 2.30.6 since it crashes when showing pages with flash video.

The only workaround seems to be downgrade flash player?:

[http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/)

Is there any bug report about this last adobe flash plugin?
Is it advisable to try gnash in epiphany or is it a worst solution to see flash videos?

---

### Post by Lothsahn on 2012-05-02
I attempted to install flashaid, but it didn't fix the problem.  Flashaid just attempted to reinstall the same broken 11.2.202.233 version of the plugin.

I finally resolved the problem by manually installing the adobe-flashplugin_11.1.102.62-0lucid1_i386.deb package.

---

### Post by lovinglinux on 2012-05-02
> **Lothsahn said:**
> I attempted to install flashaid, but it didn't fix the problem.  Flashaid just attempted to reinstall the same broken 11.2.202.233 version of the plugin.

I finally resolved the problem by manually installing the adobe-flashplugin_11.1.102.62-0lucid1_i386.deb package.

If you want to use Flash-Aid to downgrade, follow these instructions:

[Flash 11.2.202.228 solutions](http://ubuntuforums.org/showthread.php?t=1953796)

---


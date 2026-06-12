---
title: "Firefox 1.5 _very_ crash happy..."
date: 2006-01-26
forum: General Help
---

### Post by senectus on 2006-01-26
Anyone else noticed this?

In particular if I open a page with an embedded video, it will lock up FF and then crash the whole thing out with _all_ tabs as well.

FF1.5 is _much_ quicker than 1.07 but if it's going to stay crash happy and I'm going to loose my ability to open new tabs from clicking links in other programs (like evolution and Blam!) then I want to go back to 1.0.7..

Is there any way to go back easily?

---

### Post by mishranurag on 2006-01-26
Yeah, I noticed it too. You are not alone.
Anurag

---

### Post by Lord Illidan on 2006-01-26
About the crash happiness.. search the forum about firefox + xim . Basically, scim, which firefox appears to be using, is a piece of crap in Ubuntu, which is why Firefox is so crash happy. Change it to xim.

Also, if you installed it via automatix, you might want to install it again, as per the wiki. It worked for me..

P.S. to start firefox in xim, use this command:

```
GTK_IM_MODULE=xim /opt/firefox/firefox %u
```

---

### Post by dcstar on 2006-01-26
[QUOTE=Lord Illidan]About the crash happiness.. search the forum about firefox + xim . Basically, scim, which firefox appears to be using, is a piece of crap in Ubuntu, which is why Firefox is so crash happy. Change it to xim.
.......[/QUOTE]
SCIM isn't even installed on my Breezy system (according to Synaptic), and my FF 1.5 isn't "crash happy".

---

### Post by Lord Illidan on 2006-01-26
[quote=dcstar]SCIM isn't even installed on my Breezy system (according to Synaptic), and my FF 1.5 isn't "crash happy".[/quote]

Well, my machine was Kubuntu Breezy.. which may be one thing..

And it was definitely crash happy.. 10 crashes in as many minutes, I am not joking or exaggerating. Now it is rock solid.

Try running firefox from the terminal and see what error message it gives upon crashing.

And take a look at this : [http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started](http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started)

Upon doing this firefox became useful!

---

### Post by kingsidy on 2006-02-05
to add to what other suggested, also update to the latest version which 1.5.0.1. Sometimes it helps. also check which extension you installed. there might be one that is causing it to crash. for example when i installed the tab preference extension, my ff started behaving weird. after i uninstalled it, it went back to normal. check into that too.

---

### Post by grte on 2006-02-05
Also, to get other programs to interact with 1.5, just select System -> Preferences -> Preferred Applications, select the Web Browser tab, and change mozilla-firefox to just firefox.

---


---
title: "Problem with two dead characters"
date: 2011-01-05
forum: General Help
---

### Post by Queequeg on 2011-01-05
Since I installed the last version of Kubuntu, I can't enter the caret(^) and the acute accent(´) on their own in kde programs, like Kate or Konsole.

Accented characters enter alright (á, &#265;,...) but I really need the caret.

This has never happened before in the many versions of Kubuntu I have used.

Any clues? Is it a bug?

Thanks

---

### Post by cgroza on 2011-01-05
I am not using KDE but you should check your key mapping to see if the right layout is selected.

---

### Post by Queequeg on 2011-01-05
The keymapping is good, since I can write â everywhere and ^ here and in openoffice.

---

### Post by Queequeg on 2011-01-05
Well, I found out how to do it, and I expose it here just in case anybody else is as perplex as I was. I was banging away at the keyboard in desperation when the ^ appeared in kate: while pressing the accent key, press <space>.

I can live with that, but it seems weird that umlaut(¨) and acute(´) have preserved their old behaviour -that is pressing the key twice- and ^ and ` have changed it for the above described. So something is not quite right but, at least, I can get back to work.

---

### Post by Zorael on 2011-01-06
It depends on what input method engine (IME) you're using. GTK and Qt4 programs can be set to use different ones. For me, I can produce a ^ in all programs by double-hitting the ^ keybind, or by hitting it once and hitting space. I can't reproduce the Windows behavior though, where if I hit ^ once and then d, I'd get ^d.

I'm using [**UIM**](http://en.wikipedia.org/wiki/Uim), which is an input method allowing for Japanese input. I believe [**ibus**](http://en.wikipedia.org/wiki/Intelligent_Input_Bus) is currently the default in Ubuntu and Kubuntu, but you don't necessarily have all the libraries installed for it to work in Qt4/3 programs.

If you don't need exotic language input, you may be able to get similar behaviour I get by starting **im-switch** (in 10.10) from a run box or a terminal, and selecting '*Use xim (default-xim)*'. You'd need to log out and back in to notice any changes.

In 10.04 or earlier you'd need to enter the following in a terminal instead;
```
$ im-switch -s default-xim
```

---

### Post by Queequeg on 2011-01-08
Thanks a lot. I'll give it a go.

---


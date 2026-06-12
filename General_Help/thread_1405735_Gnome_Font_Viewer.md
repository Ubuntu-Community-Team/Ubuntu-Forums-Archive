---
title: "Gnome Font Viewer"
date: 2010-02-13
forum: General Help
---

### Post by jzacsh on 2010-02-13
**Gnome-Font-Viewer won't start from the menu bar**, which means I can't browse fonts at all. *I really need it to use it though :(*

I can't figure out what's wrong. I've tried typing the following into a terminal (*immediately after clicking "font viewer" from the gnome menu*)
```

ps -aujz | grep -i font
```
.. and I find nothing.

I found this "[Karmic Koala Testing]("http://ubuntuforums.org/showthread.php?t=1256400")" thread with the same thing, **closed and unsolved**:
[http://ubuntuforums.org/showthread.php?t=1256400]("http://ubuntuforums.org/showthread.php?t=1256400")

I tried running font-viewer manually, like so:
```

$ gnome-font-viewer /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf

```

The above ^ way works, but that's **the only way** I can get it to launch, which really defeats the purpose, because I can't browse around through fonts.

I'm using Ubuntu 9.10 with all the latest upgrades (*just checked again now*), here's **uname -a**:
```
Linux mybook 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux

```

**Any suggestions? Any one experiencing this?**

---

### Post by jken146 on 2010-02-13
What happens when you issue ```
gnome-font-viewer
``` without any arguments?

---

### Post by jzacsh on 2010-02-13
```
$ gnome-font-viewer
usage: gnome-font-viewer fontfile

```

**There's no man page or --help parameter.** Is this an application that I'm not supposed to be using via GUI? .. Is this application supposed to be the back bone to a "*font-browser*"-type front end? If so, that'd be ridiculous, because its practically already a finished product -- I just need a scroll bar on the left so I can click on other fonts and watch the preview change.

I tried searching google with queries like "_site:gnome.org/projects font-viewer_" but I'm not finding anything, I feel like **there's gotta be an explanation somewhere**, of what this app is for.

This project is my only hope right now: but there's no deb, only an RPM -- and the source isn't compiling for me: [http://gfontview.sourceforge.net/](http://gfontview.sourceforge.net/)
When I run **./configure** I get a ton of "checking..." output, as I'd expect from such a script, and then:
```
configure: error: installation or configuration problem: C++ compiler cannot create executables.
```

[B]see my attached output of:
[/B]```
$ gnome-font-viewer /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
```

---

### Post by jzacsh on 2010-02-13
> **jken146 said:**
> What happens when you issue ```
gnome-font-viewer
``` without any arguments?

What does it do when **you** run the above?

---

### Post by jken146 on 2010-02-13
suggested alternatives: [http://ubuntuforums.org/showthread.php?t=666919](http://ubuntuforums.org/showthread.php?t=666919)

---

### Post by jken146 on 2010-02-13
fontmatrix looks like a possibility

---

### Post by jzacsh on 2010-02-13
> **jken146 said:**
> suggested alternatives: [http://ubuntuforums.org/showthread.php?t=666919](http://ubuntuforums.org/showthread.php?t=666919)

Thank you for finding this! I can't imagine how much googling/hair-pulling I'd do without forums like this.

---

### Post by jken146 on 2010-02-13
There is an old ubuntu package for gfontview [http://packages.ubuntu.com/dapper/gfontview](http://packages.ubuntu.com/dapper/gfontview)

---

### Post by jzacsh on 2010-02-13
> **jken146 said:**
> There is an old ubuntu package for gfontview [http://packages.ubuntu.com/dapper/gfontview](http://packages.ubuntu.com/dapper/gfontview)

awesome, hopefully the next person will find everything piled up here in one thread. :)

---

### Post by falconindy on 2010-02-13
xfontsel is the tried and true solution.

---

### Post by Andrew_P on 2010-12-13
Like many things in Gnome and Ubuntu, probably broken, with no-one able or willing to fix it.  It seems these features are left in the menus, perhaps with the icon deactivated, as little cowpies for novice users to step into so that the cognoscenti can lean back in their easy chairs and chuckle at us rubes.  In the alternative, they may be left in the menus in a forlorn hope that if enough people stumble across their non-functionality, someone may eventually step forward and try to fix the applications.

While installing Ubuntu 10.04 LTS a few days ago I found that the "Report a problem ..." icon also didn't work.  Clicking on it with the System Monitor running produced about a half-second blip of activity in the System Monitor, and then -- *nothing!*  I posted a question and within 24 hours got the reply that this feature was broken and non-working, and had been that way for years; in other words, the executable has been replaced with a dummy program that runs and does nothing, not even displaying a dialog box that the program is a dummy.  The same may be true of Gnome Font Viewer.

This is an example of the things about Linux in general and Ubuntu in particular that really frosts me and makes me continue to use an assortment of Microsoft Windows machines for *real* work.  Canonical is missing the boat by allowing this kind of stuff to go on.  It generates plenty of ill will, even if Ubuntu is available for "free".:mad:

---

### Post by silverstroller on 2012-04-18
jken146 - Many thanks for pointing to fontmatrix. Just what the doctor ordered, and pleased to report that it works well on Mint 12. You are a star sir!

---

### Post by oldos2er on 2012-04-18
Closed, necromancy.

---


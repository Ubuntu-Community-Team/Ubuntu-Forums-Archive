---
title: "Inkscape 0.48 and Maverick: glitchy ruler bars"
date: 2010-10-15
forum: General Help
---

### Post by BobSongs on 2010-10-15
[COLOR=#333333]See the attached files for the visual glitch in Inkscape 0.48 in Maverick.
[/COLOR]
[LIST]
[*][COLOR=#333333]The source code was compiled under 9.10 without this visual glitch.
[/COLOR]
[*][COLOR=#333333]The source code was compiled under 10.10 with this glitch.
[/COLOR]
[*][COLOR=#333333]Version 0.48 was installed from the Maverick repositories with this glitch.
[/COLOR]
[*][COLOR=#333333]This also happened installing Inkscape 0.48 on the Live CD with the same glitch.
[/COLOR]
[/LIST]
[COLOR=#333333] Has anyone come across this? A friend of mine had the same glitch under 10.10.


Has anyone resolved this or can point point to a hack?


Thanks!
[/COLOR]

---

### Post by ujan on 2010-10-15
same thing happened to me.
thinkin of getting back the earlier version of Inkscape :D

---

### Post by StevenD on 2010-10-16
I just installed Ubuntu 10.10 a few days ago and installed Inkscape 0.48 and that same thing is happening. I checked on the bug reports for Inkscape and added my comments. It works fine in Windows 7. I was wondering if it is an Ubuntu problem. Don't know just guessing. I wonder how Inkscape 0.48 works on an earlier version of Ubuntu.

StevenD

---

### Post by BobSongs on 2010-10-31
> **StevenD said:**
> ... I wonder how Inkscape 0.48 works on an earlier version of Ubuntu.

StevenD
[COLOR=Silver]**[SIZE=4]analysis[/SIZE]**[/COLOR]
** Inkscape: version 0.48.0 r9654 (compiled)**
Compiled in: Ubuntu 9.10, Karmic

[LIST]
[*]The rulers work [COLOR=#333333]**perfectly**[/COLOR] under this system.[/LIST]

**Inkscape: version 0.48.0 r9654 (installed from repositories)**
Installed in: Ubuntu 10.10, Maverick

[LIST]
[*]The rulers fail to work properly.[/LIST]

** Inkscape: version 0.48.0 r9654 (compiled)**
Installed in: Ubuntu 10.10, Maverick

[LIST]
[*]The rules also fail to work properly.[/LIST]

---

### Post by leandro.mat on 2011-01-30
Is this problem gone ? I am using Ubuntu 10.10 and Inkscape 0.48 and having the same  problem. Can anyone point out the solution for this problem ?

---

### Post by edboyww on 2011-02-10
Anyone? I have the same problem.

UPDATE: seems the solution is aproaching
[https://bugs.launchpad.net/inkscape/+bug/627134](https://bugs.launchpad.net/inkscape/+bug/627134)
A fix have already been commited to the release 0.48.1
In another forum the guy turned off the ruler bar, which is a temporary solution if you can live without it for a while.

---

### Post by BobSongs on 2011-02-13
Right. And the website stated, as of January 5, 2011:

[QUOTE=Inkscape.org]We hope you had a great holiday season. Now that you are back, we have some news for you.

  We had a server error that prevented us from posting anything most of  December, but now it's fixed and we are back on track. The usual news  posting resumes, and the website now also has an initial [Books]("http://inkscape.org/books/index.php") section. In fact there is a whole new website coming, based on [design]("http://duckgoesoink.deviantart.com/art/Inkscape-org-redesign-188788814") by Hinerangi Courtenay.

The other good news is that 0.48.1 is done, and we are waiting for  Ted to cut the release so that packagers could start packaging. We are  also determined to make at least one more point release before it's time  for 0.49. Stay tuned for more news![/QUOTE]
So, now it's a matter of waiting for 0.48.1 to be released.

---

### Post by ratcat on 2011-02-16
Also with bad rulers on Windows 7 64 bit, Ubuntu 10.10.  I don't know what inkscape does, drawing tools spastic or something. CS 5 Illustrator user here.  Gimp seems to work well.

---

### Post by BobSongs on 2011-02-24
Let the banners fly!

Let the bells ring out!

Inkscape released a repaired version of 0.48.0 r9654 today. And in the system updates! Update your system and say bye bye to those smudgy ruler bars.

:popcorn:

I was so used to the black smears that now Inkscape looks a little odd without them. Meh, in three days I'll forget they were ever there.

Cheers, folks! This thread is now done!

---


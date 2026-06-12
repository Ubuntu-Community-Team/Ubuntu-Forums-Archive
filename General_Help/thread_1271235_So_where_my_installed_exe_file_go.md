---
title: "So where my installed exe file go?"
date: 2009-09-20
forum: General Help
---

### Post by sandsb on 2009-09-20
New to unbuntu, running the new version - jaunty jackalope or whatever it's called.  Installed Wine and tried installing itunes.  Install looked OK but I can't find the app to start it.  Where do installed apps go?  The default installs under windows putsthings under c:\program files.   Where does ubuntu put things?

---

### Post by darkstaar on 2009-09-20
Should be under Applications > Wine > Programs

That said, I don't believe that ITunes will actually run on WINE.

---

### Post by Hosmion on 2009-09-20
iTunes cannot be used on Linux because it is only available on Windows and Mac.

[IMG]http://i36.tinypic.com/29z7gua.jpg[/IMG]

**Free for Mac + PC**

---

### Post by NoaHall on 2009-09-20
Get songbird instead.

---

### Post by Hosmion on 2009-09-20
> **NoaHall said:**
> Get songbird instead.
Free music?

---

### Post by NoaHall on 2009-09-20
[http://www.getsongbird.com/](http://www.getsongbird.com/)

Songbird looks almost exactly like iTunes, but runs better.

---

### Post by CatKiller on 2009-09-21
> **sandsb said:**
>  Where do installed apps go?  The default installs under windows putsthings under c:\program files.   Where does ubuntu put things?

It's not a question of where [Ubuntu puts things]("http://en.wikipedia.org/wiki/Filesystem_hierarchy_standard"). It's a question of where those Windows installers put things. Which is exactly where they would put them on Windows. You can run ```
wine "C:\Program Files\Stupidly\Long\Path\That\Includes\Everyone\That\Had\A\Say\In\The\Application\Program Name\programname.exe"
``` perfectly well.

By default, Wine presents ~/.wine/drive_c as the "C:" drive to Windows applications (although this can be changed) so all of that "C:\Program Files" nonsense will be in there.

---

### Post by 3rdalbum on 2009-09-21
Ubuntu already comes with a music manager: Rhythmbox.

ALWAYS look for native Linux programs before trying to run your Windows programs in Wine, otherwise you might as well just be using Windows. Windows is a better Windows than Linux can ever be.

There are literally hundreds of music players for Linux, so I *know* you haven't tried them all.

---


---
title: "an unneeded entry in Burg"
date: 2011-01-01
forum: General Help
---

### Post by jvacek996 on 2011-01-01
I'm trying to minimize my burg entry options to minimum, and I happen to have an entry for Vista, which was earlier on replaced with W7 and that is now dualbooted with Ubuntu.
BUT, the entry for Vista isn't quite gone, and whenever I just go ahead and try to boot into it, it gives me a "windows is loading files" bar and the bar never finishes because the files aren't at the /dev/sda3 where they should be, but that partition is a "HP_RECOVERY" thing, which I am not very happy with deleting, since i have no idea what is in there, and what might happen if I ever need them and they're gone.

The file I'm more or less the most anxious about about is a file in "/media/HP_RECOVERY/system.sav/util" and the name of it is HPFactory.wim, it's 6.2 gigabytes large. I guess it's some kind of factory settings or something but I have no idea whether i will actually ever use it or not, coz when something goes fatal wrong i either re-install the whole machine or I just pop in the Ubuntu cd and get a working terminal from there.

So my question is whether there is a way to just delete the entry line from somewhere which refers to the vista thing or anything simple like that which doesn't involve erasing the whole partition with all of it's files.
It doesn't really prevent me from booting or anything, so it doesn't really matter that much if there will not be an easy solution, but it's nice to get rid of it.

Sorry for the essay, thanks a lot for helping me!

---

### Post by jvacek996 on 2011-01-01
A quick update, i actually waited a bit longer while trying to boot into it, and it looks like it is a windows system running only on one app, and that is an HP Recovery tool. the thing would basically restore my hard disk into factory settings blah blah.
So now I don't really know whether to get rid of it or not, coz it might come in handy sooner or later, but I don't know when. But because it is only 9 Gigs big it's ok if I leave it there.

The real question now is whether I can just hide it from burg, and if I ever need it to show it as well again, or just change the OS Class to something different so i don't accidentaly end up formatting my whole shizzle.
But How?

---

### Post by stinkeye on 2011-01-01
Have a look at grub-customizer.
If burg is installed it will give you the option to configure burg.
[**_[COLOR="DarkRed"]http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html[/COLOR]_**]("http://www.webupd8.org/2010/11/grub-customizer-20-can-change-default.html")

---


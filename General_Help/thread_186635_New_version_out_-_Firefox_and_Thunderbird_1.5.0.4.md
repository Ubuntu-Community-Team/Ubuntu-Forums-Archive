---
title: "New version out - Firefox and Thunderbird 1.5.0.4"
date: 2006-06-02
forum: General Help
---

### Post by Svanteson on 2006-06-02
Hi!

Today a new version of Firefox and Thunderbird were released. It contains a few security bug fixes.
How should we install the update? Wait for it to be available in the repository or use the built in updater?

BR/Nicklas

---

### Post by bollix47 on 2006-06-02
I updated using the internal updater.

gksudo firefox

gksudo mozilla-thunderbird

Both worked with no problems.

---

### Post by Svanteson on 2006-06-02
Ok, is using the internal updater likely to cause problems later when (if?) the update gets available from the repository?

/Nicklas

---

### Post by bollix47 on 2006-06-02
It hasn't caused me any problems in the past.

When firefox updates and it restarts it shows a different home page but pressing alt-Home will return you to your own home page(s).

When thunderbird updates it tries to create a new profile where I just clicked on cancel and exit.  It did this after the restart too but I followed the same procedure then closed and restarted normally and everything was fine.

---

### Post by cywhale on 2006-06-02
Updated two times using the firefox update service and every time after the update
- my bookmarks were gone (could not find it any more on my /hda)
- tab mix plus options were set back to default
- url-click bhaviour was set back to default

Maybe I should use apt to update firefox next time but could not resist...

---

### Post by FredB on 2006-06-02
[QUOTE=cywhale]Updated two times using the firefox update service and every time after the update
- my bookmarks were gone (could not find it any more on my /hda)
- tab mix plus options were set back to default
- url-click bhaviour was set back to default

Maybe I should use apt to update firefox next time but could not resist...[/QUOTE]

Erh... I have an old bookmarks file, which was made around one year ago, when firefox 1.5 was being made... And as I update every day my development version of firefox, I have not see those kind of problem...

Weird ;)

---

### Post by slimdog360 on 2006-06-02
[QUOTE=bollix47]I updated using the internal updater.

gksudo firefox

gksudo mozilla-thunderbird

Both worked with no problems.[/QUOTE]
err okay, how was that again?
when I use gksudo firefox all that happens is a new firefox window comes up. No updating or anything.

---

### Post by Colonel Kilkenny on 2006-06-02
Same for me. Nothing happens. Update isn't working.
Tried also with gksudo firefox -S but nothing.

Again I know why I use Opera and Epiphany. That thing called firefox just isn't for me.

---

### Post by PriceChild on 2006-06-02
Then open it with gksudo, and go to help->updates


edit

That didn't actually work for me.... :s

To a previous poster... i reccomend using "ownarea" by glaxstar.com to remotely store all your bookmarks and some settings so you'll never lose them! Free too.

---

### Post by Colonel Kilkenny on 2006-06-02
[QUOTE=PriceChild]Then open it with gksudo, and go to help->updates[/QUOTE]
Well, I would do that if that Check updates wouldn't be grayed out. It can't be clicked.

---

### Post by jobezone on 2006-06-02
Firefox people could start providing more than just a tar.gz file, like .deb's and .rpm's , don't you all agree?

---

### Post by mannheim on 2006-06-02
Best to just wait for the repositories to pick it up. In the past, security updates to Firefox have made their way into the repositories before too long. Let the whole debian/ubuntu system do its thing.

---

### Post by bollix47 on 2006-06-02
[QUOTE=slimdog360]err okay, how was that again?
when I use gksudo firefox all that happens is a new firefox window comes up. No updating or anything.[/QUOTE]

Okay the steps that worked for me are as follows:

1. close any instances of Firefox
2. open a run dialogue (alt-F2) and type
3. gksudo firefox
4. click on help and then "Check for updates"
5. click on install
6. Firefox will restart
7. Homepage will be different that usual 
8. alt-Home to return to usual homepage
9. done

substitue mozilla-thunderbird for firefox in above instructions and other that clicking on cancel and exit a couple times it too works on my setup which was a standard install using synaptic (so no need for manually installing any deb or gz files)

---

### Post by jobezone on 2006-06-02
[QUOTE=mannheim]Best to just wait for the repositories to pick it up. In the past, security updates to Firefox have made their way into the repositories before too long. Let the whole debian/ubuntu system do its thing.[/QUOTE]
Yep, I agree.

---

### Post by OPaul on 2006-06-02
Thunderbird is still at 1.5.0.2 in the repositories. If .3 didn't get posted, will .4?

---

### Post by mannheim on 2006-06-02
I'm not sure there was a Thunderbird 1.5.0.3; or if there was, it was not a security update. For example, the link [here]("http://www.mozilla.org/projects/security/known-vulnerabilities.html#thunderbird1.5.0.4")
about security updates makes no mention of Tbird 1.5.0.3

---

### Post by OPaul on 2006-06-02
> **mannheim]I'm not sure there was a Thunderbird 1.5.0.3 said:**
> here[/URL]
about security updates makes no mention of Tbird 1.5.0.3
Ah, perhaps they skipped it to keep the numbering between Firefox and Thunderbird parallel.

---

### Post by zhoux on 2006-06-02
[quote=bollix47]Okay the steps that worked for me are as follows:

1. close any instances of Firefox
2. open a run dialogue (alt-F2) and type
3. gksudo firefox
4. click on help and then "Check for updates"
5. click on install
6. Firefox will restart
7. Homepage will be different that usual 
8. alt-Home to return to usual homepage
9. done

substitue mozilla-thunderbird for firefox in above instructions and other that clicking on cancel and exit a couple times it too works on my setup which was a standard install using synaptic (so no need for manually installing any deb or gz files)[/quote]

I'm having trouble upgrading through the internel updater.  No matter which user i use or which "mode" i'm in, the "Check Update" is grayed out.  I was surprised when it didn't even work for gksu/sudo/root.  

Could anyone help me?

---

### Post by ubuntoy on 2006-06-02
Firefox auto install plugin for Micromedia Flash...... failed
anyone has the same bug?

---

### Post by Anduu on 2006-06-02
Hmmm...

Updated Firefox just fine.Thunderbird says no updates available.Still at version 1.5.0.2 :-k

---

### Post by Anduu on 2006-06-03
[QUOTE=ubuntoy]Firefox auto install plugin for Micromedia Flash...... failed
anyone has the same bug?[/QUOTE]

AFAIK this has never worked.You must install flash via the method described here:

[https://wiki.ubuntu.com/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b](https://wiki.ubuntu.com/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b)

---


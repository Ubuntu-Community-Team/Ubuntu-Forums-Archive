---
title: "Looks like KDE 3.5.2 is out! ;-)"
date: 2006-03-26
forum: General Help
---

### Post by nuzzy on 2006-03-26
[http://planet.ubuntulinux.org/](http://planet.ubuntulinux.org/)

---

### Post by Barrakketh on 2006-03-26
dist-upgrading now :D

---

### Post by Bukunut on 2006-03-26
OH.. thanks Nuzzy... Nice one!

Bukunut.

---

### Post by Mathias-K on 2006-03-27
Thanks for the news :)

---

### Post by Bukunut on 2006-03-27
Anyone had depency isssues with the update?
[I]
the following packages have unmet dependencies:
  kde-i18n-engb: Depends: kdelibs4c2a (>= 4:3.5.2) but it is not installable
E: Broken packages[/I] ?

Bukunut.

---

### Post by Barrakketh on 2006-03-27
[QUOTE=Bukunut]Anyone had depency isssues with the update?
[I]
the following packages have unmet dependencies:
  kde-i18n-engb: Depends: kdelibs4c2a (>= 4:3.5.2) but it is not installable
E: Broken packages[/I] ?

Bukunut.[/QUOTE]
No.  Mine went through without a hitch.  And the file is physically present on the server in [http://kubuntu.org/packages/kde352/pool-dapper/kdelibs/](http://kubuntu.org/packages/kde352/pool-dapper/kdelibs/) (I wouldn't install that manually though ;) )

---

### Post by Bukunut on 2006-03-27
Barrakketh

Yeah.. seems to be a breezy thing then. :-(
bukunut

---

### Post by imranj on 2006-03-27
Well where are the reps for, Breezy eh?

Will adding a rep of drapper is safe and it wont hose my system aaiii?

---

### Post by Bukunut on 2006-03-27
imranj

The release from Planet Ubuntu said:-

"Jonathan Riddell has packaged it and put on kubuntu.org for both Breezy and Dapper"

so change the names dapper to breezy.

Bukunut.

---

### Post by imranj on 2006-03-27
deb [http://kubuntu.org/packages/kde352](http://kubuntu.org/packages/kde352) breezy main
deb-src [http://kubuntu.org/packages/kde352](http://kubuntu.org/packages/kde352) breezy main


sudo kedit /etc/apt/sources.list

add these lines for breezy & to your sources.list, run `sudo apt-get update && sudo apt-get dist-upgrade` and restart KDE.

---

### Post by njf on 2006-03-27
[QUOTE=imranj]deb [http://kubuntu.org/packages/kde352](http://kubuntu.org/packages/kde352) breezy main
deb-src [http://kubuntu.org/packages/kde352](http://kubuntu.org/packages/kde352) breezy main


sudo kedit /etc/apt/sources.list

add these lines for breezy & to your sources.list, run `sudo apt-get update && sudo apt-get dist-upgrade` and restart KDE.[/QUOTE]

Is apt-get dist-upgrade really needed? I used apt-get upgrade and it worked fine.

---

### Post by zi99y on 2006-03-27
Ok cool, but what's been fixed/updated in this version, the kde site doesn't even mention it ([http://www.kde.org/](http://www.kde.org/)) is it official?

I'll probably give it a go when I get home, can someone on breezy confirm it's working ok?

---

### Post by davtaine on 2006-03-27
I just updated to kde 3.5.2 breezy and now i got no "monitor" on system settings... so how i can get it back? any idea? resolution hurts my eyes right now :-k

---

### Post by Barrakketh on 2006-03-27
It's called Display.

---

### Post by zi99y on 2006-03-27
Well I upgraded.... can't see any difference yet, is there a changelog?!

Still not fixed that bl**dy annoying buy in konqueror where the icon view always reverts back if you go to system:/

---

### Post by nuzzy on 2006-03-27
One thing that was pointed out was that the icons down in the lower right part of the panel are now stacked on top of one another

---

### Post by Jvaldezjr on 2006-03-27
I followed the instructions posted by **imranj** and it installed with no problems.  I used dist-upgrade.  The only thing I noticed is that kmail is being held back, but I dont know why.

---

### Post by stoeptegel on 2006-03-27
All went smooth here with dist-upgrading under dapper/xgl&compiz.

---

### Post by Randomskk on 2006-03-27
Mine upgraded smoothly, although I'm not entirely sure what the changes are. Only difference I see is in the "about KDE" dialogue.

---

### Post by Barrakketh on 2006-03-27
[QUOTE=Randomskk]Mine upgraded smoothly, although I'm not entirely sure what the changes are. Only difference I see is in the "about KDE" dialogue.[/QUOTE]
It's a bug fix release, and I'm rather sure we won't get a changelog until it's officially released.  Notice how the post said it's "(almost) out".  :)

---

### Post by stoeptegel on 2006-03-27
[QUOTE=Barrakketh]It's a bug fix release, and I'm rather sure we won't get a changelog until it's officially released.  Notice how the post said it's "(almost) out".  :)[/QUOTE]


Well, one thing that is fixed is the "dragging a box around icons/files". This was shocking in 3.5.1, now smooth :)

---

### Post by Kosmonaut on 2006-03-27
> It's a bug fix release, and I'm rather sure we won't get a changelog until it's officially released. Notice how the post said it's "(almost) out". 
Try this!
**Changelog**
[http://kde.org/announcements/changelogs/changelog3_5_1to3_5_2.php](http://kde.org/announcements/changelogs/changelog3_5_1to3_5_2.php)

---

### Post by livingtarget on 2006-03-27
Excellent news, will try this out on dapper straight away. :KS

EDIT: Hah, KDE locked up on me straight away after reboot, had to log-out and in again. That's the first time i've seen that. I hope it'll happen again so I know what might cause it, but I doubt it'll happen again that easily.

---

### Post by z-vet on 2006-03-27
[QUOTE=Bukunut]Anyone had depency isssues with the update?
[I]
the following packages have unmet dependencies:
  kde-i18n-engb: Depends: kdelibs4c2a (>= 4:3.5.2) but it is not installable
E: Broken packages[/I] ?

Bukunut.[/QUOTE]
Yes, i have the same issue with kde-i18n-ru.

---

### Post by zi99y on 2006-03-28
[QUOTE=livingtarget]Excellent news, will try this out on dapper straight away. :KS

EDIT: Hah, KDE locked up on me straight away after reboot, had to log-out and in again. That's the first time i've seen that. I hope it'll happen again so I know what might cause it, but I doubt it'll happen again that easily.[/QUOTE]

That's exactly what happened to me, although a reboot and another apt-get upgrade worked fine

---

### Post by Asraniel on 2006-03-28
were is the changelog??

---

### Post by Barrakketh on 2006-03-28
[QUOTE=Asraniel]were is the changelog??[/QUOTE]
Look at Kosmonaut's post...he gave us the link.

---

### Post by Asraniel on 2006-03-28
should we report bugs in this on bugs.kde.org or in the ubuntu bugzilla?

Or is it normal that i have two search boxes in konqueror? you know, the google search bar on the top right. just that i have 2 of them now

---

### Post by Bukunut on 2006-03-28
Asraniel

Blimey! Hadn't noticed that one. :-k Same here..

Bukunut.

---

### Post by Kosmonaut on 2006-03-28
Got the same problem with the Konqueror. And btw Kopete is not stable at all. It crashes when I´m trying to change its settings, and everytime I try to configure the video-device it crashes to.  This 3.5.2 Bug-Fix-Update needs to be bug fixed, I guess:-k. But we still have time to report all these bugs, before the "draper" can fly. right?

---

### Post by Asraniel on 2006-03-28
well, but where do we report them? are those upstream bugs? i think so. but its also important that kubuntu knows about, so we put them in both bugtrackers?

---

### Post by niviche on 2006-03-28
I upgraded from 3.5.1 to 3.5.2 on Breezy, and everything ran perfectly.

And judging from the Changelog, this new version is more than a minor bugfix one:

```

Sometimes KAddressBook lost all data. This is now fixed.

```

Urgh. :-|

---

### Post by njf on 2006-03-28
[QUOTE=Asraniel]should we report bugs in this on bugs.kde.org or in the ubuntu bugzilla?

Or is it normal that i have two search boxes in konqueror? you know, the google search bar on the top right. just that i have 2 of them now[/QUOTE]

Goto "Configure Extensions..." =>" Extensions" tab, untick one of them.

---

### Post by trotski on 2006-03-28
I kept the Google Suggest extension.  I've always felt it to be rather nifty.  Maybe not all that useful, but still...

The only issue I can find so far is the (already mentioned above) lack of monitor resolution control.  I don't need it, but it is missing.  Did we always have the zeroconf configuration option in System Settings?  It would be neat to get that stuff working out of the box.

---

### Post by magnusbb on 2006-03-28
I've been using a lot of KDE 3.5.2 applications in my mixed GNOME/KDE environment. Konqueror is a far better experience now, and a lot of annoying JavaScript errors are improved.

A whole better experience... so far, that is!

---

### Post by nykobing on 2006-03-28
[QUOTE=davtaine]I just updated to kde 3.5.2 breezy and now i got no "monitor" on system settings... so how i can get it back? any idea? resolution hurts my eyes right now :-k[/QUOTE]


I am having the same problem, before I could change when the montior would turn off, go to sleep - it was under Peripherals in kcontrol. It has totally disappreared for me. Any idea how I can get this back or atr least change the time for my montior to turn itself off if it is not being used?

---

### Post by trotski on 2006-03-28
Ah, the wonders of being on that bleeding edge!  I guess we'll just have to wait for a further update.

---

### Post by ltmon on 2006-03-29
I don't suppose anyone has figured out how to make the system tray behave as it used to (i.e. all on one line).  I'm not sure I like the new multiple line look.

L.

---

### Post by njf on 2006-03-29
[QUOTE=ltmon]I don't suppose anyone has figured out how to make the system tray behave as it used to (i.e. all on one line).  I'm not sure I like the new multiple line look.

L.[/QUOTE]

If you want the single line tray back (like me), right click on the panel and click "Configure Panel...". Choose "Arrangement" tab on the left, and set the "Size" to "Custom" in the combobox. Then, choose 43 pixels.

---

### Post by nuzzy on 2006-03-29
FWIW - It looks like 3.5.2 is now in the main repos...you can get rid of those two lines in sources.list. :)

---

### Post by stoeptegel on 2006-03-29
[QUOTE=Asraniel]should we report bugs in this on bugs.kde.org or in the ubuntu bugzilla?

Or is it normal that i have two search boxes in konqueror? you know, the google search bar on the top right. just that i have 2 of them now[/QUOTE]

I don't have that problem here, but yes please report as much info as you can. Since three people has the problem it's not a coincidence anymore, so they *have* to know what's going on.

---

### Post by lex1 on 2006-03-29
what should I add to my sources list if I have not as yet installed KDE but want the whole show how to from scratch. have bb5-10 gnome.

lex1:p

---

### Post by tlindner on 2006-03-29
[QUOTE=stoeptegel]All went smooth here with dist-upgrading under dapper/xgl&compiz.[/QUOTE]

Do you use kde-window-decorator???  Isn't it flat out broken?

---

### Post by stoeptegel on 2006-03-29
[QUOTE=tlindner]Do you use kde-window-decorator???  Isn't it flat out broken?[/QUOTE]

Honestly i must say i don't know what kde-window-decorator is. Is that kwin? If yes, then no that doesn't work yet(i can use it, but then whole the xgl is gone). This gui is really Gnome stylish as of now and personally i have nothing against that, although i think kwin is prettier.

---

### Post by DevilInPgh on 2006-03-29
There is a difference between the Breezy and Dapper versions of 3.5.2, just as there is a difference between the Breezy and Dapper versions of 3.5.1.  The Breezy version depends on the kdelibs4c2 library and associated libraries ending in *c2, whereas the Dapper version depends on the kdelibs4c2a library and associated libraries ending in *c2a.  I noticed this problem when I upgraded from Breezy to Dapper, especially when I was frustrated with not being able to install the newer programs depending on kdelibs4c2a.  Every package broke and had to be uninstalled along with kdelibs4c2 before installing kdelibs4c2a and reinstalling every single package (luckily, settings like bookmarks and RSS feeds were not lost).  I already posted a thread about this in the Dapper subforum, although I have not received any responses regarding that.  So for Breezy users, install the Breezy version of 3.5.2 for now, but if you want to feel a little adventurous (and have lots of sitting-around time and/or use your Linux box as a toy), upgrade to Dapper and use the Dapper version of 3.5.2.

---

### Post by davebgimp on 2006-03-29
I notice that having just upgraded to 3.5.2 that Kopete now has big problems for me.
It will not connect to MSN, though it did fine prior to updating and any clicking on 'Configure Kopete' causes the program to immediately crash. :(

---

### Post by debernardis on 2006-03-29
After upgrading from kde 3.5.1 to 3.5.2 my system lost the ability to open a **bluetooth:/** url. Kde complains of an *undefined url* error.

I still can access my phone's file system by ```
obex://[00:0e:ed:ae:d7:3b]:11/
``` so the problems is not extended to all the bluetooth management.

I filed a bug to bugs.kde.org

In the meantime, if others have the same problem, they could try to use the obex:// construct like above, putting the bluetooth address of their device inside square braces instead of mine.

---

### Post by emptycs on 2006-03-30
Whats is KDE?

---

### Post by Asraniel on 2006-03-30
anyone else has the problem that the bar on the bottom right with all those littles symbols is not right? the icons on the second line are cut of, 2-3 pixels are lost i think

---

### Post by Adrian on 2006-03-30
[QUOTE=emptycs]Whats is KDE?[/QUOTE]

[http://www.kde.org/](http://www.kde.org/)
[http://opensourceversus.com/modules.php?op=modload&name=News&file=article&sid=447&mode=thread&order=0&thold=0](http://opensourceversus.com/modules.php?op=modload&name=News&file=article&sid=447&mode=thread&order=0&thold=0)

---

### Post by MamiyaOtaru on 2006-03-30
[QUOTE=Asraniel]well, but where do we report them? are those upstream bugs? i think so. but its also important that kubuntu knows about, so we put them in both bugtrackers?[/QUOTE]

It's been a while since I had and fixed this bug, so I can't recall exactly what I did, but I can explain the procedure.  

Start off with a *locate: google* in konqueror.  Watch for a pair of results in the same directory with very similar names (google_toolbar and google_suggest_toolbar, something like that).  I found a pair of suspiciously familiar results.  Using packages.ubuntu.com I discovered one of them was in a package currently in the archive, one was not.  I deleted the one that was not, and bingo, one search field.

I suspect the one that was not in a package was at some point, and that it wasn't removed when that package was upgraded to no longer include it.  I suspect that one release of the package had the alternate name before it was reverted, and the alternate files were not released, causing two identical search fields.

IIRC I installed flight3 then upgraded from there (this was all in Dapper, but it could be something similar here).  Sorry I can't be more direct; without the duplicate hanging around anymore, it's hard for me to find it again ;)

---

### Post by f1dave on 2006-03-30
[QUOTE=MamiyaOtaru]I found a pair of suspiciously familiar results.  Using packages.ubuntu.com I discovered one of them was in a package currently in the archive, one was not.  I deleted the one that was not, and bingo, one search field.[/QUOTE]

Want to tell us which one? :P

---

### Post by shizow on 2006-03-30
how do i change the resolution in 3.5.2 at all?

---

### Post by f1dave on 2006-03-30
While they fix the bug, you could try using ctrl-alt-"+" and ctrl-alt-"-" to swap the resolutions listed in /etc/X11/xorg.conf

---

### Post by jeremy on 2006-03-31
[QUOTE=shizow]how do i change the resolution in 3.5.2 at all?[/QUOTE]
That seems to have disappeared, along with the monitors power saving options when you right click the desktop and chose; configure desktop...

---

### Post by shizow on 2006-03-31
[QUOTE=f1dave]While they fix the bug, you could try using ctrl-alt-"+" and ctrl-alt-"-" to swap the resolutions listed in /etc/X11/xorg.conf[/QUOTE]

pressing ctrl-alt-"+" and ctrl-alt-"-", i have two resolutions listed!

---


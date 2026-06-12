---
title: "KDE Marble - Open source Google Earth - outdated version in repo?"
date: 2011-05-14
forum: General Help
---

### Post by Redsandro on 2011-05-14
Hi all,

There's this wonderful geographical map program from KDE called [Marble]("http://edu.kde.org/marble/"), it will display high detail maps from [OpenStreetMaps]("http://www.openstreetmap.org/"), calculate navigation instructions etc. making it sort of the open source variant of Google Earth/Maps.

I've downloaded **version 1.0.1** for my Debian based mobile phone Nokia N900 and it allows me to record my route when I make a cycling tour. I can export this route, import it in the desktop version and check it out, save a picture and what not.

I tried this out on a way old laptop running 12 year old Windows XP. It installed **Marble 1.0.0**. Now I ofcourse want this to run on my newer Ubuntu 10.04 LTS laptop, but via the repositories I can only find **Marble 0.9**, an outdated version which does not do any of the useful stuff like route import or navigation calculation.

This OS is only 1 year old. Am I doing something wrong? How can I get the newer version of Marble? It's at **1.1.0** on the website.

[SIZE="1"]-edit-[/SIZE]

Heh, if all else fails I can try the newer Windows version through Wine, but come on the program is originally a Linux program, I must be doing something wrong, right? :)

[img]http://www.kde.org/images/screenshots/marble.png[/img]

[img]http://www.linuxjournal.com/files/linuxjournal.com/linuxjournal/articles/103/10365/10365f13.jpg[/img]

---

### Post by PaulW2U on 2011-05-14
> **Redsandro said:**
> This OS is only 1 year old. Am I doing something wrong? How can I get the newer version of Marble? It's at **1.1.0** on the website.


You're not doing anything wrong, that's the way it works with Ubuntu. Bugs will be fixed but new versions won't be added to an existing release. I'm running Kubuntu 11.04 with KDE 4.6.3 and have just downloaded version 1.0.2 of Marble.

I can't see a way of getting version 1.1.0 at the moment. :(

---

### Post by Redsandro on 2011-05-14
What? Software stays the same version as it was on release of the distro? :(
I thought only real important stuff like kernel and drivers were updated conservatively.

Oh that's why some of my other software is so 'old', it's because I'm running LTS? Hmm..

Well, there must be a PPA right? Like the Wine PPA, add it to your sources.list and you keep getting updates.

---

### Post by PaulW2U on 2011-05-14
> **Redsandro said:**
> Well, there must be a PPA right? Like the Wine PPA, add it to your sources.list and you keep getting updates.

[http://www.ubuntuupdates.org/marble](http://www.ubuntuupdates.org/marble) implies that the latest version of marble available to Ubuntu/KDE users is that which comes with KDE 4.6.3, which is what I have. I found a post on the KDE forum that implied version 1.1.0 was issued "outside of KDE" but the search facility seems to have stopped working so I can't provide a link to it.

---

### Post by Redsandro on 2011-05-14
I use Gnome and just let the package manager figure out what Qt libraries I need for KDE applications. But I guess there's also a restriction on the version of Qt because of Lucid.

I'm trying to find a .deb package, even if it's for a newer Ubuntu, just see what happens. But like you said, they keep everything well hidden.

I am still in shock though that 'policy' prevents me from getting software versions equal or newer than the ones I can get for ancient Windows. Should I really upgrade to non-LTS just to keep up? It kind of defeats the LTS purpose if it means being stuck.

---


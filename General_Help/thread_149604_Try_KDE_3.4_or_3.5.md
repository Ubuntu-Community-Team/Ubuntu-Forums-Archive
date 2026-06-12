---
title: "Try KDE 3.4 or 3.5 ?"
date: 2006-03-24
forum: General Help
---

### Post by njf on 2006-03-24
Whenever people want to try Kubuntu, we often tell them to install kubuntu-desktop or try the live/install CD. They most likely deal with Breezy stock KDE (3.4) when they first try it. 
What I am thinking is that why don't we tell them to use KDE 3.5.1 instead (i.e. install the kubuntu-desktop from the extra repo)? 

My experience is that KDE 3.5(and .1) has been more pleasing than when I first tried KDE 3.4 (mostly because of the bouncing-icon-but-nothing-come-out bug that was fixed since 3.5).

What do you think? Which version works better for you? The first impression is very important. Should we tell the newcomer to try KDE 3.4 or 3.5 ?

---

### Post by Jucato on 2006-03-24
Well, KDE 3.5.1 definitely is better than 3.4.x which comes with the Kubuntu Breezy install. 

That being said, I would prefer telling people to install kubuntu-desktop first. It's the closest thing to a clean Kubuntu install, and only installs the packages that Kubuntu has included in its default install (whereas kdebase or kde-core installs more apps than are necessary). This would give them an idea of what Kubuntu is and what it includes. Also, it's the easiest to do, not to mention it will consume less disk space. I'm trying to see this in the perspective of someone new to Ubuntu/Linux.

You are right on one thing, though. It's much better to have KDE 3.5.1 as your first impression. But I started with KDE two months before 3.5 was released. It was more or less tolerable. :D

---

### Post by adie273 on 2006-03-24
Eye-candy wise, i'd say 3.5, just for the little extra touches over 3.4.

However, when I upgraded to 3.5, I found some certain stuff, such as keyboard layouts etc for internet and multimedia keyboards didn't work and yet it does in 3.4.

I know i'm not the only person to experience this, and the problem might be sorted now. But if it isn't, and you were trying to win someone over with KDE, then these little issues might not help and thats why 3.4 might be better.

But like i said, that might be sorted now, and if it is. i'd stand by my original answer. 3.5. Just coz of the minor differences over 3.4 :)

---

### Post by Jucato on 2006-03-24
3.5.1 fixes several bugs that are present or were not fixed in 3.5.
For example the Administrator Mode not working and a critical security patch (I think) for the Javascript interpreter engine.

I guess the new user wouldn't even realize what's not working in 3.5.1 that was working in 3.4 (your case) IF 3.5.1 was the first thing he used. (He wouldn't even know about 3.4 in this case). 

I'm not familiar with keyboard layouts and multimedia keys. My only theory is that somehow upgrading to 3.5.1 must have overwritten some config file. I'm not really sure, though.

---

### Post by adie273 on 2006-03-24
[QUOTE=Fenyx]3.5.1 fixes several bugs that are present or were not fixed in 3.5.
For example the Administrator Mode not working and a critical security patch (I think) for the Javascript interpreter engine.

I guess the new user wouldn't even realize what's not working in 3.5.1 that was working in 3.4 (your case) IF 3.5.1 was the first thing he used. (He wouldn't even know about 3.4 in this case).[/QUOTE]

Thats a good point actually, If they hadn't used 3.4 first, they wouldn't notice some of the differences yea. Well spotted. 

However if they meet the same problem I did, and there volume keys for example don't work on their Internet/Multimedia keyboard in KDE, and yet work flawlessly in Gnome. Its one fault that might bug some people. Albeit a small one right enough.

---

### Post by Jucato on 2006-03-24
This also might be a bug specific to people upgrading from 3.4.x. I'm not sure if it's present in a clean 3.5.1 install. Haven't had the guts to test doing a fresh server install + kde-core with 3.5.1 :D (also, I don't have a multimedia keyboard :D)

I'll have a look around bugs.kde.org. It might be there.

---

### Post by njf on 2006-03-24
[QUOTE=Fenyx]That being said, I would prefer telling people to install kubuntu-desktop first. It's the closest thing to a clean Kubuntu install, and only installs the packages that Kubuntu has included in its default install (whereas kdebase or kde-core installs more apps than are necessary). This would give them an idea of what Kubuntu is and what it includes. Also, it's the easiest to do, not to mention it will consume less disk space. I'm trying to see this in the perspective of someone new to Ubuntu/Linux.[/QUOTE]
My idea is that tell the people to add the KDE 3.5.1 repo to sources.list and install kubuntu-desktop. I checked the package, it doesn't specify which versions of its dependencies (not gstreamer0.8, since the version is appended to the package name), so whenever people install the package they will always get the latest version of the dependencies (that means kubuntu default settings + bleeding edge :D ).

---

### Post by Jucato on 2006-03-24
well, if the kubuntu-desktop metapackage does indeed only point to whatever KDE version is found in the repositories, then I guess it makes sense to update the repos to include KDE 3.5.1 before they install kubuntu-desktop. That would work, in theory. I just don't know how well it would work in practice. Anyone up for some testing? :D

Two ways to test if it will work:
1. Try to install on an existing Ubuntu install (backup first :D)
2. Do a server install, edit the sources.list to include KDE 3.5.1, then install kubuntu-desktop. This I can do only next week. It will be my install fest week :D

---


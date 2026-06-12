---
title: "Kde 3.5.3"
date: 2006-06-02
forum: General Help
---

### Post by Triton on 2006-06-02
anyone installed it yet?

---

### Post by Rackerz on 2006-06-02
It's on Kubuntu by default isn't it?

---

### Post by KubuntuKilledMe on 2006-06-02
I did. Lost my device icons on the desktop, just like it happened in the last 2 kde upgrades... :/

The solutions posted here to recover the device icons in the last time kde was upgraded dont work now, so i'm just waiting for some more people to install it and hopefully someone more knowledgeable than me will post a fix.

---

### Post by murph2481 on 2006-06-02
Nope by default the KDE on Kubuntu Dapper final release is 3.5.2

3.5.3 is a new release that fixes about 800 bugs and adds some functionality.  You can read more about it here: [http://desktoplinux.com/news/NS8426784059.html](http://desktoplinux.com/news/NS8426784059.html)

To get it you need to add this to your repos:
deb [http://kubuntu.org/packages/kde-353](http://kubuntu.org/packages/kde-353) dapper main

I have it running on both my desktop and laptop.  It runs smoothly and boots a lot faster (one of the fixes)  I would suggest upgradeing.  I do not have any device icons on the desktop so I haven't experienced the issue mentioned above.  When I plug in a usb drive the icon shows up on the desktop as it is supposed to.

---

### Post by barbarian on 2006-06-02
> anyone installed it yet?

I'm running right now.. first impressions - nothing is changed..

> t's on Kubuntu by default isn't it?

no it's on additional repos.

---

### Post by Evoreth on 2006-06-02
The startup time has been improved immensly. There are still too much bugs, though. :(

---

### Post by Triton on 2006-06-02
I took the plunge.  I installed it on a fresh install and had no issues.  the startup is alot faster.

---

### Post by eMuNiX on 2006-06-02
Have it installed on both the laptop and my main PC, faster startup is about the most noticeable thing.

---

### Post by AdrianVeidt on 2006-06-02
Another repo you could use is:

deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

That one will always grab the latest KDE regardless of what the numbering scheme is. Of course, you're going to update automatically if you do it this way, so be careful. You may install a new KDE when you don't want to.

---

### Post by msak007 on 2006-06-06
[QUOTE=KubuntuKilledMe]I did. Lost my device icons on the desktop, just like it happened in the last 2 kde upgrades... :/

The solutions posted here to recover the device icons in the last time kde was upgraded dont work now, so i'm just waiting for some more people to install it and hopefully someone more knowledgeable than me will post a fix.[/QUOTE]

I had the same problem, and found another post with someone who had a similar experience. The only "fix" I've found is to plug in a device (such as USB key or MP3 player) or insert a CD so that it gets mounted and puts an icon on the Desktop. All of the missing icons will come back, until you restart X or the comp again. What's the fix you're talking about (what post), and more importantly has anyone filed a bug report yet?

---

### Post by alvonsius on 2006-06-09
I did't get the desktop icon problem on my upgrade. But I get my KDM login screen don't showing border for input form for login, so it seems a rather bit ugly. Anyone with a cure?

---

### Post by dresnu on 2006-06-09
Could anyone who has already installed 3.5.3 tell if they are able to install package kdebase-dev? I had opened a thread about this 'cause after upgrading I get dependency problems with that package.

---

### Post by azarhal on 2006-06-09
Ubuntu dapper don't have kdebase-dev for kde 3.5.3... I'm trying to install it too. :(

But Debian have a version for it[ here]("http://packages.debian.org/unstable/devel/kdebase-dev").  
So I suppose somebody more techie, could make us a nice little package for Ubuntu/Kubuntu. 

yes/no?

---

### Post by Video Toaster on 2006-06-09
[QUOTE=alvonsius]I did't get the desktop icon problem on my upgrade. But I get my KDM login screen don't showing border for input form for login, so it seems a rather bit ugly. Anyone with a cure?[/QUOTE]
Same thing for me, on two different machines.  I agree that it's kind of ugly...

---

### Post by NetMatrix on 2006-06-09
I have decided to jump in head first.  Hope it doesn't hurt too bad.  Have you who have installed the new KDE been installing just the desktop or every available kde upgrade from the repositories?

I have installed everything that was listed as an upgrade.  I'll make a post after I am able to test it a little further.

---

### Post by NeoChaosX on 2006-06-09
That's funny, because I have a version 3.5.3 of kdebase-dev installed. You sure you guys that don't have the [KDE 3.5.3 repo](http://kubuntu.org/announcements/kde-353.php) added to your sources.list?

---

### Post by RavenOfOdin on 2006-06-10
I installed all upgrades for 3.5.3 a while ago. . .used a stop watch before and after, didn't see much of a speed difference in logon.

---

### Post by Arkady on 2006-06-10
[QUOTE=alvonsius]I did't get the desktop icon problem on my upgrade. But I get my KDM login screen don't showing border for input form for login, so it seems a rather bit ugly. Anyone with a cure?[/QUOTE]

Same problem here :(
The other problem is that the Kmenu icon on the panel has the little arrow centered, it's kinda ugly. 
[[IMG]http://img103.imageshack.us/img103/5389/arrow5lh.png[/IMG]](http://imageshack.us)

In previous version the arrow was usually on the left side.

---

### Post by dresnu on 2006-06-10
I too have kdm without borders and the appearing/disappearing centered kmenu arrow. These are not bugs or anything, it's just the way they decided to do it this time. If you ask me they are ugly [-(. Maybe there's some way of changing these through kdmrc and kickerrc under ~/.kde/share/config/.

@NeoChaosX: Yes I have one of those mirrors in my sources.list. Curious that somebody comfirmed this problem, though you don't have it... :-k

---

### Post by dresnu on 2006-06-10
Ok, solved the kdebase-dev issue. It was a dependency problem which probably apt-get couldn't resolve. I solved it using aptitude. If you ask it to install kdebase-dev it will have to uninstall alot of kde programs, so before proceeding write down which of these programs you need to reinstall.
I advise everyone to use aptitude instead of apt-get or even adept because it manages dependencies much better ;)

---

### Post by azarhal on 2006-06-10
[QUOTE=NeoChaosX]That's funny, because I have a version 3.5.3 of kdebase-dev installed. You sure you guys that don't have the [KDE 3.5.3 repo](http://kubuntu.org/announcements/kde-353.php) added to your sources.list?[/QUOTE]

Stupid  me, that was totally right. I changed my sources.list and forgot kde repo. Thanks.

---

### Post by alvonsius on 2006-06-10
[QUOTE=Arkady]Same problem here :(
The other problem is that the Kmenu icon on the panel has the little arrow centered, it's kinda ugly. 
[[IMG]http://img103.imageshack.us/img103/5389/arrow5lh.png[/IMG]](http://imageshack.us)

In previous version the arrow was usually on the left side.[/QUOTE]

Humm ... i just noticed that the arrow is dissapear and only appear on mouseover action. To be honest (except for the position of the arrow), it's nice (I've been searching some tips to get rid those arrows). Even nicer if there is no arrows at all there :mrgreen:

---

### Post by tsb on 2006-06-10
Me likes the mouseover arrow and the icon.  Mine's all blue though not white.

I hate the login screen without boxes though.

---

### Post by msak007 on 2006-06-11
I got the same problem with the login boxes not having any borders. I just noticed the arrow on the K menu icon now that you guys pointed it out, and yea it's only during a mouseover. I guess I can live with that, but seriously fix the Desktop icon issue and bring the borders back.

---


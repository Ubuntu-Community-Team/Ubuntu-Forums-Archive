---
title: "Missing iTunes"
date: 2006-02-21
forum: General Help
---

### Post by Maupertus on 2006-02-21
It's strange, but after using Ubuntu for a year now, the only thing I miss is a good replacement for iTunes.

I like Rhythmbox, but it's not really a comparison.
Beep-player is nice and simple, but it's more like winamp and I started using iTunes because of it's medialibrary. I don't like the winamp library.

Plus I like iTunes because of the ease to update my iPod.

It's a nagging detail in a perfect experience, I know that if I go over to KDE I could use Amarok, but I don't like KDE!

Am I being a nag or is there something out there to satisfy my desire.
It doesn't have to be a clone ofcourse, but it would be nice to have a kind of Rhythmbox with a few extra's.

---

### Post by z_diver on 2006-02-21
You don't really need KDE to run Amarok.  It may install a few extra libraries but nothing to worry about.  Off on a tangent but also dealing with music, mpd is very cool if you have a bunch of machines in the house and want to run all music off one central server.  gmpc is the gnome client for it.

---

### Post by RAOF on 2006-02-21
For something like Rhythmbox but with a few extras (iPod sync-ing support, automatic metadata searching, album-art), you could try the recent builds of Banshee.  I believe that you can get them (and the required dependencies) from the filefind.net repositories.

---

### Post by aysiu on 2006-02-21
I miss iTunes as well, but I've found the overall experience in Ubuntu is worth leaving Windows for (even if that means leaving iTunes behind as well). Unfortunately, it means I have to use AmaroK for listening, Goobox for ripping, Gtkpod for iPod integration, TagTool for tag editing (no, AmaroK cannot edit **every** tag). Fortunately, I have **global keyboard shortcuts**--something iTunes has never offered.

If you miss it so much, you can also try to run it through Crossover Office. [The version that runs iTunes is about US$40](http://www.codeweavers.com/store/?cat=cxof;view=prod-cxoffice-std-dl)

---

### Post by adrenaline on 2006-02-21
I feel ya bud.

Have you guys heard about Songbird?  Development is in the very early stages (not even available for linux yet) but it sure does look promising! :) 

[http://www.songbirdnest.com/home](http://www.songbirdnest.com/home)

Edit:  After searching the forums, I'd say you probably do know of it!  My bad.

---

### Post by Yokalosh on 2006-02-25
Just spent a whole day searching through different media players and testing them, came to the comclusion that the latest version of banshee is a perfect replacement for itunes

---

### Post by nerval on 2006-02-25
i didn't knew about banshee ...
damn this is good :)

---

### Post by Dargo on 2006-02-25
I still boot into windows every morning to sync my podcasts for my long commute to work.  I like the way it downloads new shows I haven't listened to and gets rid of ones I have automatically. 

Really, as sad as it is to have a whole partition devoted to one app, iTunes is the only reason I need to boot into Windows..

---

### Post by spahn on 2006-02-25
you might like streamtuner- it has a bigger library than itunes... \\:D/

---

### Post by RAOF on 2006-02-25
[QUOTE=Dargo]I still boot into windows every morning to sync my podcasts for my long commute to work.  I like the way it downloads new shows I haven't listened to and gets rid of ones I have automatically. 

Really, as sad as it is to have a whole partition devoted to one app, iTunes is the only reason I need to boot into Windows..[/QUOTE]
Just to pimp Banshee a bit more, it's getting a podcast plugin :)

---

### Post by just1m on 2006-02-25
I don't see why someone who has the knowledge wouldn't make a Linux port for Itunes concidering it's native to Unix, which both Linux and OSX are programmed in.

---

### Post by aysiu on 2006-02-25
[QUOTE=just1m]I don't see why someone who has the knowledge wouldn't make a Linux port for Itunes concidering it's native to Unix, which both Linux and OSX are programmed in.[/QUOTE] Isn't it closed source?

---

### Post by RAOF on 2006-02-25
[QUOTE=just1m]I don't see why someone who has the knowledge wouldn't make a Linux port for Itunes concidering it's native to Unix, which both Linux and OSX are programmed in.[/QUOTE]
If you can get the source code to iTunes I have no doubt that someone would very quickly have a linux port going.  That, however, is never going to happen - if Apple released the source of iTunes it would completely break the DRM of the iTMS (because the files downloaded don't actually have DRM - it's added later by iTunes).

And it would still be a lot of effort to do a port, even with the source code.  The fact that iTunes is written for a unix-like system doesn't really help.

---

### Post by just1m on 2006-02-25
Probably but the give the program away, if anything they'd just be expanding there market share.

---

### Post by Morbett on 2006-03-03
Banshee looks pretty solid and promising to me.  Would this sort of be GNOME's response to amaroK ?

---

### Post by Iandefor on 2006-03-04
FYI, Banshee 10.6 (latest) is in the Dapper repos.

---

### Post by AleXit on 2006-03-04
It's out a new version of libgpod (0.3.2)
[http://www.gtkpod.org/libgpod.html](http://www.gtkpod.org/libgpod.html)

---

### Post by Toxicity999 on 2006-03-04
Correct me if I'm wrong but I thought WINE handled iTunes pretty well (Only from what I've heard, I have no use for it so haven't tried.) I know it didnt handle the latest version but a few small releases back I think WINE took to.

---

### Post by CameronCalver on 2006-03-04
Can some1 plz put banshee on there next post so i can download it ?

---

### Post by RAOF on 2006-03-04
[QUOTE=Toxicity999]Correct me if I'm wrong but I thought WINE handled iTunes pretty well (Only from what I've heard, I have no use for it so haven't tried.) I know it didnt handle the latest version but a few small releases back I think WINE took to.[/QUOTE]
I've tried, and WINE doesn't handle iTunes.  At all.  You can't install it, and you can't run it without the ipod service running.  And I couldn't get the ipodservice running :(

The banshee site is [http://www.banshee-project.org](http://www.banshee-project.org)

You can get packaged versions of Banshee (and it's mono dependecies) from the filefind repositories: [apt.filefind.net](apt.filefind.net)

---

### Post by adamkane on 2006-04-23
You'll end up with dependency problems, if you use filefind. Warn of the pitfalls, if you're going to suggest something like filefind to new users.

aysiu:
Can you post some of the shortcut settings you use for amarok? The functionality seems limited in amarok, and I haven't figured it out. Next track, volume control would be useful.

---

### Post by aysiu on 2006-04-23
[QUOTE=adamkane]
aysiu:
Can you post some of the shortcut settings you use for amarok? The functionality seems limited in amarok, and I haven't figured it out. Next track, volume control would be useful.[/QUOTE] I use Win+Up for Play/Pause, Win+Down for Stop, Win+Right for next song, Win+Left for previous song, Win+O for show current song, Win+= for volume increase, and Win+- for volume decrease. These can all be defined in Configure Global Shortcuts.

---

### Post by RAOF on 2006-04-24
[QUOTE=adamkane]You'll end up with dependency problems, if you use filefind. Warn of the pitfalls, if you're going to suggest something like filefind to new users.
...[/QUOTE]
Oh, really?  Whoops!  I always build my own packages from CVS, and on Dapper, I just found that advice on the Banshee mailing list.  Useful to know in future :)

---

### Post by sinaen on 2006-09-06
> **Dargo said:**
> I still boot into windows every morning to sync my podcasts for my long commute to work.  I like the way it downloads new shows I haven't listened to and gets rid of ones I have automatically. 

Really, as sad as it is to have a whole partition devoted to one app, iTunes is the only reason I need to boot into Windows..

Itunes doesn't work with wine and ipod. and i have found an excellent ipodcast program juice it is named.
[http://juicereceiver.sourceforge.net/faq/index.php](http://juicereceiver.sourceforge.net/faq/index.php)

---


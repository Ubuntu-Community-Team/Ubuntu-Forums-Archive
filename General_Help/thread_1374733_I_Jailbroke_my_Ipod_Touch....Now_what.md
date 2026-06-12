---
title: "I Jailbroke my Ipod Touch....Now what?"
date: 2010-01-07
forum: General Help
---

### Post by Neezer on 2010-01-07
So I went through the process to jailbreak my ipod touch, but now i'm at a loss for what to do?? I have actually figured out how to use openssh to login to the ipod. It was pretty simple actually. I have used scp to send a test folder with music in it to the ipod touch....

I can't find the music.

there are other things that I want to do too. like change the black background. add other apps....but I'm not really sure how to go about doing that.

Any help out there?

---

### Post by cz8 on 2010-01-07
The thing you can do is to go to your cydia (if you jailbroke ur iphone properly), search an application called "winterboard", and install it. It allows you to change background pics as well as themes (you have download themes from Cydia). 
If you want free applications, "installous" is the Cydia app you should download, just go to Cydia and search for "installous".then install it, BAM!!! you got tons of free apps right after!!
There are tutorials on Youtube as well.
Hope it will help a little bit.

---

### Post by Chronon on 2010-01-07
You probably shouldn't advise people to pirate stuff on the forums.

---

### Post by Neezer on 2010-01-07
> **cz8 said:**
> The thing you can do is to go to your cydia (if you jailbroke ur iphone properly), search an application called "winterboard", and install it. It allows you to change background pics as well as themes (you have download themes from Cydia). 
If you want free applications, "installous" is the Cydia app you should download, just go to Cydia and search for "installous".then install it, BAM!!! you got tons of free apps right after!!
There are tutorials on Youtube as well.
Hope it will help a little bit.

Thanks....

I used scp to send a folder with mp3 files in it to /var/root/Media, but I have no Idea how to play that music on my ipod now...I can't find it when I go to music...I've tried restarting the ipod and restarting the music app....no luck.

---

### Post by Neezer on 2010-01-07
Also,

Where is my music that has been sync'd through itunes? I can't seem to find it when I'm using ssh to browse the file system...Also, where are the pictures that I have sync'd to it with itunes?

---

### Post by Chronon on 2010-01-07
Apple's music app only plays media that's listed in a properly generated iTunesDB.  You need to find yourself a 3rd party media player that is willing to simply play files from the internal storage.

---

### Post by Chronon on 2010-01-07
> **Neezer said:**
> Also,

Where is my music that has been sync'd through itunes? I can't seem to find it when I'm using ssh to browse the file system...Also, where are the pictures that I have sync'd to it with itunes?

I don't know.  All of this stuff gets hidden away in some obfuscated fashion.  It might be possible for a program to scan the metadata of all media files in the internal storage and create a searchable database from that.  You can't use a file browser to sensibly browse any media that's been synced by iTunes.

---

### Post by Neezer on 2010-01-07
> **Chronon said:**
> Apple's music app only plays media that's listed in a properly generated iTunesDB.  You need to find yourself a 3rd party media player that is willing to simply play files from the internal storage.

So basically I am going to have to have two different music players? sounds pretty straight forward...can you advise a certain one that works well? I am assuming that I would find it via cydia? Using Cydia isn't piracy is it?

---

### Post by zine92 on 2010-01-07
Anyway a note to you, about apps go google. Music wise, anyway in the newer itunes version and the ipod version, they encrypted the ipod
to make deleting and finding music difficult. Trust me, the music are group in different weird folders and the song name is even weirder. Anyway if you reall want to see it. heres how. either get ifile for your touch or use ssh and go into this folder. ```
/var/mobile/Media/iTunes_Control/Music
```

And don't say i didn't warn you.

---

### Post by Chronon on 2010-01-07
> **Neezer said:**
> So basically I am going to have to have two different music players? sounds pretty straight forward...can you advise a certain one that works well? I am assuming that I would find it via cydia? Using Cydia isn't piracy is it?

I haven't really bothered.  I think the Touch is kind of a crap music player and I prefer to use other players (ones that run Rockbox) for that purpose.  I only really use the Touch for apps. If someone could get Rockbox running on the Touch I would probably use that.

Cydia is just a package manager (a front-end for an apt system similar to what Ubuntu uses).  The nature of the packages that are available depends on what repositories you use.  Some stuff is pirated/cracked proprietary software (such as what you get from the installous app that the other poster mentioned).  You can also find pretty standard free software offerings (e.g. VLC).

---

### Post by Neezer on 2010-01-07
> **zine92 said:**
> Anyway a note to you, about apps go google. Music wise, anyway in the newer itunes version and the ipod version, they encrypted the ipod
to make deleting and finding music difficult. Trust me, the music are group in different weird folders and the song name is even weirder. Anyway if you reall want to see it. heres how. either get ifile for your touch or use ssh and go into this folder. ```
/var/mobile/Media/iTunes_Control/Music
```

And don't say i didn't warn you.

wow...that is absolutely crazy...thanks a lot apple. Thank goodness I don't have a large library from itunes...at least downloaded stuff...Since my switch over to ubuntu I have put all my cd's onto my laptop....I may just start over on the touch and jailbreak again with no music on it.

---

### Post by zine92 on 2010-01-07
> **Chronon said:**
> I haven't really bothered.  I think the Touch is kind of a crap music player and I prefer to use other players (ones that run Rockbox) for that purpose.  I only really use the Touch for apps. If someone could get Rockbox running on the Touch I would probably use that.

Cydia is just a package manager (a front-end for an apt system similar to what Ubuntu uses).  The nature of the packages that are available depends on what repositories you use.  Some stuff is pirated/cracked proprietary software (such as what you get from the installous app that the other poster mentioned).  You can also find pretty standard free software offerings (e.g. VLC).

I do agree that touch is kind of crappy. I jailbroke it but mainly to use theming features and yes cydia is not illegal. It is merely a app to fetch your repo and what more cydia host apps which may not get into the apps store which is not a bad thing after all and for people who maybe in terested in developing apps for the Iphone platform, Cydia the way to distribute it.

---

### Post by Neezer on 2010-01-07
Thanks for all of the speedy replies! I really appreciate the help...Winterboard is pretty sweet! 

Is there a way I can add my own pictures to the options for chosing a wallpaper?

---

### Post by Zorael on 2010-01-07
For what it's worth, if you add Paul McEnery's ppa ([ppa:mcenery/ppa](https://launchpad.net/~pmcenery/+archive/ppa)) you should be able to sync music over usb with Rhythmbox or gtkpod after doing package upgrades, even without having jailbroken your device.

edit: On second though, you may need to manually tag **usbmuxd**, **libiphone** and **ifuse** for installation. Search the forums for those package names and you should find the thread discussing them.

---

### Post by XLAWLX on 2010-01-07
Look in cydia for your needs. everything is in there :)

---

### Post by Neezer on 2010-01-07
> **Zorael said:**
> For what it's worth, if you add Paul McEnery's ppa ([ppa:mcenery/ppa](https://launchpad.net/~pmcenery/+archive/ppa)) you should be able to sync music over usb with Rhythmbox or gtkpod after doing package upgrades, even without having jailbroken your device.

edit: On second though, you may need to manually tag **usbmuxd**, **libiphone** and **ifuse** for installation. Search the forums for those package names and you should find the thread discussing them.

Can I add those to my repositories even if I am running 9.04? It looks like the only choices there are for 9.10 and 10.04.

---

### Post by Zorael on 2010-01-07
Well, there are only Karmic builds of those packages. Your choices would be to just add them as Karmic repos and install the packages anyway, or to copy the packages to a ppa of your own and tell it to build them for Jaunty then.

Either way there's a chance the packages will depend on other packages of versions higher than are available in the Jaunty repos, and refuse to install.

---

### Post by Neezer on 2010-01-07
> **Zorael said:**
> Well, there are only Karmic builds of those packages. Your choices would be to just add them as Karmic repos and install the packages anyway, or to copy the packages to a ppa of your own and tell it to build them for Jaunty then.

Either way there's a chance the packages will depend on other packages of versions higher than are available in the Jaunty repos, and refuse to install.

I am pretty sure that is exactly what happened. I tried adding the lines in my sources GUI and I clicked apply or whatever it is, and it gave me a bunch of error messages.

too bad.

any other solutions? using rhythmbox would have been awesome! I assume it is something where I can just drag and drop songs into an icon for my ipod.

---

### Post by Zorael on 2010-01-07
Without details of what errors it threw, hard to say. It may be that you just need to manually fetch a few extra packages from main Karmic repos.

So what does the following terminal command output?
```
$ aptitude install ifuse usbmuxd libiphone0 -sv
```
It won't download or install anything - just simulate an installation.

---

### Post by Neezer on 2010-01-07
> **Zorael said:**
> Without details of what errors it threw, hard to say. It may be that you just need to manually fetch a few extra packages from main Karmic repos.

So what does the following terminal command output?
```
$ aptitude install ifuse usbmuxd libiphone0 -sv
```
It won't download or install anything - just simulate an installation.

so I did some checking and i had jaunty after the source location, so i removed the jaunty ones and put in karmic. it seemed to go fine. Now what. When I plug in my ipod and open rhythmbox I don't see the ipod. I didn't get any error messages when installing or doing the updates...

---

### Post by Zorael on 2010-01-07
Perhaps your gvfs is too old to react automatically when you connect it.

Open up a terminal.
```
$ mkdir iphone
$ ifuse iphone
```
Does it spout any errors, or does Rhythmbox say anything?

Else try with **gtkpod**, though you'll need to install its package if you don't have it already.

---


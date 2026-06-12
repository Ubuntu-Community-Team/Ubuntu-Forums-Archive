---
title: "Installing iTunes using Wine"
date: 2006-06-04
forum: General Help
---

### Post by Jammy_Stuff on 2006-06-04
I installed Wine using Automatix today and I've been trying to install iTunes. However, it keeps crashing while its supposed to be copying the files over. Does this just happen or is it just not working for me?

Is there another way to install iTunes?

---

### Post by testube_babies on 2006-06-04
I think the most popular way of installing iTunes is by using Codeweavers Crossover Office.

[http://www.codeweavers.com/](http://www.codeweavers.com/)

BTW, Crossover implements WINE and only supports up to iTunes version 4.9.

---

### Post by aysiu on 2006-06-04
iTunes doesn't play nice with Wine.
You'll need Crossover Office for sure if you want iTunes.

If you're open to alternatives, you can try SharpMusique for purchasing songs and Banshee for organizing/playing music and syncing with your iPod.

---

### Post by codypumper on 2006-06-04
Considering the low support for iTunes, you may want to opt for AmaroK.

---

### Post by Jammy_Stuff on 2006-06-04
If I want to listen to my iTunes music from Windows and sync with my ipod which is the best way to go?

---

### Post by aysiu on 2006-06-04
[QUOTE=Jammy_Stuff]If I want to listen to my iTunes music from Windows and sync with my ipod which is the best way to go?[/QUOTE] I've heard Banshee (particularly in Dapper) has pretty good iPod syncing.

Otherwise, you can use AmaroK (for playing) and Gtkpod (for syncing).

To mount your Windows partition:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by padre999 on 2006-06-04
[QUOTE=aysiu]I've heard Banshee (particularly in Dapper) has pretty good iPod syncing.

Otherwise, you can use AmaroK (for playing) and Gtkpod (for syncing).

[/QUOTE]

Amarok is also good for transfering music, inclusive covers. I am doing that every day. I am using the new 1.4 Beta of Amarok btw.

---

### Post by Jammy_Stuff on 2006-06-04
I've got amaroK but it doesn't seem to want to play anything. MP3s, M4Ps nothing works. They add to the playlist but as soon as I click play it says playlist finished.

---

### Post by aysiu on 2006-06-04
[QUOTE=Jammy_Stuff]I've got amaroK but it doesn't seem to want to play anything. MP3s, M4Ps nothing works. They add to the playlist but as soon as I click play it says playlist finished.[/QUOTE] Ubuntu is one of the few Linux distributions that comes with no proprietary or "non-free" software. That can be remedied, though:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[http://www.ubuntuforums.org/showthread.php?t=185643](http://www.ubuntuforums.org/showthread.php?t=185643)

---

### Post by Jammy_Stuff on 2006-06-04
If I am going to use amaroK do I need to get the Ubuntu or the Kubuntu ones?

Give me a list of packages I need to get.

---

### Post by bionnaki on 2006-06-04
ubuntu or kubuntu what?

---

### Post by Jammy_Stuff on 2006-06-04
If you look in the resticted formats wiki it has some packages for Ubuntu and some for Kubuntu. Seeing as amaroK is a KDE app should I use the Kubuntu packages?

---

### Post by aysiu on 2006-06-04
[QUOTE=Jammy_Stuff]If I am going to use amaroK do I need to get the Ubuntu or the Kubuntu ones?

Give me a list of packages I need to get.[/QUOTE] Just install it through the package manager or the terminal ```
sudo aptitude update
sudo aptitude install amarok
```

---

### Post by Jammy_Stuff on 2006-06-04
I've installed amaroK but I was talking about the restricted formats packages. I already have the Ubuntu one for MP3s but they still don't play (in amaroK).

---

### Post by Jammy_Stuff on 2006-06-05
Sorry to bump but I really can't work out what packages I need to install to get amaroK to play MP3s etc.

---

### Post by aysiu on 2006-06-05
[QUOTE=Jammy_Stuff]Sorry to bump but I really can't work out what packages I need to install to get amaroK to play MP3s etc.[/QUOTE] ```
sudo aptitude update
sudo aptitude install libxine-extracodecs gstreamer0.10-plugins-ugly
```

---

### Post by ericesque on 2006-06-05
I used BUMPS to get all my multimedia-- or a vast majority of it-- going.  It's an install script that takes care of the codec issues for you.  

Check it out 

 [http://www.ubuntuforums.org/forumdisplay.php?f=143](http://www.ubuntuforums.org/forumdisplay.php?f=143)

---

### Post by RAOF on 2006-06-05
[QUOTE=Jammy_Stuff]Sorry to bump but I really can't work out what packages I need to install to get amaroK to play MP3s etc.[/QUOTE]
You probably want the **libxine-extracodecs** package.

But you're never going to be able to play music bought from iTunes - they're DRM encrypted (Apple's "FairPlay" DRM).  To play them, you'll need to first strip the DRM from them, if it's legal in your country.  From memory, there are tools which can do it.

---

### Post by th3james on 2006-06-05
I find the easiest way to setup all the media codecs is with either the BUMPS script previously mentioned, or using easy ubuntu, which might be slightly easier:

[http://easyubuntu.freecontrib.org/index.html]("http://easyubuntu.freecontrib.org/index.html")

Also, if you want to play more formats, be sure to get the newest version of amaroK:

[http://kubuntu.org/announcements/amarok-1.4.php]("http://kubuntu.org/announcements/amarok-1.4.php")

For some reason, i don't think the newest version is actually in the dapper repos (correct me if im wrong). Unfortunatly though, as said, it won't play DRM music. I it supposed to support ipods as well, although i have not been able to test this.

---

### Post by bunkee on 2006-08-18
I was able to get iTunes to run using the latest version of wine.

---

### Post by secretlondon on 2006-08-18
> **aysiu said:**
> 
If you're open to alternatives, you can try SharpMusique for purchasing songs and Banshee for organizing/playing music and syncing with your iPod.

SharpMusique has been broken for about 9 months - it doesn't work with itunes 6.

Amarok and Rhythmbox both claim to work with ipods (I haven't got one to test).

---

### Post by teabeartom on 2006-08-24
Jammy_Stuff,
If you want to play your encrypted files on Ubuntu that you bought from the iTunes store, you can install the latest iTunes with wine.  Instructions are here: [http://frankscorner.org/index.php?p=itunes6]("http://frankscorner.org/index.php?p=itunes6")

That worked on my computer with Dapper installed and now I can play encrypted files.

---

### Post by hiena on 2006-10-03
I think the question was how to install iTunes and  not a replacemement for it...
Come on guys!

---

### Post by aysiu on 2006-10-03
> **hiena said:**
> I think the question was how to install iTunes and  not a replacemement for it...
Come on guys!
The OP wants the impossible.

You can't run iTunes in Wine.

Even in Crossover Office, I don't think iTunes has full functionality.

If iTunes is that important to you, run it in VMWare or a dual boot. Otherwise, use native solutions.

---

### Post by KeeganX on 2006-10-03
Try using Songbird it looks exactly like Itunes

[www.songbirdnest.com](www.songbirdnest.com)

---

### Post by weird_c00kie on 2006-10-23
> **bunkee said:**
> I was able to get iTunes to run using the latest version of wine.

what version of itunes did you install?
whenever i try installing it, it comes up with a message saying:

Windows (R) Installer found. this is an older version of the windows (r) installer. click ok to continue"

and then setup just exits. i've tried this with itunes versions 4.5, 5, 6, and 7 and none of them work.

funny thing is, i'm not too fussed about running itunes or any other piece of software.... i jus want to preserve my playlists and song data :(

---

### Post by satauros on 2008-06-26
songbird plays m4ps.
getsongbird.com

---


---
title: "has anyone gotten electric sheep to work in karmic?"
date: 2009-11-03
forum: General Help
---

### Post by PuddingKnife on 2009-11-03
Well? How'd you do it??   ):P

---

### Post by The Toxic Mite on 2009-11-03
Electric sheep?! What the <beep> is that?!

---

### Post by PuddingKnife on 2009-11-03
sorry

[http://community.electricsheep.org/](http://community.electricsheep.org/)


A totally rad screensaver :guitar:

---

### Post by Joeb454 on 2009-11-03
It does look awesome.

That said - no, I haven't. So I'd be interested in a solution as well, I've only found it since I had Karmic installed, so I can't really troubleshoot it :(

**Edit:** Also - moved to General Help

---

### Post by PuddingKnife on 2009-11-03
Yea found it here via UF:

[http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html](http://blog.thesilentnumber.me/2009/09/top-things-to-do-after-installing.html)

Which is awesome in its own right.

---

### Post by Flimm on 2009-11-03
I had to download the latest version of Electric Sheep from [this PPA](https://launchpad.net/~flam3/+archive/ppa/+packages), it's not listed under Karmic but the one under Intrepid is the latest version for Linux, 2.7b11 and works on Ubuntu 9.10 great. The current version in Karmic's repositories is 2.6.8.

---

### Post by PuddingKnife on 2009-11-03
I dont uh .. I'm a newb.

What do I do at that link? I clicked on something and it took me to a web page of code.

sorry for my newbishness

---

### Post by glittalogik on 2009-11-04
[LIST]
[*]Open Synaptic
[*]Goto Settings --> Repositories --> Other Software --> Add
[*]Enter "ppa:flam3/ppa" (minus quotes) as the APT Line and click Add Source
[*]Highlight "http://ppa.launchpad.net/flam3/ppa/ubuntu karmic main" and click Edit
[*]Change Distribution from "karmic" to "intrepid" (minus quotes) and click OK
[*]Click Close
[*]Click Reload
[*]Install 'electricsheep'
[/LIST]

If you get an error for the flam3 package, just retry installing it and it should be fine =)

That worked for me, hope it does for you =)

---

### Post by PuddingKnife on 2009-11-04
Did everything you listed. Installed electricsheep via the CLi. Then typed electricsheep .. the output:

> Please be patient while the first sheep is downloaded...
curl: (6) Couldn't resolve host 'v2d6.sheepserver.net'
lost contact with v2d6.sheepserver.net, cannot retrieve sheep.

Somethings phishy there   :P

---

### Post by PuddingKnife on 2009-11-05
Still no progress

---

### Post by tlacuache on 2009-11-05
Thanks, worked for me, too.

> **glittalogik said:**
> [LIST]
[*]Open Synaptic
[*]Goto Settings --> Repositories --> Other Software --> Add
[*]Enter "ppa:flam3/ppa" (minus quotes) as the APT Line and click Add Source
[*]Highlight "http://ppa.launchpad.net/flam3/ppa/ubuntu karmic main" and click Edit
[*]Change Distribution from "karmic" to "intrepid" (minus quotes) and click OK
[*]Click Close
[*]Click Reload
[*]Install 'electricsheep'
[/LIST]

If you get an error for the flam3 package, just retry installing it and it should be fine =)

That worked for me, hope it does for you =)

---

### Post by Milan Knizek on 2009-11-07
There is another repository for Karmic:
[https://launchpad.net/~khashayar/+archive/builder](https://launchpad.net/~khashayar/+archive/builder)
And it works for me.

---

### Post by Skiro'n on 2009-11-08
It's working for me too.

What I did:
1) Add PPA of electricsheep Team
1.1) Add the following two lines in your /etc/apt/sources.list
```
deb http://ppa.launchpad.net/flam3/ppa/ubuntu intrepid main 
deb-src http://ppa.launchpad.net/flam3/ppa/ubuntu intrepid main
```
(yeah I know, it's an intrepid repository, but the version of electricsheep in here is up to date)

1.2) Add the key for the PPA
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0xf191582f22b943d1029b2d5a91dae98f32ffb679
```

2) Install electricsheep (after updating the repositories)
```
sudo apt-get update
sudo apt-get install electricsheep
```

EXTRA 3) for KDE 4.3 users
To let Electricsheep appear in the list of screensaver, you need to:
3.1) create a new file in your home directory named "electricsheep.desktop"

3.2) copy the following in this file:
```
[Desktop Entry]
Encoding=UTF-8
Exec=electricsheep
Icon=kscreensaver
Type=Service
X-KDE-ServiceTypes=ScreenSaver
Actions=InWindow;Root;Setup;
X-KDE-Category=Fractals
Name=ElectricSheep

[Desktop Action Setup]
Exec=electricsheep-preferences
Name=Setup...

[Desktop Action InWindow]
Exec=electricsheep -window-id %w
Name=Display in specified window
NoDisplay=true

[Desktop Action Root]
Exec=electricsheep -window-id %w
Name=Display in root window
NoDisplay=true
```
3.3) Move this file to "/usr/share/kde4/services/ScreenSavers" with the command
```
sudo cp electricsheep.desktop /usr/share/kde4/services/ScreenSavers/electricsheep.desktop
```

Note that for KDE users, you can have more screensaver by installing the package "kscreensaver-xsavers". I've installed it, I don't know if it is necessary to have electricsheep working...

---

### Post by Ipharus on 2009-11-20
> **Skiro'n said:**
> 
Note that for KDE users, you can have more screensaver by installing the package "kscreensaver-xsavers". I've installed it, I don't know if it is necessary to have electricsheep working...

Thanks for the tip, and yes electricsheep doesnt need the package "kscreensaver-xsavers" to work properly.
I'll install it anyways :D

---

### Post by goldsniper on 2009-11-21
Yep.. jut got it working!:popcorn:

The version in the universe repository is older and broken.
 
[Try this one]("http://mikeysfog.wikispaces.com/HowTo+Install+Electricsheep+For+Ubuntu")

I qoute :

([COLOR="Red"]**If prompted by apt-get to remove a whole lot of packages**[/COLOR] because libavutil-unstripped-49 is to be removed to install libavutil49[COLOR="Red"]**[SIZE="4"] quit the script[/SIZE]**[/COLOR] with [ctrl]+C then see my post on the [Ubuntu Forums]("http://ubuntuforums.org/showpost.php?p=7978449&postcount=2"). Once finished installing the devs run the script again but say no to removing all unstripped packages.)

:popcorn:

---


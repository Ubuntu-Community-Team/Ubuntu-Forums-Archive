---
title: "what is this source for in my software source list?"
date: 2010-11-03
forum: General Help
---

### Post by Rasa1111 on 2010-11-03
hey all, 

 This has been bothering for a couple days now. lol
 I cannot seem to find what this source is for..
[ATTACH]174381[/ATTACH]
"PPA for rugby471"

 How do I find what uses it? 

I ask only because , almost daily, for the past week or so..
I will get an (i) icon in my notification area, telling me to check my sources because something might be out of date,
but i update everything,
 and it might go away for a little while,
but is back again shortly, 
But when i open update manager, it says, :
"your system is up to date"

 while showing me the (i) icon, telling me something is out of date :?:  lol

 Im thinking..
 Since that source sounds ..hmm.. "less important" than the rest.. 
and i know what the other sources in my list are for.. 
so maybe that is causing it? lol, I dunno. 

 Thanks for any insight.

---

### Post by Quackers on 2010-11-03
Do you have Crebs wallpaper slideshow generator?

---

### Post by Rasa1111 on 2010-11-03
> **Quackers said:**
> Do you have Crebs wallpaper slideshow generator?

Hi Quackers,
 No I definitely do not. 
I mean, unless it comes in 10.10, but if not..
no. At least... I shouldnt. 
Ive never installed anything like it. lol

 thanks for the speedy reply. :) <3

---

### Post by Quackers on 2010-11-03
That was the only thing that google came up with that was remotely possible :-)
Rugby471 was a username at Launchpad who had a ppa.

---

### Post by dcstar on 2010-11-03
> **Rasa1111 said:**
> hey all, 

 This has been bothering for a couple days now. lol
 I cannot seem to find what this source is for..
[ATTACH]174381[/ATTACH]
"PPA for rugby471"

 **How do I find what uses it?** 
.........

Google:

[https://launchpad.net/~and471/+archive/ppa/+build/1171007](https://launchpad.net/~and471/+archive/ppa/+build/1171007)

**Every** single PPA in your system is put there by you, no one else.

---

### Post by garvinrick4 on 2010-11-03
```
gksudo gedit /etc/apt/source.list
```
And put a # (comment) at the front of the added ppa that you do not know what it is.
That will make it inoperable but if you want to add it back take away the #(uncomment)
Then open a terminal and:
```
sudo apt-get update
```
Will now not use that ppa but still there just incase you find out what it is and want it.

---

### Post by Rasa1111 on 2010-11-03
> **Quackers said:**
> That was the only thing that google came up with that was remotely possible :-)
Rugby471 was a username at Launchpad who had a ppa.

 Cool, thanks Quackers. :)

 Yeah , I found him on launchpad,
 but still couldnt find out what he had that I would need his source for. lol


> DCstar~

Google:

[https://launchpad.net/~and471/+archi...+build/1171007](https://launchpad.net/~and471/+archi...+build/1171007)

Every single PPA in your system is put there by you, no one else.

 Thanks,
 Yeah I know,
i did google, [see above]. 
 I wasnt implying someone else put it there. lol
Just not sure what I have downloaded/installed that would be using it.  :P

 thanks,
 
 and your link is dead. 

@garvinrick4~ 

 Cool, thanks man. 
 good to know. :)

i am really tempted to just remove it... lol :guitar:

---

### Post by Quackers on 2010-11-03
Why don't you just comment it out for now, then if your memory improves (with the medication) you can just uncomment it again. :-) :-) :-)

---

### Post by Rasa1111 on 2010-11-03
> **Quackers said:**
> Why don't you just comment it out for now, then if your memory improves (with the medication) you can just uncomment it again. :-) :-) :-)

haha,
 funny guy. :P

Well, Ive attempted to do that...
but when gedit comes up,
 it is blank.. 
so I cant put a # in front of any PPA. 

look> [ATTACH]174392[/ATTACH]

 or am I confused, and missing something?...
[possibly means i need to medicate... or stop...] ;) lol

 thanks.

---

### Post by coldraven on 2010-11-03
[FONT=monospace]garvinrick4 made a typo, it should have been.

[/FONT]```
gksudo gedit /etc/apt/sources.list
```with an "s" on "source".
Don't forget to 
```
sudo apt-get update
```

---

### Post by Elfy on 2010-11-03
Possibly it's not even on sources.list anyway - could be in it's own repo in /etc/apt/sources.list.d/

---

### Post by Rasa1111 on 2010-11-03
cool, thanks coldraven, that worked.. 

 But forestpiskie is right..
 I dont see it in there anywhere.. 

> # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release Candidate i386 (20100928)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by Elfy on 2010-11-03
Then it's in /etc/apt/sources.list.d/ - there will be a file in there that can be deleted or edited if necessary.
```

ls /etc/apt/sources.list.d/
```

---

### Post by luigi_mb on 2010-11-03
> **dcstar said:**
> Google:
...
**Every** single PPA in your system is put there by you, no one else.

Not strictly true. For example, installing Google-Chrome causes the Google-Chrome ppa to be added automatically.

/luigi

---

### Post by Rasa1111 on 2010-11-03
ok, well.. 
I have removed that PPA, a few hours ago,
everything seems fine, and the (i) is no longer popping up in my notification area. 
So, I guess we can mark this solved! lol
 Thanks everyone for your replies,
 much appreciated. <3

---

### Post by garvinrick4 on 2010-11-03
> **luigi_mb said:**
> Not strictly true. For example, installing Google-Chrome causes the Google-Chrome ppa to be added automatically.

/luigi Isn't there a chromium in the repo's that is stable without a ppa that can
be installed thru normal channels and then a ppa that can be installed (unstable) that gets updated on a daily basis? At one time only thru ppa now have a choice I believe. I think I installed from Ubuntu software center and commented out ppa that I installed in sources.list. I have never seen a ppa that puts itself in your sources.list without you installing and or adding key.

---

### Post by Rasa1111 on 2010-11-03
> **garvinrick4 said:**
> Isn't there a chromium in the repo's that is stable without a ppa that can
be installed thru normal channels and then a ppa that can be installed (unstable) that gets updated on a daily basis? At one time only thru ppa now have a choice I believe. I think I installed from Ubuntu software center and commented out ppa that I installed in sources.list. I have never seen a ppa that puts itself in your sources.list without you installing and or adding key.

Yeah, I use chromium and have no PPA for it. 
Installed it through software center.

---

### Post by Rasa1111 on 2010-11-03
welp,
 on another note:
 the damn (i) icon has reappeared. :( lol
(i) "The update information is outdated" :mad:

---

### Post by Quackers on 2010-11-03
Do you need to run sudo apt-get update?

---

### Post by Rasa1111 on 2010-11-03
> **Quackers said:**
> Do you need to run sudo apt-get update?

well now.. that is a very good possibility! 
I did forget to do that! doh! lol

ok, Done. we shall see.  

 Thanks quackers. <3

---

### Post by Quackers on 2010-11-03
I have my fingers crossed :-)

---


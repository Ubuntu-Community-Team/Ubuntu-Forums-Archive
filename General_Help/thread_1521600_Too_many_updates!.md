---
title: "Too many updates!"
date: 2010-07-01
forum: General Help
---

### Post by cr4321 on 2010-07-01
I am not a software professional - but have been using computers for quite some time now. Started using Linux a couple of years back, and am really impressed. I installed Ubuntu 10.04 in early May. I also installed some programs to test out - and some games for pre-school kids. The kids love it too.

In less than 2 months I have already downloaded more than 700Mb of updates of all sorts. (the original cd was only about 700Mb)

My question is this. Why are there so many updates and so frequently? I can understand "security updates" - but why so frequently? Moreover, I doubt if any of the updates has any improved functions or features.

Is it not possible to stop updates till a new version or new features is made or an old feature has significant improvements?

As an outsider, the only inference I can draw is - the releases are done without much thought to quality. (Just as I am typing this I get a message that "Firefox" has a new version! - there was a version change just weeks back)

Secondly, I do get the feeling that the programs are becoming too bulky.. (which in turn is slowing down he system) with too many frills which does nothing to enhance the "utility" or "usability" of the programs. 

This is the only negative feeling in 2 years, otherwise, there has been some good improvements in feel and looks, besides in the installation etc..  I would like to know if these are common feelings, or is it my ignorance about the nitty gritties ?

- cr4321

---

### Post by byStanderone on 2010-07-01
...much thoughts have been taken and third party softwares have been considered before any release of a particular version, the updates and patches are made later for several reasons and one of them i'd guess is the fact that feedback from users come late. understandle because most of us would rather install a new version after a month or so of the release date, playing safe, and due to the multitude of applications feedback about a malfunctioning application comes late also.

there are legal matters that would have to be settled, too before a particular source code could be obtained, hence the delay for some patch for a particular application. existing softwares i would say are dynamic in the sense that they are also upgraded, hence the system needed updates as well.

...a simple opinion anyway, and of course there are other reasons which the developers have the right not to divulge...i trust, they know their thing.

---

### Post by jocko on 2010-07-01
> **cr4321 said:**
> My question is this. Why are there so many updates and so frequently? I can understand "security updates" - but why so frequently? Moreover, I doubt if any of the updates has any improved functions or features. 
Most updates are just security updates and bug fixes, which does not add anything you will notice, unless you suffer from the bugs or security flaws that they fix.

> **cr4321 said:**
> Is it not possible to stop updates till a new version or new features is made or an old feature has significant improvements?
You can stop some of the updates if you want to. Just open up System-->Administration-->Software sources, go to the "Updates" tab and untick the ones you don't want. But you need to know that it's probably a bad idea to skip the security updates. Or you could just inactivate the automatic check for updates and live in complete oblivion about all the updates: go to System-->Settings-->Startup programs (not sure this is what it's called in the English version). Inactivate "Update Notifier". 


> **cr4321 said:**
> As an outsider, the only inference I can draw is - the releases are done without much thought to quality. (Just as I am typing this I get a message that "Firefox" has a new version! - there was a version change just weeks back)
Do you really think there is something as a perfect and bug-free program? During the development of the next ubuntu version the ubuntu developers have just six months to take the source code of every single piece of software from their respective upstream developers, build them for ubuntu and try to fix any issues that they themselves or the testers find, before the ubuntu version is released.
Sometimes there are still some bugs left that are not noticed until "normal users" start to upgrade, which results in a fair amount of updates after the final release.
Sometimes a problem with the version of a program in the ubuntu repos is fixed in an upstream version. Then the developers often patch the source to include that fix from the upstream developers and rebuild the package.

> **cr4321 said:**
> Secondly, I do get the feeling that the programs are becoming too bulky.. (which in turn is slowing down he system) with too many frills which does nothing to enhance the "utility" or "usability" of the programs.
No idea which programs you talk about here, but I have the exact opposite feeling. But maybe your hardware is close to the lower end of the scale when it comes to ram, cpu or graphics card, which could probably cause a slight slow-down in some cases. For example I noticed that my old computer became sluggish after I upgraded it to 9.04, but that was caused by bad default settings for the open source driver for my ati graphics card and was easily fixed by configuring it myself.

---

### Post by Aearenda on 2010-07-01
Have you tried changing the automatic updates settings? This won't change the number of updates itself, but it will change how often the system looks for them and you can do them in fewer 'lumps'.

Go to System->Administration->Update Manager
Click the 'Settings' button 
Click the 'Updates' tab
Choose an interval (daily/weekly etc) and change other settings if you fancy
Click 'Close' and again 'Close'

I don't think you should disable security updates, but you can stop everything else.


(Jocko says this too, but that post appeared while I was typing this! Doh)

---

### Post by snowpine on 2010-07-01
Ubuntu is a "cutting edge" Linux distro. You get the latest applications and frequent updates. This is what makes Ubuntu such a great showcase for the latest developments in desktop Linux.

You could switch to a distro with older, stable packages (like Debian Stable or CentOS), or perhaps an older Ubuntu release (8.04 is very stable, not many updates these days). But you would miss out on the experience of using the latest and greatest software.

Unless you have restricted internet access (some ISP's are capping downloads these days) I recommend you simply trust the Ubuntu developers and apply all of the updates. They really do know what they're doing; the updates range from bug fixes that improve your user experience to major security updates that protect you and your children online (for example the recent Firefox upgrade).

ps I'll also point out that the Update Manager is one of my favorite things about Linux. I don't miss the Windows method of shutting down my computer and seeing "Please wait while Windows installs 11 updates."

---

### Post by dnguyen1963 on 2010-07-01
I have 8.04 LTS on one of my computers and never perform any update to the system...rock solid...no crash...no virus attack.  The computer is on 24/7.  My wife watches films online from website that has been known to destroy Windows OS with viruses, and again no problem whatsoever.  This might not be true for everyone...just my personal experience.  On the other hand, I had 10.04 LTS on my newer computer and the system completely crashed after one update.

---

### Post by cr4321 on 2010-07-04
> **byStanderone said:**
> ...much thoughts have been taken and third party softwares have been considered before any release of a particular version, the updates and patches are made later for several reasons and one of them i'd guess is the fact that feedback from users come late. understandle because most of us would rather install a new version after a month or so of the release date, playing safe, and due to the multitude of applications feedback about a malfunctioning application comes late also.

there are legal matters that would have to be settled, too before a particular source code could be obtained, hence the delay for some patch for a particular application. existing softwares i would say are dynamic in the sense that they are also upgraded, hence the system needed updates as well.

...a simple opinion anyway, and of course there are other reasons which the developers have the right not to divulge...i trust, they know their thing.

Thank you bystanderone. I appreciate your views. I am sure there are multitude of reasons for these updates. I really do admire the way people of such high calibre come together to develop such a wonderful creation as the Ubuntu distro - (and, of course, the other packages, too)

Instead of complaining, henceforth, I think I will spend sometime to give feedback on the software I work with - whenever I get the time!

Thanks, once again.

- cr4321

---

### Post by stderr on 2010-07-04
I hear your concerns. I've been using Ubuntu solidly for around 4 years, and the update frequency can be frustrating. Whilst you can disable checking, or only update every now and again (as I do), the fact is you *know* there are updates waiting and one tends to feel somewhat obliged to install them sooner rather than later ;)

However, this is simply a fact of software development. There are always a huge plethora of bugs in software that's released, and the frequency of update rollout can be as much a signifier of a good software development team as originally poor coding. I'd much rather have fixes rolled out ASAP, especially for security issues, than have some knowing that X million people will be running software with a specific vulnerability until the next major release.

I would recommend you do as I do if you're overwhelmed by the updates; ignore the warnings (disable the update checking as above too if you fancy) and just run updates every week/month/...

If you're interested, I tend to stick an alias at the bottom of ~/.bashrc to make updating even quicker (many people prefer Update Manager though):

```
alias aptupgrade="sudo apt-get update && sudo apt-get upgrade"
```

---

### Post by cr4321 on 2010-07-04
Thank **byStanderone, jocko, Aearenda, snowpine, dnguyen1963 and stderr**. Very nice to read your views and really appreciate it guys! In fact, I thought I had come into the Lions den to criticise the den's interior decoration fully expecting to be blasted by all the Ubuntu lovers! I am overwhelmed by the fact all of you have taken time to put things in perspective for a old timer like me!

I do appreciate your views and also like the way the "community" is speaking up for one another and being supportive! I have read everything you guys have written, and I do understand how it must be during the "final" days of the deadline to release a software - because this happens in every other fields as well.

I would want that distros like Ubuntu necessarily have to be dynamic and continue to reach out for "the cutting edge". However, I will request each package developers (they are the real heroes, of course) to ensure that the package is well tested and released only when it is found to be reasonably stable. Take time for the next version - till there is a major feature enhancement. On my part, I will surely take time to test packages and give my humble feedback, for whatever it is worth!. Once again, let me reiterate, all your views are well taken. Thanks and regards.

[About me, I am touching 60, and have been in love with technology and been working for nearly 40 years now - in fields where at best, I have only used computers for normal work. I was fascinated with computers and softwares - and that became my hobby in the limited spare time I had.

I came accross Linux and Ubuntu only 2 years back - when a nephew of mine talked about Linux. Curiosity led me to Kubuntu and I just requested for a free cd - and was pleasantly surprised to get one a few days later! Then on, I have tried out many distros and love them all.

Let me reiterate that I love Ubuntu and will continue to keep it updated! - though I can barely afford the high cost charged by the isp!!!]

- cr4321 :p

---

### Post by giddyup306 on 2010-07-04
I posted these videos on another site a while ago.  They really helped me understand how Linux and Ubuntu have been developed.  Basically Ubuntu can't do all of the beta testing and relies on the public to fill out bug reports, and then they can make a patch for them.  They are quite long so grab some :popcorn:.  I can't remember which video it was, but they have only so many components that they can test at their work.  Plus I see the updates and devotion and pride in their work.

[Ubuntu Linux   with Mark Shuttleworth]("http://www.youtube.com/watch?v=mrLFFGWKqG8&NR=1") (about 55 minutes)

[Greg Kroah Hartman on the Linux Kernel ]("http://www.youtube.com/watch?v=L2SED6sewRw&NR=1") (about 50 minutes)

[The Origins of Linux -  Linus Torvalds]("http://www.youtube.com/watch?v=WVTWCPoUt8w") (about 1 hour 25 minutes)

EDIT: I think I'm going to put these links in my sig.

---

### Post by stderr on 2010-07-04
You're very welcome! I do hope you'll never find ubuntuforums to be a Lion's Den though! I am occasionally guilty of exchanging the terms "Windows" and "Winblows" in jest, but that's about as far as I go ;) 

The community here is, IMHO, second to none among Linux distros. I originally started out with Debian, and when I first moved to Ubuntu I was overwhelmed by the readiness of people here at ubuntuforums to offer support. Indeed, due to the similarity of Debian and Ubuntu (since Ubuntu is based on Debian), I was already gleaning valuable information from here even before I switched over.

However true it may be, I like to think of most of those running Ubuntu, or contributing to the community, or indeed developing for it as having something of the Ubuntu spirit about them - I often get such a feeling from the people here.

Best wishes to your good self, and as they say, may [the spirit of Ubuntu be with you]("http://www.linuxplanet.com/linuxplanet/reports/7098/1/").

Umuntu ngumuntu ngabantu. "A person is a person through other persons".

---

### Post by 4Orbs on 2010-07-05
Good grief... I dropped in here expecting to read some really great insults, but instead found a bunch of mushy goo-goo talk. Excuse me while I float on over to the marshmallow booth.

---

### Post by stderr on 2010-07-05
Insults... for some good starting places I'd recommend school playgrounds and the House of Commons. Good luck!

---


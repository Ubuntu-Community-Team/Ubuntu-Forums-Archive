---
title: "A problem nobody here can solve?"
date: 2011-03-14
forum: General Help
---

### Post by Hector23 on 2011-03-14
I use Ubuntu LTS, which is supposed to be the most checked and rechecked version of Ubuntu, and is provided to the industry. 

Here:

[http://ubuntuforums.org/showthread.php?t=1706318](http://ubuntuforums.org/showthread.php?t=1706318)

I explained that I can't produce multisession DVDs with K3B. I didn't get a single answer in more than 20 hours. Of course, I could use Brasero, which, for years, has meant nothing but trouble to me, whereas K3B has been solid as rock. Besides, K3B has an option to check the engraving that I appreciate.

How come there are such problems in an LTS version, more than 10 months after release? Am I supposed to roam the net for days in search of solutions proposed by some nobodies? Like writing shell scripts, configuring K3B to use cdrecord, changing options and what not?

This is the first real problem I encounter with Ubuntu, which make the let down even worst. I really thought I'd have zilch problem with Ubuntu LTS. Is there anybody here who can't reproduce the problem? Has K3B been written off the list of Ubuntu supported software?

TIA

---

### Post by ron999 on 2011-03-14
> **Hector23 said:**
> ... I didn't get a single answer in more than 20 hours...

...How come there are such problems in an LTS version... 

...Is there anybody here who can't reproduce the problem?..


Hi Hector23
Sometimes nobody here knows the answers.:(
Or maybe those people with similar problem haven't visited this forum recently.:confused:
It's not really Ubuntu's fault.:rolleyes:
If you can't get an answer here try going further up the tree - ask at the k3b forum.:cool:
Here:- [http://forum.kde.org/viewforum.php?f=153](http://forum.kde.org/viewforum.php?f=153)

---

### Post by 3Miro on 2011-03-14
The K3B software is supported by the community not Canonical. Furthermore, since it is a KDE applicaiton running under GTK/Gnome environment, problems are possible. Also, note that if you are not satisfied with the help that you get from us volunteers, you can always purchase support from Canonical.

What software did you use to write the multi-session DVD in the first place. I have bad experience with Windows programs using their own standards which would be incompatible with K3B (or Brasero for that matter).

---

### Post by Hector23 on 2011-03-14
> 
If you can't get an answer here try going further up the tree - ask at the k3b forum.:cool:
Here:- [http://forum.kde.org/viewforum.php?f=153](http://forum.kde.org/viewforum.php?f=153)

I was previously using Fedora and I must say I hated this classical response. There were so many bugs that you'd have to spend all your time opening accounts for different software, discussing endlessly until a new version would come out that wouldn't fix the bug. Yet, the bug report was erased and you had to fill another one. Fortunately, there really aren't that many bugs in Ubuntu LTS.

It seems K3B has its own site, k3b.org and here's what you can find:

Changelog since K3b 1.91 (2.0-RC2)
Bugfixes:

    * In some cases medium doesn't get accepted for multisession burning (230742)

[http://www.k3b.org/](http://www.k3b.org/)

1.91 is the version presently offered for Ubuntu LTS and, as you can see, it's a RC. K3B is now at version 2.02, so it's hard to report a problem when you're using a RC and you're 2 versions late after the version declared stable.

Maybe Ubuntu should provide the latest upgrade? Or does it cause other problems? I must confess that, when it comes to upgrading, I a sissy. I only install upgrades that are provided fearing to fall from the frying pan into the fire.

Is there any way I can install the latest updates and revert back if things don't work out? But, as there really is a problem, I believe Canonical developers should give it some consideration. I'll just get **** if I go to K3B.

---

### Post by wojox on 2011-03-14
When ever you want a more up to date application check out Launchpad [“k3b” package in Ubuntu]("https://launchpad.net/ubuntu/+source/k3b")

---

### Post by bodhi.zazen on 2011-03-14
> **Hector23 said:**
> I believe Canonical developers should give it some consideration. I'll just get **** if I go to K3B.

I think you misunderstood what 3Miro told you. The Canonical developers do not support K3b , you need to go upstream, to the K3b developers with your concerns. (Just because there is a package in Universe does not mean the Canonical Developers wrote or maintain it).

K3b is packaged by the MOTU:

[https://wiki.ubuntu.com/MOTU/](https://wiki.ubuntu.com/MOTU/)

In general, the community (MOTU) packages the source code into a .deb, which is technical and complicated enough

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

But if there is a bug, in the source code, the bug is then passed "upstream" in this case to the K3b project.

---

### Post by 3Miro on 2011-03-14
Hector23,

LTS means long-term-support, which means that people let it run for a while and eventually clean out most of the bugs. If you constantly update the software, then it doesn't have a chance to get stable as new bugs are constantly introduced.

Waiting 20 hours for a response may be long time for you, but not all of the "helpers" have the time to visit all the threads every day, sometimes you have to wait for a while. If you cannot find the answer to your problem here, then your problem is probably a rare one and needs someone with more knowledge of the actual code of K3B (i.e. it is not a simple matter of "change those 3 settings"). We here are a community of volunteers that try to help the best we can, you will probably have to go to "higher authority". 

Canonical doesn't make K3B, K3B is included in the repository by the community. I don't know if buying support form Canonical would help with K3B (although they will surely help with Brasero).

K3B forum/development web-page is the only other option that I can think of.

You also did not provide information on what software you used to make the multi-session DVDs in the first place. You can try making a multi-session DVD under K3B, write something small, then extend the session with K3B again. I know it will waste a DVD (which costs money), but this is the only way I can think of that eliminates the possibility of software incompatibility.

---

### Post by Hector23 on 2011-03-14
> **wojox said:**
> When ever you want a more up to date application check out Launchpad [“k3b” package in Ubuntu]("https://launchpad.net/ubuntu/+source/k3b")

I find it very hard to guesstimate the quality of a software with bug reports. Users of one soft, for instance, may be more advanced than for another and find a way around more easily. But those results do correspond with my experience with both K3B and Brasero:

Brasero: 

1 &#8594; 75 of 128 results (Bugs)

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bugs?field.status:list=NEW](https://bugs.launchpad.net/ubuntu/+source/brasero/+bugs?field.status:list=NEW)

K3B:

1 &#8594; 67 of 67 results (Bugs)

[https://bugs.launchpad.net/ubuntu/+source/k3b/](https://bugs.launchpad.net/ubuntu/+source/k3b/)

Ubuntu LTS is the first distro I use in which Brasero works at all. Every single time a distro came with Brasero, I erased it and replaced it with K3B. But, since Brasero, at least with the little experience I have with it -- I only suppose, from what I read, that it does multisession correctly -- I won't complain about it here. But I'd rather install K3B if ever Ubuntu provides a more up to date version.

---

### Post by Hector23 on 2011-03-14
> I think you misunderstood what 3Miro told you. The Canonical developers do not support K3b , you need to go upstream, to the K3b developers with your concerns. (Just because there is a package in Universe does not mean the Canonical Developers wrote or maintain it).

I understand this very well, but it seems that K3B developers have maybe fixed the problem. Sine Ubuntu LTS uses an RC version in which this peculiar bug wasn't apparently noticed(1). Maybe it would be time to move to the stable version with maintenance and bugfix updates?

(1) As Mark Shuttleworth noted, it would be nice if distros had the same release date and developers could make an effort to make their stable release available for the said release date... But, as you know, this provoqued yet another outcry.

See my next answer for continuation.

---

### Post by clhsharky on 2011-03-14
Hector23


Might want to ask on IRC channels
#k3b
#ubuntu

There fairly quick to respond and maybe some other volunteers might know solution.


Sharky

---

### Post by t0p on 2011-03-14
"LTS" means "long term support" - ie. that version of Ubuntu *and the applications that came with it* will get security updates, etc, for longer than a usual release - 3 years, I think.  This means you won't get newer versions of software.

If you want to use newer versions, you should really use a newer version of Ubuntu.  Or maybe a different distro.  Ubuntu tends to use older versions of software, due to software release dates not coinciding with Ubuntu's release dates.

---

### Post by Hector23 on 2011-03-14
> **3Miro said:**
> Hector23,

LTS means long-term-support, which means that people let it run for a while and eventually clean out most of the bugs. If you constantly update the software, then it doesn't have a chance to get stable as new bugs are constantly introduced.

Y... eees. But certainly K3B wasn't tested much with Ubuntu... Maybe Kubuntu works better with K3B, but I hate it. Klipper and Dolphin certainly work well with Ubuntu.

If, countrary to what happens with Fedora, Brasero went through extended testing with Ubuntu, I aaarrrgh suppose I could do with it, despite all the plight it got me through. Can you believe this, only hearing the name makes me feel awful.

Still, I kinda feel upgrading to a stable instead of RC version of K3B would be a good idea. 

> Canonical doesn't make K3B, K3B is included in the repository by the community. I don't know if buying support form Canonical would help with K3B (although they will surely help with Brasero).

A company might want to buy support for maintaining a large database, for instance, but I don't believe anybody would buy support to use K3B. What I'm doing here is pointing a problem with an LTS version that has not been declared stable. If Brasero performs well, it's not a major problem. 

I also noted that there a problem with the «"» character being absent of the Canadian Multilingual keyboard in OOo, even though Kubuntu got this right and it can be fixed easily.

This is my contribution and I'll see if it will be accepted. With Fedora, these contributions are not accepted. Unless you have a configuration problem, it's always «Go upstream» and, when you're not a developer, nobody listens to you. As a matter of fact, even RH developers have little influence. Quite often, their bug reports stay unresolved for years. You end up wondering if Red Hat talks to developers and what's the use of losing your time.

I don't know what the attitude here will be. Will MOTO prefer to use a buggy RC version instead of a stable one? Will anybody care about one character missing in a seldom used keyboard, just in OOo? Will dictionaries be someday unified so that you can click "Install French" and that will be it? (I discussed this with the keyboard issue and never got an answer. See the post if you want to reply.)

If those comments have no influence, I will stop making them. If the problems I face are too obnoxious, I will change distribution. Maybe I'll switch to Clement Lefebvre's LinuxMint, since he finds that Ubuntu is so bugged than he's planning a move to Debian. (Why is it that I can't trust this guy?) Maybe I'll switch to all the KDE novelties that nobody gives a c-r-a-p about... and install XFCE.

It's open source. There are alternatives but, so far, I find Ubuntu looks mighty good.

---

### Post by jerome1232 on 2011-03-14
> **Hector23 said:**
> I understand this very well, but it seems that K3B developers have maybe fixed the problem. Sine Ubuntu LTS uses an RC version in which this peculiar bug wasn't apparently noticed(1). Maybe it would be time to move to the stable version with maintenance and bugfix updates?

(1) As Mark Shuttleworth noted, it would be nice if distros had the same release date and developers could make an effort to make their stable release available for the said release date... But, as you know, this provoqued yet another outcry.

See my next answer for continuation.

Ubuntu releases do not change application versions during a release. That's part of how things are kept stable within each release. Sometimes newer releases are included in a backports repository.

More on backports here and criteria for apps that may be added to the backports repository. [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

edit: Also how to get applications suggested to be added into backports [https://help.ubuntu.com/community/UbuntuBackports#How%20to%20request%20new%20packages](https://help.ubuntu.com/community/UbuntuBackports#How%20to%20request%20new%20packages)

---

### Post by Hector23 on 2011-03-14
> **t0p said:**
> "LTS" means "long term support" - ie. that version of Ubuntu *and the applications that came with it* will get security updates, etc, for longer than a usual release - 3 years, I think.  This means you won't get newer versions of software.

If you want to use newer versions, you should really use a newer version of Ubuntu.  Or maybe a different distro.  Ubuntu tends to use older versions of software, due to software release dates not coinciding with Ubuntu's release dates.

I receive updates all the time for U. LTS. So what? Bug fixes are eliminated and only security patches remain? I didn't know that.

>  How to download and save streaming video from the Internet - updated 19 Nov 2010

I save videos with DownloadHelper.
Instructions: Click the icon and select the format the video will be saved in. Really neet!

---

### Post by Hector23 on 2011-03-14
> **jerome1232 said:**
> Ubuntu releases do not change application versions during a release. That's part of how things are kept stable within each release. Sometimes newer releases are included in a backports repository.

More on backports here and criteria for apps that may be added to the backports repository. [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Please note that with the keyboard issue I had, all software is absolutely perfect; it's  just a default software configuration issue for OOo. And it's not quite evident that you can reconfigure quotes for your keyboard under Tools, Autocorrection Options. This has nothing to do with Autocorrection.

This problem has been fixed by Kubumtu and Mint... or maybe it was created by some loony at Ubuntu. No idea.

edit: Also how to get applications suggested to be added into backports [https://help.ubuntu.com/community/UbuntuBackports#How%20to%20request%20new%20packages](https://help.ubuntu.com/community/UbuntuBackports#How%20to%20request%20new%20packages)[/QUOTE]

I've filled a backport request at:

[https://bugs.launchpad.net/lucid-backports](https://bugs.launchpad.net/lucid-backports)

We'll see what happens. Thanks for teh URL.

---

### Post by Hedgehog1 on 2011-03-15
> **Hector23 said:**
> 
A company might want to buy support for maintaining a large database, for instance, but I don't believe anybody would buy support to use K3B. 

Hector23,

This is sad news.  I best be telling the folks at Nero that no one will be willing to pay for burning software and the support that comes with it.  I tend to forget that because someone gave me something for free, they are therefore indebted to me.

**What was I thinking** actually paying for Nero (so those engineers and support people could feed their families) when I could file bug reports and make no effort to either fund the solution or become part of the solution.  ***How I have wasted my money***.  Never mind that I can burn any disk, from CD to BluRay, with excellent success.

Then again, ***you could be stupid like me*** and when the free tool isn't yet at where you want it to be, blow 20 bucks on Nero for Linux **[NeroLinux]("http://www.nero.com/enu/linux4.html")**.  Of course, you won't be able to complain about the volunteer efforts of others then.  Or make so many 'coasters'.  And there is that darn 30 day free trial to make sure it works before you spend a red cent.  No, NO don't be tempted.  Remember your are entitled to have volunteers at your service. 

But then, I am a fool.  A fool who earns his living creating software; and teaching others for free.  What do I know?

***The Hedge***

p.s. The problem lies, Hector, not in the distros, but in yourself.

---

### Post by mastablasta on 2011-03-15
i don't think that what he is saying is so wrong.
 
Afterall wher eis the logic in this: A long term support = means it's there to stay for a few years or so and is ment to be sued by companies as well, uses a software with 0.7.1 beta designation. Ofcourse while this LTS version that stays installed for a while, is on computer, they fix all the bugs in the software and give the new software designation 1.0.2. but the LTS  version still has the old one in repositories. Why? so they can offer support for buggy software? perhaps earn money when people call them asking how to resolve the bug?
 
to me a good example is my sound issue. this one seems to have been resolved, but i am not so sure anymore after certain updates. also kernel patches are not JUST security patches it would seem.
 
ok here's what happened - Ubuntu 10.04 LTS came out. A month or two afterwards new ALSA version 1.0.23 came out. now plenty people had issues with .22 version. some sound hardware purchase last year simply did not work with it. you can ofcourse upgrade to .23 but every update seems to overwrite the settings and the version. 
fast forward to february. ALSA .23 is now over 6 months old. It is still no included in 10.04, it was included in 10.10 (which is not long support version). it was also included into debian stable which we know is well, stable. but it is still not in any 10.04 version. why? so they can offer support telling people/companies whose sound card don't work how to upgrade? because you see when you upgrade the thing sorta works. like i said, until certian updates. support my ...
 
i am not saying latest programmes (especially betas or something untested) and latest testing drivers should be there. but drivers and programmes that imporved their stability, resolved bugs, made the fixes should be included.

---

### Post by bodhi.zazen on 2011-03-15
> **mastablasta said:**
> i am not saying latest programmes (especially betas or something untested) and latest testing drivers should be there. but drivers and programmes that imporved their stability, resolved bugs, made the fixes should be included.

I think the misunderstanding you have is with how new releases of various packages are included into a release of a distribution.

There is also the issue of a release , as with Ubuntu, and a rolling release, as with Arch or Gentoo.

All distros have a mechanism of including the new version. There are issues of packaging and testing.

With Debian (and thus to some extent Ubuntu) we have 3 repositories - Stable , testing, and unstable (sid). There is also experimental.

In gentoo new packages are masked.

So you need to balance a new version of a package against stability. Of course if you want bleeding edge go with LFS or learn to compile.

---

### Post by mastablasta on 2011-03-16
no, i think i understand that it's a snapshot of the operating system, "frozen in time".
 
but if certain part is found to be unstable (in the stable version) and a fix is provided, then why not update?
 
then again i just loaded a new snapshot :-)

---

### Post by Hector23 on 2011-03-17
> **bodhi.zazen said:**
> I think the misunderstanding you have is with how new releases of various packages are included into a release of a distribution.

Absolutely. With Fedora, for instance, as Jonathan Corbet explained about 6 months ago, any developer can upload his stuff to the stable version anytime he feels like. So, there's pretty much always something broken in Fedora. It's the kind of pain you just can't imagine.

OTOH, you have Linuxmint's Clement Levebvre going around claiming to the greenest newbies that Ubuntu is always broken, that he must fix so many things that, in the long run, he's thinking about going up to Debian for his only release.

And Linuxmint gets a lot of followers who flee from Ubuntu and won't be buying music and films from Ubuntu. If the only big trick, save providing the codecs on their DVD, is fixing bugs providing more recent software by providing patches, I don't know. For now, they do seem to be using the same version of K3B as Ubuntu. So, unless it's patched, they should have the same problem. 

So, what I'm suggesting is not giving Unity a try in LTS, it's just giving the latest stable version a try in order to prevent some fly by night distributions to get some of Ubuntu market share. I don't believe that, in general, using stable versions of softwares would make Ubuntu less stable. Ubuntu is still the most popular distribution and I would believe developers test their latest version version against Ubuntu LTS. At least, they certainly should. In my experience, K3B does a wonderful job with their stable version. Sebastian Trueg is a very serious developer. His stable versions are what he claims they are: stable. 

Of course, IANAP, and I'll leave developers and administrators evaluate if it's better to keep well documented broken versions of software in LTS in order to keep LTS... stable.

Ok, those are my final 2 ¢ on the matter.

---

### Post by bodhi.zazen on 2011-03-17
> **mastablasta said:**
> no, i think i understand that it's a snapshot of the operating system, "frozen in time".
 
but if certain part is found to be unstable (in the stable version) and a fix is provided, then why not update?
 
then again i just loaded a new snapshot :-)

I think Hector23 summarized it better then I could have.

It may seem "simple" , but installing the newest greatest patched version of foo can fix problem A, but may cause problems x,y, or z.

It also depends on if the problem is minor/critical or if it affects only a few or most users.

It also depends as the new version of foo may depend on bar which may break yet another package.

IMO your best options would be:

1. File a bug report on Launchpad.

2. Try backports

3. From your posting style you might prefer a "rolling release" such as Arch or Gentoo, although both of those distros have their own testing methods.

4. If you really feel it is so easy, just install Linux From Scratch.

---

### Post by mageus on 2011-04-29
In the attempts to wrench this thread back on track . . . (screeeech)

- Yes, multisession has been broken in K3B since Karmic.
- Yes, Brasero doesn't always work.
- Yes, wodim is broken.
- Yes, there has been discussion about this issue since 2005 by the devs themselves, but this petered out some time in 2010.  This issue has never been resolved.

I'd have to agree with the OP on this one.  This issue has been taken to the top, and never addressed adequately.  Solutions like "don't use wodim, compile your own" are not appropriate for a general Ubuntu user.

How a modern day OS can't get multisession DVD burning working boggles the mind.

I just popped back into the discussion because Brasero is now broken for me (worked before).  Looks like I'm booting into Windoze and dusting off Nero or something.

---

### Post by mageus on 2011-04-29
My bad.

Just installed the latest KDE.  Didn't try it much, but a couple burns where I continued a prior multisession worked.

There are several KD3 problems in gnome, the biggest being release of the CD/DVD mount by gnome (disabling automount sometimes helps).

If you're set on using gnome, a solution would be to install KDE or Kubuntu, and just log into a KDE session when you want to burn.

---


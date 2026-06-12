---
title: "PPA repository for original cdrtools for newer Ubuntu?"
date: 2009-11-24
forum: General Help
---

### Post by mgol on 2009-11-24
I use Karmic which includes cdrkit packages. I would personally want to replace them with original cdrtools which are written better; moreover, cdrkit is breaking cdrtools author's copyright names - see:
[http://cdrecord.berlios.de/new/private/linux-dist.html](http://cdrecord.berlios.de/new/private/linux-dist.html)

I don't want to involve in any copyright fights but it would be nice to at least have packages that don't break cdrtools if installed manually and a cdrtools PPA repository would be welcome.

I saw this:
[https://launchpad.net/~ubuntu-burning/+archive/ppa](https://launchpad.net/~ubuntu-burning/+archive/ppa)
However, support ends on Intrepid; I use Karmic. Is there any current repository? Anyone knows why ubuntu-burning team doesn't provide packages for newer Ubuntu versions?

---

### Post by dcstar on 2009-11-24
> **mgol said:**
> I use Karmic which includes cdrkit packages. I would personally want to replace them with original cdrtools which are written better;
........

You can manually download all older packages and install them yourself:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by antistress on 2010-05-09
[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

---

### Post by mgol on 2010-05-10
Thanks, antistress! :)

---

### Post by piedro on 2010-06-17
Do these packages really replace the cdrkit & wodim stuff or do I have to expect problems because of functions impemented by two software packages? 

Is there any howto how to completely switch to the cdrtools tools? 

thx, 
piedro

---

### Post by mgol on 2010-06-17
I use cdrecord with k3b with full success.

---

### Post by nomnex on 2010-06-17
maybe read this for your information

[http://www.linux-watch.com/news/NS6848359973.html](http://www.linux-watch.com/news/NS6848359973.html)

> [FONT=Arial,Helvetica][SIZE=3]Torvalds wrote, "If Joerg keeps  breaking cdrecord, the distributions will hopefully just keep unbreaking  it. The way you send SCSI commands to a device under Linux is to open  the device (with O_NDELAY) and then just start sending the commands.  None of the idiotic scanning and SCSI numbering crap."

"Involving  Joerg in it just makes you go crazy. Don't bother," Torvalds concluded.

Debian,  two years later, has decided to indeed stop bothering with Schilling. [/SIZE][/FONT]

---

### Post by piedro on 2010-06-17
Yes I know about all that legal stuff and the technical critics. 

The points for me as user are: 
- its supposed to really work 
- has blueray support 
- has working dvd-ram support (I love dvd-ram backups!) 
- hope to fix my burning error issues with dvd size errors 
 
Maybe I will be disappointed. In this case I switch back. 

Can anyone explain to me how to make sure my burning engines in the my burning applications, mainly k3b and brasero, will use cdrtools? 

thx for any help, 
piedro

---

### Post by piedro on 2010-06-22
Hi again! 

Still none who knows how to use cdrtools in ubuntu? 
I don't know wether I can safely install and then replace the ubuntu builtin burning tools. 

plz help, 
thx, 
piedro

---

### Post by dcstar on 2010-06-22
> **piedro said:**
> Hi again! 

Still none who knows how to use cdrtools in ubuntu? 
I don't know wether I can safely install and then replace the ubuntu builtin burning tools. 


Don't ask other people to test something you don't even seem to know that you need, do it yourself and see if it works or not.

---

### Post by piedro on 2010-06-23
Hello David! 

You are right, I will test it. 
And you are right that I'm not sure whether it'll solve my burning problems. Maybe not. I'll see ... 

But what's wrong about checking if there's any experience already made by someone else? No harm done in asking, right? 

The truth is that while searching for information and documentation on the cdrtools and the topic in general, I feel lost in an obviously very emotional discussion. It's hard to get any reliable information that people like me can understand without being a programmer or lawyer. 

thx for reading anyway, 
piedro

---

### Post by piedro on 2010-06-30
I have not done any extensive testing yet but using the brandon snider ppa for cdrtools replaced wodim, genisoimage and cdrkit with cdrtools. cdrecord & mkisofs show version 3.0 by Jörg Schilling and until now I haven't run into any problems yet using brasero. 

I'll post if I run into trouble ... 

thx for reading, 
piedro

---

### Post by schily on 2010-07-10
> **nomnex said:**
> maybe read this for your information

[http://www.linux-watch.com/news/NS6848359973.html](http://www.linux-watch.com/news/NS6848359973.html)

These are pointless rants and not really related to cdrtools.

During the past 14 years, I was forced several times to find
workarouds for non-stable Linux kernel interfaces. The last 
incompatible change in Linux SCSI is furtunately nearly 6
years ago. This last one has been introduced by Linus Torvalds 
and caused any compliant SCSI userprogram to fail. Torvalds
has been asked by a big majority of the Linux kernel hackers
to undo his change immediately after he broke Linux, to no
avail.

The original cdrtools only have been broken by Linux kernel
self-incompatibilities from time to time....

Unfortunately many people may believe that there are additional
problems, but these additional problem are bugs that have been
introduced by Debian in the Debian variants of the cdrtools
binaries. The current problems are caused by an unfriendly
Debian packager that started attacks against the project in 
May 2004.

The current version of the fork found on Debian is dead since
more than 3 years. There are more than 100 well known and
well documented bugs. There never has been any attempt from
Debian to fix these bugs.

People who use the original software instead of the fork
from Debian know that none of the documented bugs from
the Debian variant apply to the original software.

During the past 6 months, more and more people realized
the real cause of the problems and started using the
original software again.

---

### Post by schily on 2010-07-10
> **piedro said:**
> Hello David! 

The truth is that while searching for information and documentation on the cdrtools and the topic in general, I feel lost in an obviously very emotional discussion. It's hard to get any reliable information that people like me can understand without being a programmer or lawyer. 

thx for reading anyway, 
piedro

I have no idea why some people run personal attacks against cdrtools.
It started as a personal attack in May 2004 and in Autumn 2005,
the person who started the personal attacks changed his strategy
and started to claim a legal problem in the original software.

If you are interested in the legal background, it would however 
be fairly simple to understand which side is using valid arguments.

Debian and other parties that claim a legal problem did never
give any valid legal prove for their claims and all "information"
that is floating around is just copies from the original Debian claims.

The legal validation on why the original software has no legal
problems is however cleanly proven by legal facts and quotes
to the related laws. Even the FSF only publishes unsourced and
unconfirmed opinions. There are however many respected lawyers 
and law-scientists that all confirm the same interpretation 
of the US- and European Copyright law and this is the  
interpretation that I base my statements on: 
 
* Lawrence Rosen (former legal consultant of the OpenSource Initiative)  
        about the GPL: [http://www.rosenlaw.com/Rosen_Ch06.pdf](http://www.rosenlaw.com/Rosen_Ch06.pdf) 
* Thomas Gordon (US lawyer living in Berlin) about license  
        compatibility: [http://www.osscc.net/pdf/QualipsoA1D113.pdf](http://www.osscc.net/pdf/QualipsoA1D113.pdf) 
* Lothar Determan (Professor at FU-Berlin and University of San  
        Francisco) - Software combinations as Derivative works?  
        [http://www.cs.berkeley.edu/~tlavian/publications/article/Berkeley%20Law%20Journal%20softwarecombinations060403.pdf](http://www.cs.berkeley.edu/~tlavian/publications/article/Berkeley%20Law%20Journal%20softwarecombinations060403.pdf) 
* Till Jaeger et al (the lawyers that help Harald Welte with  
        gplviolations.org) German GPL comment: [http://www.osscc.net/de/gplger.html](http://www.osscc.net/de/gplger.html) 
 
It is real fun to see that there is not a single serious publication that proves me wrong...

---

### Post by piedro on 2010-07-10
Hallo Jörg! 

Danke, thx, for all the legal information. Actually I already read through a lot of the documents while trying to figure things out. 

As it has been stressed out by many people before joining the whole discussion (in which by the way I absolutely see your point and don't understand why noone of the other side of the whole discussion is willing to start getting somehow constructive in solving the whole issue. It just seems like noone does care anymore or people want to leave things as they are ...), as stresed out before, I think there's two completely different perspectives to the subject: 

1. the developers perspective: 
in which the legal issues, the technical implications and, I think this should also be part of the open source community, questions of manners and respect should be discussed (and somehow resolved!) 

2. the users perspective: 
herein the questions are more like how to get the choice which tools to use, how to integrate cdrtools into the system without spoiling the user experience of a well integrated modern OS, where to find documentation suitable for different levels of experience 

IMO, getting users to be able to use your tools again in a simple way, the ppa of brandon snider may well be a first step, will quickly evolve into the necessity to revitalize the discussion on the developers side of things. (e.g. there's clearly legal problems using libdvdcss for example, still everybody I know is using it and by integrating in mediabuntu repositories it became a defacto standard part of any ubuntu based privat use system) 

A personal note: I really like your stamina to still work on the cdrtools instead of going for a "screw you!" and quit. Please don't! Thanks for your work. 

thx for reading, 
piedro 

p.s.: still haven't had any issues with the ppa install ...

---

### Post by OS/2-User on 2010-07-21
> **schily said:**
> These are pointless rants and not really related  to cdrtools.

People who use the original software instead of the fork
from Debian know that none of the documented bugs from
the Debian variant apply to the original software.

During the past 6 months, more and more people realized
the real cause of the problems and started using the
original software again.

Having Brasero CD write problems ever since I switched from Linux Mint 7  to 8 (Karmic) 7 months ago, I finally wanted to find a fix for it.  While searching for one, I found that apparently the issues with Brasero  on Lucid are even worse. In the process I also came across [http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html),  causing me, to immediately wanting to get rid of that unfortunate  childish Linux cdrkit Kaspertheater and replacing it with cdrtools,  which I am familiar with from OS/2.

Since I couldn't find any up-to-date Ubuntu packages, I ventured to get  cdrtools-2.01.01a80.tar.gz 
and dare trying to compile it. I need to mention, that coming from OS/2,  I'm still pretty green with *nix.
Despite some warnings, <./Gmake.linux> seemed to have finished  successfully, but now I need some assistance, since I'm a bit lost at  this point.

So far, I couldn't find any binaries yet, leading me to assume, that the  compilation process isn't finished yet. If I understand README.compile  correctly, then <./Gmake.linux install> should finish it, but from  here on, I don't know what to expect next, what else exactly is  supposed to be happening.
Since I didn't find any "uninstall" instructions, in case I screw things  up and need to reverse the whole deal, I didn't continue.

In README.compile, section "Using a different installation directory:"  there seems to be the instruction bit missing in the 2nd paragraph, for  installing in /usr/local.

Unless I'm missing something essential here, I'd like to have all the  compilation stuff being finished inside the original tarball directory  structure, so that I then can pick up the binaries and put them in place  of the cdrtools components' symlinks in /usr/bin, pointing to wodim and  genisoimage and uninstall those 2 packages.

So, now any help is appreciated.

---

### Post by mgol on 2010-07-21
> **OS/2-User said:**
> So far, I couldn't find any binaries yet, leading me to assume, that the  compilation process isn't finished yet. If I understand README.compile  correctly, then <./Gmake.linux install> should finish it, but from  here on, I don't know what to expect next, what else exactly is  supposed to be happening.
Since I didn't find any "uninstall" instructions, in case I screw things  up and need to reverse the whole deal, I didn't continue.


First, uninstall what You've messed up. ;) To do this, go to the source directory, invoke:
```
sudo make uninstall
```
Then execute (it will add a special Ubuntu repository for cdrtools):
```
sudo add-apt-repository ppa:brandonsnider/cdrtools
```
(If it doesn't work (I don't know how it's in Mint), add the following to /etc/apt/sources.list:
```
### cdrtools
deb http://ppa.launchpad.net/brandonsnider/cdrtools/ubuntu karmic main
deb-src http://ppa.launchpad.net/brandonsnider/cdrtools/ubuntu karmic main
```
)

Afterwards, update:
```
sudo apt-get update && sudo apt-get upgrade
```
and install proper packages:
```
sudo apt-get install cdrecord mkisofs
```

Now You'll have original cdrtools updated along with the rest of the system. It's far easier than compiling manually from source...

---

### Post by OS/2-User on 2010-07-21
> **mgol said:**
> Now You'll have original cdrtools updated along with the rest of the system. It's far easier than compiling manually from source...
Thanks, Michal.

I actually also had found Brandon's ppa, but since his latest package is *.01a76, while Jörg is already at *.01a80, I foolishly decided to give the whole 'compile it yourself' thingy a try. ;) 
At some point one should learn how to do it, n'est-ce pas?

But apparently, I'm in way over my head with this venture, with no smart geek being around, where I could go to and ask for help.

So, unless some supernatural enlightenment strikes me tonight unexpectedly, then I'll probably follow your much appreciated guidelines :D

---

### Post by mgol on 2010-07-21
Well, before I switched to Brandon's PPA, I used two scripts for installing and uninstalling, both attached.

However, I prefer the repository approach, so I don't use them any more.

If You're so willing to go bleeding-edge, You can try them; however, I am not taking responsibility for any inappropriate behaviour, compiling errors etc. ;)

---

### Post by alfabravoteam on 2010-08-11
> **mgol said:**
> First, uninstall what You've messed up. ;) To do this, go to the source directory, invoke:
```
sudo make uninstall
```
Then execute (it will add a special Ubuntu repository for cdrtools):
```
sudo add-apt-repository ppa:brandonsnider/cdrtools
```
(If it doesn't work (I don't know how it's in Mint), add the following to /etc/apt/sources.list:
```
### cdrtools
deb http://ppa.launchpad.net/brandonsnider/cdrtools/ubuntu karmic main
deb-src http://ppa.launchpad.net/brandonsnider/cdrtools/ubuntu karmic main
```
)

Afterwards, update:
```
sudo apt-get update && sudo apt-get upgrade
```
and install proper packages:
```
sudo apt-get install cdrecord mkisofs
```

Now You'll have original cdrtools updated along with the rest of the system. It's far easier than compiling manually from source...

Nice walkthrough. Do you know about this process working on Lucid? Thanks for your help.

---

### Post by mgol on 2010-08-11
> **alfabravoteam said:**
> Nice walkthrough. Do you know about this process working on Lucid? Thanks for your help.

It's the same... Just change everywhere karmic to lucid and You're done.

---

### Post by alfabravoteam on 2010-08-17
> **mgol said:**
> It's the same... Just change everywhere karmic to lucid and You're done.

I've set it up the way you wrote it down, installing also k3b (well, couple hundred MBs on kde are worthy with this great sw) and it works fine, testing with an existing 3.7GB .iso file at normal speed.

But the thing is that Brasero now shows a lot of disabled plugins (the ones pointing to the killed "wodim and friends"). So, given the lack of settings interface for brasero, is there a way to set it up pointing to the brand new shiny cdrecord? Sorry for the bothering, thanks.

---

### Post by mgol on 2010-08-17
> **alfabravoteam said:**
> But the thing is that Brasero now shows a lot of disabled plugins (the ones pointing to the killed "wodim and friends").

I haven't tried it with Brasero. I don't know what it exactly needs but You can always try to create a link for wodim:
```
cd /usr/bin
sudo ln -s cdrecord wodim
```
and mkisofs:
```
cd /usr/bin
sudo ln -s mkisofs genisoimage
```

---

### Post by Alejandro Nova on 2010-10-15
Thanks for providing that repository.

About legal issues: part of all of this comes from a fundamental incompatibility between principles of Civil Law (on which the Urheberrecht is based) and Common Law (on which the copyright principles are based). That's why Jörg constantly cites the Urheberrecht, and that's what a good portion of Debian legal comentators, who seem to be trained in US copyright, but not in Civil Law, fail to understand. I'll exemplify with the Intellectual Property Act (again: in Civil Law there's Intellectual Property, comprising **solely copyrights**, and Industrial Property, comprising **patents**, utility designs, microchip drawings, and other industry relevant property) of Chile.

The Chapter Four of the Chilean Intellectual Property Act says something like this (translation by me)

> CHAPTER FOUR
MORAL RIGHTS

§ 14. The author, as the sole and exclusive person entitled with the moral right, has while he lives the following rights.

1. The right to revindicate the paternity of the work, assigning to it his name or his known pseudonym;
2. The right **to oppose to any deformation, mutilation, or another modification done without his express and previous authorization**. The conservation, reconstitution or restoration of deteriorated works that have suffered damage that alter or diminish their artistic value won't be considered as such;
3. The right to keep the work unpublished;
4. The right to authorize third persons to finish the inconclused work, who must get first the consentment of the editor or the copyright owner, if there is one, and;
5. The right to demand that his will to maintain the work anonymous or with a pseudonym while it doesn't belong to public knowledge domain.

§ 15. The moral rights is transmissible mortis causa to the surviving spouse and to the successors ab intestato of the author.

§ 16. The rights numbered in the previous sections are **inalienable, and any pact in contrary is null and void**.

Germany, like Chile, is a country of Civil Law, and you'll find something like this in the Urheberrecht. Those rights, enforceable under German law but unknown in the Common Law tradition (which lacks a concept of moral rights independent from copyrights), are outside of the scope of the GPL (a copyright license), and are what enables Jörg to reject Wodim as a modification that denigrates his work. His claims will be unheard in an U.S. court, but, believe me, Jörg would prevail in a German court on this argument alone.

That comes before the argument if the scripts and the code or only the code has to be released under the GPL, or who has active legitimation to proceed in a court if such an incompatibility is found. If I start to redistribute the original CDRecord, like Jörg wishes, who would complain? The patches authors? Wodim authors? The FSF? And what size would be the backlash against them if they do?

So, the people who can sue Jörg are... Debian patchers... FSF... (I don't see any major anti-FOSS company). And Jörg has some serious chances to prevail as long as we get this thing out of a Common Law country and take it to a Civil Law country, with a clear and defined concept of moral rights. Legal issues are a lot more complicated than what was initially thought, and, as you can see, Wodim legal safety is challenged.

So, in plain English: keep using CDRecord happily, no one will sue you ;).

About CDRecord: I had two clear bugs with Wodim, absent with CDRecord.

1. Certain DVD-Rs and DVD+Rs made Wodim believe that it was burning at 24848491891656616x. CDRecord always report the correct speed for the same media.
2. Speed can't be lowered with Wodim, with some media. OTOH, speed always lowers gracefully with CDRecord.

---

### Post by heitormsilva on 2011-11-07
Please, confirm your bad experiences in burning (wodim) here: [https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/481536](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/481536)

---

### Post by doru001 on 2012-04-10
I wish to thank Schily for his unequaled program. Several bugs which I had with wodim went away. I could not mount audio and video cd's and dvd's after successful burning with wodim, I could not mount any disc copied with wodim, I could not blank my dvd's with wodim. 

I installed cdrtools following instructions at: [http://ubuntuforums.org/showpost.php?p=5552555&postcount=5](http://ubuntuforums.org/showpost.php?p=5552555&postcount=5) (from thread: [http://ubuntuforums.org/showthread.php?t=851707](http://ubuntuforums.org/showthread.php?t=851707)). (I also recommend [http://www.troubleshooters.com/linux/coasterless.htm](http://www.troubleshooters.com/linux/coasterless.htm).) 

Alejandro Nova: thank you for your competent exposition. However, I have no idea in my wildest dreams why would or could anyone sue the author of such a good program. On the other hand, your explanation shows clearly that Ubuntu can very safely include unmodified Schily's cdrtools into its distribution.

---


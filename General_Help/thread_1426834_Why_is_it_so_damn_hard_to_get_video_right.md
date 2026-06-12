---
title: "Why is it so damn hard to get video right?"
date: 2010-03-10
forum: General Help
---

### Post by smcnally on 2010-03-10
I always come back to Ubuntu because I love it.  I love everything about it except for the fact that its video support is downright horrible.  Why is this the Achilles Heel of Ubuntu?  I run a P4 with 1.5 GB of RAM and run an nvidia GEForce 6200...Not the most up-to-date hardware, but I should be able to watch a youtube video in a resolution larger than 640x480 without it tearing and being unwatchable, shouldn't I?  Sorry for the rant, but I've been messing with this for the last few weeks and I'm about to fork the money over for Windows 7 just to have this PC back up and running in an acceptable way. I've done every suggestion I've found here with Flash and nvidia drivers and think I'm just screwed now.](*,)

---

### Post by blur xc on 2010-03-10
imo- your computer doesn't have enough oomph to run flash video.  Fact- flash uses more cpu in Linux and Mac OSX than in Windows.  Fact- generally speaking, video cards are better supported in Windows.  So - what is an acceptable setup for a windows computer isn't so much in a Linux computer.  That being said- my desktop pc runs flash very, very well, with only a few exceptions...

The Intel Atom netbooks in my house? Not so much...

BM

---

### Post by Scunizi on 2010-03-10
Hopefully you didn't use "Automatix" 1 or 2.. it simply messes with your system. If you tried to install the nvidia drivers that can be downloaded directly from their site, then without the proper instruction you'll have issues.  If you enabled the drivers from System>Admin>hardware drivers and you had a choice of 2 different one's, choose the one with the lower version number.

I ran a P4 with a 6600gt AGP with no issues until the motherboard gave up the ghost... for the second time due to a power outage.

If you haven't been on IRC yet give it a shot.  The server to connect to is irc.freenode.net and the channel is #ubuntu.  Install and learn a little about "irssi" a cli IRC client so when you're configuring video you can shut down the gui if necessary and still be able to talk.

---

### Post by smcnally on 2010-03-10
> **blur xc said:**
> imo- your computer doesn't have enough oomph to run flash video

Ok...now that is just crazy talk no matter how you slice it.  If what you say is true, then how can you explain this?  [http://www.youtube.com/smcnally75#p/u/6/X9BD6C6s23Y](http://www.youtube.com/smcnally75#p/u/6/X9BD6C6s23Y) The PC in this video is the same PC I'm running now but, at the time, I was running PCLinuxOS.  It had no problems running heavy desktop effects with multiple flash videos running at the same time.

> **Scunizi said:**
> Hopefully you didn't use "Automatix" 1 or 2.. it simply messes with your system. If you tried to install the nvidia drivers that can be downloaded directly from their site, then without the proper instruction you'll have issues.  If you enabled the drivers from System>Admin>hardware drivers and you had a choice of 2 different one's, choose the one with the lower version number.

I ran a P4 with a 6600gt AGP with no issues until the motherboard gave up the ghost... for the second time due to a power outage.

If you haven't been on IRC yet give it a shot.  The server to connect to is irc.freenode.net and the channel is #ubuntu.  Install and learn a little about "irssi" a cli IRC client so when you're configuring video you can shut down the gui if necessary and still be able to talk.

I haven't used Automatix.  I tried both installing the latest from Nvidia and using the suggested ones from the hardware manager.  When I used the Nvidia drivers from their site I followed these instructions [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by Scunizi on 2010-03-10
the one thing those instructions left out was to use synaptic and uninstall the nvidia bits provided by ubuntu on hte initial install.  If you no longer have a gui to go to for synaptic package manager then use aptitude from the cli.  After the removal try reinstalling the drivers again.. you also might need to install build-essential which has the compiler libraries needed for the installer to do it's thing.

---

### Post by dcstar on 2010-03-11
> **smcnally said:**
> I always come back to Ubuntu because I love it.  I love everything about it except for the fact that its video support is downright horrible.  Why is this the Achilles Heel of Ubuntu?  I run a P4 with 1.5 GB of RAM and run an nvidia GEForce 6200...Not the most up-to-date hardware, but I should be able to watch a youtube video in a resolution larger than 640x480 without it tearing and being unwatchable, shouldn't I?  Sorry for the rant, but I've been messing with this for the last few weeks and I'm about to fork the money over for Windows 7 just to have this PC back up and running in an acceptable way. I've done every suggestion I've found here with Flash and nvidia drivers and think I'm just screwed now.](*,)

[http://ubuntuforums.org/showthread.php?t=1349553](http://ubuntuforums.org/showthread.php?t=1349553)

---

### Post by Dayofswords on 2010-03-11
[IMG]http://imgs.xkcd.com/comics/supported_features.png[/IMG]
i dont use fullscreen flash

---

### Post by asmoore82 on 2010-03-11
The Gnash flash-compatible plugin calls out to a real video player to render video
so it works much better in that regard.

But the last time I checked it was not allowed in to view Hulu content,
works great with youtube though.

---

### Post by Dayofswords on 2010-03-11
> **asmoore82 said:**
> 
But the last time I checked it was not allowed in to view Hulu content,
works great with youtube though.
how come? needs adobe?

---

### Post by ankspo71 on 2010-03-11
> **smcnally said:**
> Ok...now that is just crazy talk no matter how you slice it.  If what you say is true, then how can you explain this?  [http://www.youtube.com/smcnally75#p/u/6/X9BD6C6s23Y](http://www.youtube.com/smcnally75#p/u/6/X9BD6C6s23Y) The PC in this video is the same PC I'm running now but, at the time, I was running PCLinuxOS.  It had no problems running heavy desktop effects with multiple flash videos running at the same time.

Wow, that's really good for KDE ;) . I don't have any answer as to why that is, but from my experience with Ubuntu, flash player is high on the cpu usage side. Maybe it's not as much in PClinuxOS with KDE?

---

### Post by ankspo71 on 2010-03-11
Hi Again,
I just tried to do everything in that video (including watching the same video), and my cpu usage kept tipping 100%. It was compiz at 50% (as soon as I made the cube transparent) and flash player making firefox-bin at 50%. This is a 3.0 pentium 4, 2gb ram, 512mb nvidia 8400gs graphics.

---

### Post by smcnally on 2010-03-11
> **Dayofswords said:**
> [IMG]http://imgs.xkcd.com/comics/supported_features.png[/IMG]
i dont use fullscreen flash
That's pretty funny! :p

> **asmoore82 said:**
> The Gnash flash-compatible plugin calls out to a real video player to render video
so it works much better in that regard.

But the last time I checked it was not allowed in to view Hulu content,
works great with youtube though.
This is kind of what I'm getting at...things like this aren't really answers but more like band-aids that don't fully fix the issue.  Video issues these days shouldn't even be a problem.  I know they are and there isn't much we can do about it, but it's just frustrating that something that should be so simple can be such a pain in the butt.

> **ankspo71 said:**
> Hi Again,
I just tried to do everything in that video (including watching the same video), and my cpu usage kept tipping 100%. It was compiz at 50% (as soon as I made the cube transparent) and flash player making firefox-bin at 50%. This is a 3.0 pentium 4, 2gb ram, 512mb nvidia 8400gs graphics.
Then I guess the issue is with gnome.  Maybe I'll have to go back to PCLinux OS or just get Windows 7.

---

### Post by TBABill on 2010-03-11
Another interesting aspect to this question. Ubuntu on my machine (specs not necessary for this comparison) runs flash videos "glitchy" with tearing, pausing, etc. 64-bit system, all updates installed, 64-bit flash, etc. Not great performance and a fresh install.
 
Mint 8 64-bit, same story on the install and updates. However, flash is awesome and near flawless.
 
What did the folks over at Mint figure out and implement that is different from Ubuntu, since their distro is based on Ubuntu? (Yes, Karmic 9.10 and Mint 8) Pulse Audio has been mentioned as a must remove or tweak on ubuntu, but it is present on the install of Mint as well and not causing errors.
 
Mint figured it out and I haven't found an answer to what it is they implement differently to make such a huge difference.

---

### Post by Grenage on 2010-03-11
> **smcnally said:**
> This is kind of what I'm getting at...things like this aren't really answers but more like band-aids that don't fully fix the issue.  Video issues these days shouldn't even be a problem.  I know they are and there isn't much we can do about it, but it's just frustrating that something that should be so simple can be such a pain in the butt.

It's Adobe's poor Linux player that causes most of the problems.

Are you running proprietary Nvidia drivers?  Have you tried downloading and manually installing the flash plug-in from Adobe's site?  My old HP laptop with integrated intel graphics runs full-screen flash no problem, but I've seen rigs with 5x the power have the issues you describe.

---

### Post by ankspo71 on 2010-03-11
I found a PPA for kde3.5 (for karmic) if you're interested in it.
[https://launchpad.net/~kde3-maintainers/+archive/ppa](https://launchpad.net/~kde3-maintainers/+archive/ppa)
There are also PPA's for nvidia drivers too, in addition to the above advice.

I need to mention that I'm not running Ubuntu 9.10, I'm using Ubuntu Lucid Alpha 3. So far nothing has slowed down this computer's new hardware yet, except for now... with the heavy transparency in the compiz cube plus using flash experiment I mentioned above. Fullscreen flash video is not a problem for me, neither is gaming, it's just when I combined the extra compiz effects and flash together.

---

### Post by smcnally on 2010-03-11
> **Grenage said:**
> It's Adobe's poor Linux player that causes most of the problems.

Are you running proprietary Nvidia drivers?  Have you tried downloading and manually installing the flash plug-in from Adobe's site?  My old HP laptop with integrated intel graphics runs full-screen flash no problem, but I've seen rigs with 5x the power have the issues you describe.

Yes, I am running the proprietary drivers.  I have tried the flash plugin from Adobe's site with no noticeable changes.  

Now, one thing that has me even more stumped... This morning I decided to burn a PCLinuxOS image and run the LiveCD.  I went to YouTube, played a video, went to full screen, and it ran nice and smooth.  So I took a quick video of it with my phone and then loaded up Ubuntu and did the same with the same video.  Now Ubuntu is playing full screen video fine for some reason unless I go over 480p.  I'm wondering if it will still work when I get home from work.

I may just install PCLinuxOS fully and see how it runs.  Maybe my system will play nicer with a KDE desktop, I don't know.

---

### Post by TBABill on 2010-03-13
Mandriva and SUSE (KDE Both) ran videos MUCH smoother than Ubuntu for me. But, Mint 8 is the first GNOME distro I have run with all necessary codecs, drivers, etc., that runs video perfectly. I can't say why, but it's better than Ubuntu that it's based upon. There's a fix obviously implemented in Mint and I wish it'd be migrated into Ubuntu (besides just turning desktop effects off, tweaking settings, etc., only to get mediocre improvement).

---

### Post by QIII on 2010-03-13
A lot of this has to do with how poorly Flash is designed for Linux (my apologies to the Linux Flash Player Team).

Open the Task Manger in Windows and watch how much of your CPU capacity is taken up when you run Flash.

Now do the same with the System Manger in Linux (I use gkrellm).

The difference is appalling.  Continue to work on what you can and take any advice you can get here, of course.  But Flash for Linux is a resource hog of biblical proportions.

---

### Post by detroit/zero on 2010-03-13
> **blur xc said:**
> imo- your computer doesn't have enough oomph to run flash video.  Fact- flash uses more cpu in Linux and Mac OSX than in Windows.  Fact- generally speaking, video cards are better supported in Windows.  So - what is an acceptable setup for a windows computer isn't so much in a Linux computer.  That being said- my desktop pc runs flash very, very well, with only a few exceptions...

The Intel Atom netbooks in my house? Not so much...

BM
I don't believe I just read that here.

A P4, a gig and a half of RAM, and a GeForce 6200 video card isn't enough of a system to run a flash video?

What planet are you from, man?

I have an old P1 400MHz box with no video card running Windows 98 laying around that plays flash videos fullscreen and does it just fine.

Flash is just crap in Linux. Always has been, probably always will be.

---

### Post by QIII on 2010-03-14
Flash my be crap in Linux, but Linux is not to blame.

---

### Post by tcoffeep on 2010-03-14
> **QIII said:**
> Flash my be crap in Linux, but Linux is not to blame.

Yeah, how dare Adobe focus on maintaining Flash for the more popular OSes, with Linux somewhere in the backdrop. How *dare* they?

---

### Post by Grenage on 2010-03-15
> OSes

I think you mean OS - their Mac support is also quite poor.

---

### Post by QIII on 2010-03-15
> **tcoffeep said:**
> Yeah, how dare Adobe focus on maintaining Flash for the more popular OSes, with Linux somewhere in the backdrop. How *dare* they?

I was making no commentary on Adobe's business model of catering to a larger user base.

That makes good business sense.

I was merely stating that the poor quality of Flash on Linux is not an indictment of Linux.

---

### Post by clhsharky on 2010-03-15
HI

[http://www.adobe.com/products/flashplayer/systemreqs/](http://www.adobe.com/products/flashplayer/systemreqs/)

System requirements for Adobe flash, higher than most think.


Sharky

---

### Post by QIII on 2010-03-15
I think Adobe is fooling themselves or attempting to fool others with regard to Linux.

I have a quad core 3.0 GHz system with 8GB of memory.

I find that Flash's use of system resources is acceptable in Windows and appalling in Linux.

---

### Post by kazakore on 2010-03-24
Similar problem with tearing video but I get it with Everything.

Media players suck as VLC or MPlayer. Web Flash (although not noticed Flash being overly heavy on my machine, like some have commented.) But worst and most annoyingly! In wave editors while playing back samples I am wanting to edit, the location bar splits and is really distracting.

Tried pretty much everything in the thread. Native driver, Nvidia 185 and 173 (the two in Hardware Drivers.) Followed the instructions to make the Nvidia settings loaded at start-up. Made sure all VSync are on, have no Desktop Effects or Compiz.

Am running the 32bit version due to some of the software I use. Card is a 8800m gtx laptop card in a Clevo D901C / Sager NP9262.

Yet to try KDE and see if it's the same that side but starting to think that could be the next move...

---

### Post by javyn999 on 2010-03-24
FYI, I had this problem with my older system too.  

Athlon 2.0 ghz, 2 gigs ram, Geforce 6200.

In Firefox, fullscreen flash is awful.

In Opera, even worse.

Then I got a wild hair a few weeks ago and installed Chrome.  No idea why, but Flash just works in Chrome.  No trouble whatsoever, I can watch fullscreen youtube just like I could in Windows.

May want to give it a shot.

---

### Post by desnaike on 2010-03-24
Hey I hope this helps I've experienced the same problems with flash and multimedia for quite sometime I started with linux 5 years ago  then about 3 yrs ago I realized the plugins were running thru symlinks so I copied the plugins to each browsers plugin folder now 3 years of flawless multimedia try it worked for me.

---

### Post by kazakore on 2010-03-24
Please read my post. I also get issues with normal programs, not only video playback and most definitely not only with Flash. Have tried making my own thread, which got ignored.

---

### Post by desnaike on 2010-03-24
> **kazakore said:**
> Please read my post. I also get issues with normal programs, not only video playback and most definitely not only with Flash. Have tried making my own thread, which got ignored.


Really sounds like a codec problem, with my setup I install all codecs not just those recommended in various tutorials  on the forums/net and have not experienced any problems for years. After codecs I would really make sure I had the right video card drivers.

---

### Post by javyn999 on 2010-03-24
never had a problem w/ codecs either.  but most of what i have i convert to xvid.

---

### Post by kazakore on 2010-03-25
> **desnaike said:**
> Really sounds like a codec problem, with my setup I install all codecs not just those recommended in various tutorials  on the forums/net and have not experienced any problems for years. After codecs I would really make sure I had the right video card drivers.

How can it be a codec problem when I'm not talking about playing videos? It's very obviously a vertical sync problem but the settings in the Nvidia driver (and editing the xinitrc file to make it load them) seems to make no difference. Don't know if different desktop environment could make a difference but I am fairly used to Gnome now.

---

### Post by desnaike on 2010-03-25
> **kazakore said:**
> How can it be a codec problem when I'm not talking about playing videos? It's very obviously a vertical sync problem but the settings in the Nvidia driver (and editing the xinitrc file to make it load them) seems to make no difference. Don't know if different desktop environment could make a difference but I am fairly used to Gnome now.


Then I would say it's the video driver, I have nvidia geforce 6200 256 ram all nvidia drivers work for me 96 is slow,173 some jerkiness with multiple apps open 185 perfect 190 gave me the problems you are experiencing, so try them if none solve your problem hit the multimedia room on theforums

check this [http://www.function13.net/2010/02/22/ubuntu-9-10-karmic-koala-fix-video-tearing-with-compiz-nvidia-geforce-gts-250/](http://www.function13.net/2010/02/22/ubuntu-9-10-karmic-koala-fix-video-tearing-with-compiz-nvidia-geforce-gts-250/)

---

### Post by kazakore on 2010-03-25
I agree it's a driver issue. Have tried both Nvidia drivers in the repository and the native Linux one and no joy. Have followed instructions and made sure VSync is ticked and loaded when the computer boots.

Have desktop effects (Compiz) set to Off although some people say to change the settings in that to get it to work properly so maybe I'll try enabling it. Will also try the drivers from their site as have only tried the ones that show up in Hardware Devices.

Thanks for replaying.

---

### Post by kazakore on 2010-03-25
OK downloaded latest driver and following instructions on the page you linked to but I can't run the installer. What am I doing wrong?

I have CDed into the folder the driver is in and type sudo NVIDIA...... (full driver name inclusing .run) and nothing happens. Try sudo ./NVIDIA...... as that is what they have put although I thought the probably meant ~/ with the assumption you would save the file in your home director.

Any help appreciated.

EDIT: Sorry, my mistake. I missed the make the file executable bit. All sorted and installed now. Just to test out if it's solved my issue.

---


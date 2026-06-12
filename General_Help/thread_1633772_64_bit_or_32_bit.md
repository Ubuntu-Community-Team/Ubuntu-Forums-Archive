---
title: "64 bit or 32 bit?"
date: 2010-11-29
forum: General Help
---

### Post by Wanderin_ponderer on 2010-11-29
Hi all,

When 10.04 came out I decided to upgrade and figured it was finally time to switch to 64 bit as well since I had the hardware.  Unfortunately, I've been encountering many more problems than usual including, but not limited to: Flash problems that have not been fixed by any of the many threads I've found, wireless printing problems, and random restarts that close all my programs without saving and return me to the login screen.

On the one hand, I'm not sure I want to do a 32 bit re-install since I always worry I'm going to lose something important during the back up, and making a working ISO disc in Jaunty was a pain in the neck.

On the other hand, I've grown tired of being unable to surf the web while using flash apps in another window, finding a cord to use for every printer I want to use, and the constant worry that my OS will restart in the middle of an important project.

In short, has anyone been experiencing these problems in 32-bit Lucid Lynx?  I don't want to go through the hassle if I'm just going to experience the same problems (especially the 'restart' problem).

Thanks in advance for any helpful responses!

---

### Post by Slim Odds on 2010-11-29
System specs?

Have you looks at the logs to see what might be causing your "restart' problem?

Many of us have used the 64 bit version for a long time without issues.

---

### Post by akand074 on 2010-11-29
I've strictly been using 64 bit Ubuntu since I moved to Linux. No problems with anything. I would give 64 bit a try (do a clean install). If you have problems then you could always switch back. You shouldn't though.

---

### Post by oldos2er on 2010-11-29
If you're using 64-bit Ubuntu, you should use the 64-bit flash plugin, which unfortunately is not in the repositories. [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz)

---

### Post by I'mGeorge on 2010-11-29
it's easy if you have a dual core processor than 64 bit if you don't 32. In the current state of ubuntu you can get the same applications in 64 or 32 bit architecture, there's no difference anymore regarding the available apps

---

### Post by Wanderin_ponderer on 2010-11-29
Limited Specs: Lucid Lynx (10.04) 64 bit, Kernal Linux  2.6.32-25-generic, Gnome 2.30.2, Intel(R) Pentium(R) Dual  CPU  T3400  @  2.16GHz

@Slim Odds: This is my first time posting a problem like  this, so I'm not sure if you need anything more than this, but I  thought these looked the most pertinent to your question.  

As  for checking the logs, I have no idea where to begin, but I didn't think  you'd want me to post everything and have to sift through it all.[IMG]http://ubuntuforums.org/images/icons/icon5.gif[/IMG]

@oldos2er:  Thanks, I'll give it a try, though I've tried installing it before to  no avail, and none of the suggestions from other threads have worked.[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

@anyone  else who's still interested: I'm running 64 bit already (I figured  since I had a dual core processor and it had been long enough, why not?)  but I'm experiencing problems I never experienced on my old 32 bit  Jaunty and Karmic. Mostly, they're software related (Flash and hard to  find drivers), but my big worry is the restart problem.

When it  first happened a couple months ago I found a thread that said it was  related to Adobe no longer offering the 64 bit Flash version, and  indeed, it only happened when I'd fall asleep listening to Pandora or  watching on-line tv--so I quit doing that.

However, today it  happened while I was typing a thank you note, and I thought it was time  to look into switching back to 32 bit just to be safe. 

[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]  Basically, I'm just wondering if there are a few people out there  running 32 bit Lucid Lynx who could tell me if they've experienced many  problems, or if it's been running like an LTS dream [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by Slim Odds on 2010-11-29
As I mentioned, tons of us use the 64 bit version of Ubuntu and have for quite some time. The main point that I was making is that the 64 bit version is fine and that if you are having problems it is something specific to either the machine that you have (perhaps hardware related) or the specific installation that you have (some combination of programs/drivers maybe, etc.).

Looks for any strange messages in /var/log/syslog

---

### Post by Wanderin_ponderer on 2010-11-29
[IMG]http://ubuntuforums.org/images/icons/icon3.gif[/IMG]Update: I found this in my log file,

Nov 29 14:10:52 Wanderer polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session1 (system bus name :1.17, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.utf8) (disconnected from bus)
Nov 29 14:10:53 Wanderer gnome-keyring-daemon[1208]: dbus failure unregistering from session: Connection is closed
Nov 29 14:10:54 Wanderer gnome-keyring-daemon[1208]: dbus failure unregistering from session: Connection is closed

-----
I searched some threads which suggest it is an X crash probably caused by a software/hardware 'fitting' problem so to speak.  Most of the people on the thread indicated having a 64 bit system and Flash running when it crashed, so I'm hoping by taking oldos2er's advice (none of the usual Flash problems so far!) I'll have solved the other problem.  

The only thing I can think is I had a forgotten Firefox window minimized on another desktop, and I just panicked because I was working instead of playing when this crash occurred.

Of course, if it happens again, I feel I'll have no choice but to switch back to 32 bit since I imagine that software will 'fit' better my hardware (and as is probably clear, I'm too novice to be doing any significant internal work).
-----
Since I just posted the bug, and have only had the 64 bit flash installed for a few hours, I'll leave this unmarked [solved] for now.

Thanks for everyone's help [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by I'mGeorge on 2010-11-30
> **Wanderin_ponderer said:**
> 
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]  Basically, I'm just wondering if there are a few people out there  running 32 bit Lucid Lynx who could tell me if they've experienced many  problems, or if it's been running like an LTS dream [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

Using open source software that you can constantly upgrade (unlike windows) so you could have the newest available apps sometimes could be tricky, as some small bugs or incompatibilities could occur for 32 and 64 bit alike.

---

### Post by cascade9 on 2010-11-30
> **oldos2er said:**
> If you're using 64-bit Ubuntu, you should use the 64-bit flash plugin, which unfortunately is not in the repositories. [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz)

+1. Makes a big difference. (though I dont think it will fix your restarting problems) 

> **I'mGeorge said:**
> it's easy if you have a dual core processor than 64 bit if you don't 32. In the current state of ubuntu you can get the same applications in 64 or 32 bit architecture, there's no difference anymore regarding the available apps

Close. All the AMD dualcores are 64bit capable, but not all the intels are. Core Duo are not 64bit capable, but are dual cores (T2XXX, L2XXX, U2XXX) 

[http://ark.intel.com/ProductCollection.aspx?familyId=22731](http://ark.intel.com/ProductCollection.aspx?familyId=22731)

---

### Post by I'mGeorge on 2010-11-30
> **cascade9 said:**
> 
Close. All the AMD dualcores are 64bit capable, but not all the intels are. Core Duo are not 64bit capable, but are dual cores (T2XXX, L2XXX, U2XXX) 

[http://ark.intel.com/ProductCollection.aspx?familyId=22731](http://ark.intel.com/ProductCollection.aspx?familyId=22731)

True but those Core Duo processors aren't manufactured anymore since 2008 [http://en.wikipedia.org/wiki/Yonah_(microprocessor)](http://en.wikipedia.org/wiki/Yonah_(microprocessor))) so I've didn't felt like making a specification about them.

---

### Post by cascade9 on 2010-12-01
> **I'mGeorge said:**
> True but those Core Duo processors aren't manufactured anymore since 2008 [http://en.wikipedia.org/wiki/Yonah_(microprocessor)]("http://en.wikipedia.org/wiki/Yonah_%28microprocessor%29")) so I've didn't felt like making a specification about them.

I would have (I did!) Just because they are no longer in production doesnt mean that people wont get confused, I've had to tell several people that Core Solo + Core Duo are 32bit only.

---

### Post by I'mGeorge on 2010-12-01
> **cascade9 said:**
> I would have (I did!) Just because they are no longer in production doesnt mean that people wont get confused, I've had to tell several people that Core Solo + Core Duo are 32bit only.

The thing it's if you have a 32 bit only processor in two years (assuming that he/she bought the processor in the last year of production) most likely you should probably know by that already, 'cause if you don't it means you're completely atechnical regarding computers, and if this it's the case I won't really recommend using linux, 'cause it will probably make your life really miserable.

---

### Post by oldos2er on 2010-12-01
> **Wanderin_ponderer said:**
> @oldos2er:  Thanks, I'll give it a try, though I've tried installing it before to  no avail, and none of the suggestions from other threads have worked.

Here's an easy way to install it: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

---

### Post by 0949er on 2010-12-01
OP, in regards to your computer crashing and restarting, are you talking about the actual GUI only? (and no the physical computer?)

If so, do you run dual monitors by any chance?

---

### Post by Wanderin_ponderer on 2010-12-01
> OP, in regards to your computer crashing and restarting, are you talking  about the actual GUI only? (and no the physical computer?) If so, do you run dual monitors by any chance? 

Yes, it was only the GUI that was crashing; that is, until yesterday.  It crashed again, but this time it froze before bringing up the login screen (just got stuck on the default purple Lynx background).  Also, I was absolutely positive there were no firefox windows running during that crash. (And in answer to your 2nd question, no I do not run dual monitors).

Since the problem seemed to be getting worse, I just decided to play it safe and go back to a 32 bit version as I've rarely had problems with other such versions on my system.  

Next time I upgrade my hardware I'll try to upgrade my software again as well, but I love the free aspect of Linux for good reason.

I also really like the community aspect of Linux, so thank you everyone for your advice!  [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by 0949er on 2010-12-01
enjoy :)

---

### Post by cascade9 on 2010-12-02
> **I'mGeorge said:**
> The thing it's if you have a 32 bit only processor in two years (assuming that he/she bought the processor in the last year of production) most likely you should probably know by that already, 'cause if you don't it means you're completely atechnical regarding computers, and if this it's the case I won't really recommend using linux, 'cause it will probably make your life really miserable.

LOL. Theres lot of people who have no intrest in hardware, "as long as it does XXX and YYY". They tend to have no idea if they have a 32-bit or 64-bit CPU.......and even some of the people with an interest in hardware dont know. The number of times I've heard 'what, my CPU is 64-bit? Why did it ship with vista 32-bit then?' is amazing.

---


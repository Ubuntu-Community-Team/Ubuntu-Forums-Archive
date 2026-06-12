---
title: "nbcolympics live extra"
date: 2012-07-28
forum: General Help
---

### Post by TVAbuntu on 2012-07-28
Anyone get this working in the US?

It won't register my account, just kicks back to the sign in screen. Ubuntu 12.04 and Kubuntu 12.04.

Works fine in OSX Lion and XP (in virtualbox).

Should just be flash based, so not sure why this isn't working. Linux is not listed in the "minimum requirements" but it's just Flash, right?

edit: changing useragent on chromium-browser or Firefox doesn't help.

---

### Post by ElderDryas on 2012-07-28
Saw this behavior during the US Olympic Trials as well. Not sure what is causing it, but it does happen in both Xubuntu and Ubuntu 12.04, and does NOT happen with the same versions of FF and Flash in SalixOS 13.37 (Xfce) and Linux Mint 13 (Xfce).

---

### Post by benenglish on 2012-07-28
> **TVAbuntu said:**
> Anyone get this working in the US?
Not me and not happy about it.

I'm running 11.10 with FF 14.0.1.

My cable account includes the required stations. I've used my account credentials and email credentials (they're different) to no avail. Both signins are verified good; I can open them in a new window and go directly to them with no problem.

At NBCOlympics.com, though, after entering the credentials the browser (both Firefox and Chrome) bounces right back to the start page. If I select a stream and click directly on the video box, I get the pop-up box to select a provider. I then click on my cable provider, the box goes away...then the same provider selection box reappears in an endless loop.

When I told my cable customer support that I was running Linux, they simply said they couldn't help me.

I may have an old Windows box around here somewhere that I can plug in and I can run various Windows versions in a vm.  Either would take a bit of time to set up and, on general principle, I'd like to exhaust my Ubuntu alternatives first.

So - Anyone with ideas?

---

### Post by ElderDryas on 2012-07-28
> **benenglish said:**
> So - Anyone with ideas?

Seeing as how I have trying to get someone interested in this problem since the US Olympic Trials, the Olympics will probably be over before some one cares, and then it'll be moot.

I'd grab a copy of Linux Mint 13 (choose your favorite DE)(Flash is installed by default), put it on a USB stick, boot the LiveUSB and watch the Games.  You'll have to validate every time you boot, but you <will> be able to validate :)

---

### Post by benenglish on 2012-07-28
> **ElderDryas said:**
> ...grab a copy of Linux Mint 13...boot the LiveUSB and watch...
That seems like a good way to go.  Thanks; I really appreciate it.

---

### Post by TVAbuntu on 2012-07-28
I'll try LM also. Thanks for the tip.

I can confirm this bug also for Fedora 17 and Opensuse Tumbleweed.

Very interested in any ideas as to why it works in Mint.

---

### Post by legoman666 on 2012-07-28
Seeing this issue on Mint 11 and Mint 13. Going to try spoofing the UA...

Didn't work.

---

### Post by LeastCriminal on 2012-07-28
A Mint 13 live USB drive is working for me. That solves the immediate problem but is not ideal.

A bug has been filed, please mark it as affecting you: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1030365](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1030365)

---

### Post by legoman666 on 2012-07-28
> **LeastCriminal said:**
> A Mint 13 live USB drive is working for me. That solves the immediate problem but is not ideal.

A bug has been filed, please mark it as affecting you: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1030365](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1030365)

Working for me on Firefox 15 on Mint 13. Took me so long to get it to work that the event I wanted to originally watch is now over.

---

### Post by EricCFlem on 2012-07-28
As per [this post]("http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html") on the Adobe website:

Step One: Install HAL

sudo apt-get install hal

Step Two: Quit your web browser

Step Three: Clean out the Adobe Flash folder:

cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2

This process worked for me.  In my case, I'd been able to go to nbcolympics.com and click the log to begin the verification process, but never given the chance to enter my Comcast credentials.  Doing the steps above fixed everything.

---

### Post by benenglish on 2012-07-28
> **EricCFlem said:**
> This process worked for me.Same here.
I owe you a beer.  
My doctor owes you a beer for how much you've lowered my blood pressure.
My family owes you a beer for how much you've improved my mood.
:D

---

### Post by willenium on 2012-07-28
This did not work for me.  Sorry, when there is a better fix, please post.
Edit:  It worked by using the embedded browsers in Ubuntu, which are Firefox and Chromium.  I use Google Chrome exclusively so I tried the other ones and they worked.  Thanks.  I am guessing that this has to do with the fact that Chrome carries its own Flash driver.

---

### Post by TVAbuntu on 2012-07-28
> **EricCFlem said:**
> As per [this post]("http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html") on the Adobe website:

Step One: Install HAL

sudo apt-get install hal

Step Two: Quit your web browser

Step Three: Clean out the Adobe Flash folder:

cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2

This process worked for me.  In my case, I'd been able to go to nbcolympics.com and click the log to begin the verification process, but never given the chance to enter my Comcast credentials.  Doing the steps above fixed everything.


Lovely, thanks so much. Worked for me.

I will mark thread solved.

By the way, Mint KDE maya 64 bit did not work for me.

---

### Post by EricCFlem on 2012-07-28
I had the same experience on another computer, but just had a thought which I tested out.  In Chrome, go to the chrome://plugins page, then click the blue "details" or the plus sign icon in the upper right.  Now you should see two Flash options.  One is the built-in Pepper API flash, the other is the traditional NPAPI Flash that you installed manually in Ubuntu (or came installed in Mint).  To get the Olympics streaming in Chrome, simply disable the built-in Pepper Flash (which should have a newer version number).

Yes, obviously this puts you at a lower version of Flash, and also brings back some of the security issues that the Pepper API solves, but if you want Olympics, this is a fix.

---

### Post by rewyllys on 2012-07-28
Just tried viewing nbcolympics.com in Linux Mint 13 with Cinnamon, and had no problems at all. For example, using the Chromium browser I watched two gorgeous full-screen videos of Jordyn Wieber: on the uneven bars and on the floor mat.

But I want to pay full credit to Ubuntu-Freak's "Comprehensive Multimedia & Video Howto: New Version".:popcorn:  It's at
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

About a week ago, I went through the New Version and incorporated everything in it into my desktop computer.  It took a good five minutes for me to download and install all the stuff that Ubuntu-Freak's command-line commands handle.

Doing so solved a problem for me and may well have helped with my viewing of nbcolympics.com.

I heartily recommend this "New Version".

---

### Post by legoman666 on 2012-07-28
[http://www.anthonynotes.com/2012/07/28/more-2012-olympics-tech-issues-nbc-olympics-website-streaming-on-linux/](http://www.anthonynotes.com/2012/07/28/more-2012-olympics-tech-issues-nbc-olympics-website-streaming-on-linux/)

Worked for me on Mint 11 FF 15.

---

### Post by clhcpa on 2012-07-29
Thank you!  What a relief...thank you so much for sharing your success.

---

### Post by benenglish on 2012-07-30
My enthusiasm was premature.  In my case, the Adobe fix allowed me to get my credentials verified by NBC.  Playback, however, never happened.  The video window stayed black no matter what I tried.

I used a LiveDVD of Mint 13 (as suggested earlier) and had good success.  It wasn't perfect.  I couldn't capture the streams with my normal download helper and NBC insists on inserting lots of commercials that occasionally crash the page.  In the latter instance, I just refresh and click the progress bar to go to a spot beyond where the commercial had been inserted.

Still, there's lots of good info in this thread and I wanted to thank everyone for their contributions.  I'm sure that anyone will, using this info, be able to find a way to get over the hurdles that NBC throws at us.

Addendum: I'm rather jealous of folks in European Broadcasting Union countries.  It's my understanding they can go to [http://www.eurovisionsports.tv/london2012/index.html](http://www.eurovisionsports.tv/london2012/index.html) and stream all the same (if not more) content without having to plug in credentials from a local cable company as we are forced to do in the United States.

---

### Post by mikecomaroto on 2012-07-30
Worked for me, too. Thank you!

---

### Post by sumithar on 2012-07-31
> **EricCFlem said:**
> As per [this post]("http://helpx.adobe.com/x-productkb/multi/flash-player-11-problems-playing.html") on the Adobe website:

Step One: Install HAL

sudo apt-get install hal

Step Two: Quit your web browser

Step Three: Clean out the Adobe Flash folder:

cd ~/.adobe/Flash_Player
rm -rf NativeCache AssetCache APSPrivateData2

This process worked for me.  In my case, I'd been able to go to nbcolympics.com and click the log to begin the verification process, but never given the chance to enter my Comcast credentials.  Doing the steps above fixed everything.


Thanks.

---


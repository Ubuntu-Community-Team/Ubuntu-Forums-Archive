---
title: "Karmic crashes due to Ati drviers???"
date: 2010-02-09
forum: General Help
---

### Post by Struki on 2010-02-09
Hm try to keep it short and clear...

Upgraded from 9.04 - 9.10 via fresh install. (some months ago)

I'm having random crashes, symptoms:

1. First I get "screen freeze" or my desktop freezes for no apparent reason
2. After a few seconds screen turns black or white or brownish
3. I can here the computer running, my hdd light is working like mad, I can hear the hard spining, and wifi is active(but the screen is still black).
 - then I reboot-
4. At startup I get the loading screen, and hear the welcome drums, but right when gnome should start I get freeze screen followed by black screen or etc. again
 -reboot again-
5. I can load gnome but after a second or two (eg. before awn loads) I get screen freeze etc. all over again
 -reboot again-
6. I load gnome completely but after 10 or so seconds i get points 1,2 and 3 again.
 -reboot again-
7. Finally  everything starts normal but emerald is turned off (shows active in compiz but not shoving on desktop as decoration), or awn doesnt start and I have to start it manually or something else is not running like it should
   
Points 4-6 sometimes are repeated more than once before I get to point 7 eventually.
  
All of the crashes occur while preforming random operations (using FF flash plugin(surfing watching online videos), using vlc, every day computer usage, tex typing, sometimes even when I'm not using computer, some times if i'm using all of my virtual desktops at once, crash occurs) I cannot find a relation.

Somehow all of this is looking to me like ati drivers crash, maybe it's in some kind of conflict(or something) with Compiz(or something). 
I've used proprietary drivers fglrx drviers via system>administration>hardware drivers, and I tired ati drivers from the official site. 
I'm also using Karmic on a home server, with nvidia card, and without compiz, and there are no crashes.

So right now I'm not looking for a quick fix, I'm looking for the cause, I'm out of ideas:

1. Could emerald as window decorator be the cause?
2. Flash plugin for linux...?
3. AWN?  
4. Compiz?
5. ...

So my questions are:

1. Is there some kind of a system check that could tell me what part of my configuration is causing the problem
2. Are there any reported problems similar to this that someone knows about(cause I didn't find any)
3. Could this be a global Karmic bug, issue....
4. Would a simple roll back to 9.04 solve my problems? (and is there a way to do that without a fresh install)

I know this is not a trivial problem, but bare with me and try to get me some of your insight and opinions.

My machine specs are in the sig.

THNX guys, give it a shot!

---

### Post by orrie on 2010-02-12
I've had the same problem about now, but not with ATI.
I think it's the screensaver that does it since this have happend almost each time I've locked my computer.
And, I haven't seen this problem in Jaunty, just in Karmic.

I have now tried to disabled the screensaver to check if that have some effect.

When this problem occur, I have to press the power-switch for some seconds to turn the computer off and then turn it on to get it up and working again.
I have also got some lag when moving the touchpad at the laptop (Compal JFT00).

Perhaps I just should downgrade to Jaunty, that actually worked great.

---

### Post by Struki on 2010-02-12
Hm perhaps it could have some impact on my problem as well, but in my case, this crashes also occur while I'm using my computer,  watching a movie clip or doing some work (eg. in octave), so that  situation isn't quite explained with the screensaver issue.
But yes I'm also forced to reboot the computer when the crash occurs...
Right now I'm seriously  considering either downgrading to 9.04 or switching to fedora...

---

### Post by Struki on 2010-02-16
Hmmm still no replys, how can it be that I'm the only one with this kind of problem.
Perhaps an early upgrade to 10.04 alpha 2 ?

---

### Post by darkod on 2010-02-16
Did you try troubleshooting some of the possible issues you mentioned?

1. Did you try to remove AWN?
2. Disable/remove compiz?
3. Disable all screensavers?

---

### Post by woodmaster on 2010-02-16
I had similar problems that boiled down to a graphics driver issue...had to regress to older.  Maybe look into that for your card?  I have basic OEM Intel integrated card so, no experience with ATI.

---

### Post by Struki on 2010-02-21
Ok! So...
I've installed fresh 9.04, and guess what... the crashes remain...
This is starting ti be really a problem and I wouldn't want to go back to win7, but linux isn't offering stabillty right now, and i can't even point to the problem.
I've installed the last drivers that I'm sure worked for me (ati-9.6), but i still get a completly random crash.
I am using this emerald theme: [http://gnome-look.org/content/show.php/LaGaDesk-Universe?content=119098](http://gnome-look.org/content/show.php/LaGaDesk-Universe?content=119098)

So is it possible that emerald is crashing my ubuntu, and isn't there a way to find out in some log file or something what process did cause the crash.
I've been going with this problem for weeks now and I haven't found anything similar to this. So come on guys give me a break anyone...

---

### Post by Struki on 2010-02-21
> **darkod said:**
> Did you try troubleshooting some of the possible issues you mentioned?

1. Did you try to remove AWN?
2. Disable/remove compiz?
3. Disable all screensavers?

The thing is I'm using compiz and awn all the the time, and I never had any crashes before while using 9.04. Now the only thing difernet is that I'm using emerald as window decorator, and I'm setting it up with compiz icon in sys tray. 
So by elimination, emerald is causing the problems, but the real question is how can I be sure?
Now if I think about it, I am using balazan wallpaper and icon theme wich i didn't use before in 9.04, also its clear now that the problem is not in the drivers or ubuntu distro, it's something else, something in the way i'm setting up gnome, so now the question is how can i narrow it down. 
I'll try and revert to the exact settings I had when all did work fine, and start from there I guess...but this is taking to long there has got to be an easier way

---

### Post by drdanielfc on 2010-02-24
What ati graphics card do you have? I (believe) i am having graphics card problems after ati dropped support for my card (13astards, excuse me)

---

### Post by Struki on 2010-02-25
Ahem just saw you posted here 2, we should probably switch here...
Anway my card is listed in my sig, Radeon 3200 HD

---

### Post by Struki on 2010-02-25
So the latest info is:
Crashes remain on ubuntu 9.04 and 9.10, I'm thinking it must be somehow related to ati fglrx drivers, but I can't be sure of anything really cause until now I haven't found anything completely like my situation.
To mention these crashes occur anywhere from 2-3 times a week to 2-3 times a day!!!
So I don't really know how can I be so specific with my situation.

So right now I've turned off compiz and all the extra visual effects, purged all fglrx drivers so I think right now I'm not running any of them.
Is there a way I can't find out what drivers am I using at the moment if any?

Is there somewhere else I could report this problem?
Anyone thinks I should post some log files or something?

---

### Post by Struki on 2010-03-03
It seems I have resolved my crash problems, I'm just not quite sure what was the solution with all the changes I did last few weeks.

After I was crash-free for a few days with all the effects removed, I figured the problem was in compiz or in some fglrx-compiz relation.

So what I did was remove compiz (*sudo apt-get remove compiz*), and I used Envy to install my drivers, also at the moment I'm using Normal desktop effects instead of Extra witch I used before. All in all, so far without a crash with, compiz, awn, emerald running.

One question remains, since I removed compiz, I didn't reinstall it but when I look it up in synaptic I find several compiz variations : Compiz-core with all the packages and Compiz. So my question would be, 

What is te differance between the two?
Is it possible that I had them both installed and that it was the cause for all the crashes?

All in all I'm hoping that this is my final post on the topic ,and if I don't post anything in a week or two consider this problem solved.

---

### Post by Struki on 2010-03-10
F**** it! Crash remains, this is a total ubuntu fail!

---

### Post by Struki on 2010-06-01
To update, it's kinda embarisng, I figured out the crashes, they happened because of a stuck ventilation duct, so the cpu was overheating, especially when using flash etc. So this is solved. All ubuntu versions are now stable on my hp6735s!!

---


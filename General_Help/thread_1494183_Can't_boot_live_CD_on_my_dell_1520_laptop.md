---
title: "Can't boot live CD on my dell 1520 laptop"
date: 2010-05-26
forum: General Help
---

### Post by eitama on 2010-05-26
I downloaded the 32 bit desktop edition.
Burned it on a DVD using nero.
Put it in, restarted. The objective is to run it from CD.
The menu of ubuntu CD appears, it asks me to select a language,
I tried english and hebrew.
I Choose English, Press "start ubuntu without installing" (Enter) and nothing happens. I can hear the CDROM trying to load something.
But to no avail, I redownloaded the whole thing, and burned it on a new DVD, same thing. NO GO.

What am I doing wrong? (I have successfully installed ubuntu 9.x and 8.x in the past easily on this very same laptop.)

---

### Post by ttshivers on 2010-05-26
Did you burn the live CD onto a DVD?  If you did and it is not working, try burning it on a CD instead of a DVD.

---

### Post by eitama on 2010-05-26
> **ttshivers said:**
> Did you burn the live CD onto a DVD?  If you did and it is not working, try burning it on a CD instead of a DVD.

Just tried on a CD as well.
Not working. I can choose any option in the boot menu and none of them work, but they all cause the CD to spin up for a few seconds.
(install ubuntu/try without/check disk - all not working).

So I took the CD out, I now have 3 CDs
- DVDs of 32/64 bit
- CD of 32 bit

Tried all 3 on my PC, core 2 duo monster, same behavior exactly.
I don't know what to do.

---

### Post by cacycleworks on 2010-05-26
Did you double check the md5s of your downloads? Not working on one could be a hardware issue*. Not working on any points to CD burning or iso download problem.


[FONT="Arial Narrow"]*- I observed some interesting fail to boot reports with 10.04 on folks with some not-quite-new computers. Maybe a fix got phased out?[/FONT]

---

### Post by spiky001 on 2010-05-26
Did you burn them at slow speed? and as an iso not data

---

### Post by eitama on 2010-05-26
> **cacycleworks said:**
> Did you double check the md5s of your downloads? Not working on one could be a hardware issue*. Not working on any points to CD burning or iso download problem.


[FONT="Arial Narrow"]*- I observed some interesting fail to boot reports with 10.04 on folks with some not-quite-new computers. Maybe a fix got phased out?[/FONT]

I did not check the md5 at all. I find it hard to believe 2 images i downloaded are pooped with the same transfer error... Ill check them now anyway.

Its really odd. the images downloaded both in less then 20 min.

---

### Post by eitama on 2010-05-26
> **spiky001 said:**
> Did you burn them at slow speed? and as an iso not data

No, I burned at max speed. tried on 2 different cd types and 1 dvd.
I used Neros burn image option and selected the iso. same as i did for ubuntu 8.04 when i installed.

The laptop has also core 2 duo cpu with 4g ram. it's not a hardware problem.

Thx for the help ill update more info soon.

---

### Post by spiky001 on 2010-05-26
Burn at slowest speed possible

---

### Post by eitama on 2010-05-26
Ok, I checked the MD5. It didn't match.
I hope I got it from the right place, I had to go to alternative downloads, choose a mirror, and browse to the file MD5SUMS
from there I took :
d044a2a0c8103fc3e5b7e18b0f7de1c8 *ubuntu-10.04-desktop-i386.iso

And I downloaded the 10.04 desktop 32 bit edition.
It didn't match.
I will download again, from a different location.
I never had any problems with downloaded files, this is odd (;

Thank you for the help, I'll update when I have more info.

---

### Post by eitama on 2010-05-27
Morning.

I burned a new CD, at 4x, checked md5 1st, it matched.
Now I have a new problem, which is not far from the former one.

When the ubuntu setup menu loads, (where you choose to install/try without etc...) I can choose any of the options, and I get a fullscreen purple screen with a very nice color change cycle everytime I press a button.

It looks almost intentional, but there is no setup, no ubuntu...
It's a bit hard to explain.

Still not working. (sigh)

---

### Post by cacycleworks on 2010-05-27
Try this: 
[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

[FONT="Arial Narrow"](was 6th entry when googling [COLOR="DarkSlateBlue"]Can't boot live CD on my dell 1520 laptop[/COLOR])[/FONT]

---

### Post by louismurphy on 2010-05-27
[COLOR=#000000][FONT=Times New Roman][FONT=verdana]There are probably a bunch of un-needed services starting at boot that you could get rid of. That " screen of ever changing data" is the normal output of the Linux boot process: checking the filesystem, checking [hardware[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://ubuntuforums.org/#") and starting services etc. You could run the hdparm command to see how Ubuntu configured your hard drive. As root, type **hdparm /dev/hd?** where ? is the drive. Copy/paste the results here. Though, if it's running fast after boot, as you say, it may be optimized ok already.[/FONT][/FONT][/COLOR]

---

### Post by eitama on 2010-05-28
> **cacycleworks said:**
> Try this: 
[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

[FONT="Arial Narrow"](was 6th entry when googling [COLOR="DarkSlateBlue"]Can't boot live CD on my dell 1520 laptop[/COLOR])[/FONT]

Hi, thanks for the hint!
I didn't work, but it got me a bit further into a different problem, So it's not for this thread. (flashing capslock and scroll lock)
Followup on : [http://ubuntuforums.org/showthread.php?t=1494617](http://ubuntuforums.org/showthread.php?t=1494617)

---

### Post by eitama on 2010-05-28
> **louismurphy said:**
> [COLOR=#000000][FONT=Times New Roman][FONT=verdana]There are probably a bunch of un-needed services starting at boot that you could get rid of. That " screen of ever changing data" is the normal output of the Linux boot process: checking the filesystem, checking [hardware[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://ubuntuforums.org/#") and starting services etc. You could run the hdparm command to see how Ubuntu configured your hard drive. As root, type **hdparm /dev/hd?** where ? is the drive. Copy/paste the results here. Though, if it's running fast after boot, as you say, it may be optimized ok already.[/FONT][/FONT][/COLOR]

I am not trying to install ubuntu, just load live cd. so I never get to a terminal to play with linux. I am stuck way before that.

---

### Post by cacycleworks on 2010-05-28
@eitama: when it comes to running a linux liveCD, etc, imho, ubuntu is about miserable running off the CD. 

I've done [SLAX]("http://www.slax.org/") off a USB stick, which works REALLY WELL. And my perpetual go-to for any computer voodoo is [Knoppix]("http://www.knoppix.net/"), which runs well loading from the CD and also imho is very compatible with a wider array of hardware than ubuntu. We were using knoppix to diagnose why ubuntu wouldn't load. If you do get knoppix, get version [5.1]("ftp://ftp.cise.ufl.edu/pub/mirrors/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso") from a [mirror]("http://www.knopper.net/knoppix-mirrors/index-en.html"). The current version is version 6, but 5 boots with less nonsense...

:)

---

### Post by eitama on 2010-05-28
> **cacycleworks said:**
> @eitama: when it comes to running a linux liveCD, etc, imho, ubuntu is about miserable running off the CD. 

I've done [SLAX]("http://www.slax.org/") off a USB stick, which works REALLY WELL. And my perpetual go-to for any computer voodoo is [Knoppix]("http://www.knoppix.net/"), which runs well loading from the CD and also imho is very compatible with a wider array of hardware than ubuntu. We were using knoppix to diagnose why ubuntu wouldn't load. If you do get knoppix, get version [5.1]("ftp://ftp.cise.ufl.edu/pub/mirrors/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso") from a [mirror]("http://www.knopper.net/knoppix-mirrors/index-en.html"). The current version is version 6, but 5 boots with less nonsense...

:)

@cacycleworks

Thanks for the tips, I will try that.
Full disclosure on what I am trying to do :
1. I got a nokia N900
2. I am trying to flash it's firmware.
3. The firmware can be flashed with a "maemo flasher" application, which does not work well with windows 64 bit versions, which is what I am running as Main OS.
4. The forums on talk.maemo.org suggested ubuntu as an easy solution to my problem, which turned out not so easy (;
5. I am very fond of debian apt-get and dpkg, and feel very at home with it, thats why I am trying hard to get ubuntu to run.
6. If I have to go for knoppix or slack, I think i'll look for a debian live cd, if such exists.

If my debian/ubuntu attempts will fail, I will most definitely try knoppix per your suggestion.

Thank you sir for you help!

---


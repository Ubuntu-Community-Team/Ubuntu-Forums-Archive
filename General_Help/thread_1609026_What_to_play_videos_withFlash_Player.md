---
title: "What to play videos with?Flash Player?"
date: 2010-10-29
forum: General Help
---

### Post by 340six on 2010-10-29
I have almost everything done now but that....will a download of free flash player work by it self? Or try some other softwhare? My wife gets off at 2:00 and would be a happy camper if she can see Swamp People:popcorn:

---

### Post by WorMzy on 2010-10-29
What videos? VLC or MPlayer will play most things.

---

### Post by TBABill on 2010-10-29
Flash will support your browser in allowing you to see flash videos online (streaming). Chromium has flash contained already within it. Are you wanting to stream videos or download and watch offline?

---

### Post by gufide on 2010-10-29
Also, you can install gnash from ubuntu software center

---

### Post by lovinglinux on 2010-10-29
Get [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939/), an extension to remove conflicting flash plugins and install the proper version according to your browser architecture.

---

### Post by Omnomnom on 2010-10-29
Depends on what you want, if it's a flash video online, you just go to [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/) and get the plug-in for Firefox, chromium has flash built in and so does the closed-source google chrome. If you want to download normal video files and watch them on a laptop or something with your wife, you can get VLC media player, which should play any movie files you throw at it.. Not literally, I wouldn't throw a cassette at a computer, especially a linux one. Ok, back on-topic.
To get VLC go to Applications > Ubuntu Software Center and search up VLC Media Player, click on the one with a little traffic cone, and install it. Then download your movie and right click it, click open with VLC Media player and there you go. Enjoy your movie :)

---

### Post by 340six on 2010-10-29
> **Omnomnom said:**
> **Depends on what you want, if it's a flash video online, you just go to [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/) and get the plug-in for Firefox** chromium has flash built in and so does the closed-source google chrome. If you want to download normal video files and watch them on a laptop or something with your wife, you can get VLC media player, which should play any movie files you throw at it.. Not literally, I wouldn't throw a cassette at a computer, especially a linux one. Ok, back on-topic.
To get VLC go to Applications > Ubuntu Software Center and search up VLC Media Player, click on the one with a little traffic cone, and install it. Then download your movie and right click it, click open with VLC Media player and there you go. Enjoy your movie :)
Yes the places like History Channel will not play says that I don not have flash so it can not play.
When I went to Adobie earlyer today it shows 4-5 types of down loads so I posted this intsead of just picking one
Yum for linux
.tar.gz for linux
.rpm for linux
.deb for Ubuntu 8.04+
.apt for Ubuntu 9.04+
I also tried to toss a DVD in and it does not play

---

### Post by 340six on 2010-10-29
> **TBABill said:**
> Flash will support your browser in allowing you to see flash videos online (streaming). Chromium has flash contained already within it. Are you wanting to stream videos or download and watch offline?
Most everything she looks at is streaming from a few sites history is 99% of the time.
As she likes the shows they have and we have no cable/sat Tv free air anntenna with 40+ chanells

---

### Post by joshruehlig on 2010-10-30
> **340six said:**
> Yes the places like History Channel will not play says that I don not have flash so it can not play.
When I went to Adobie earlyer today it shows 4-5 types of down loads so I posted this intsead of just picking one
Yum for linux
.tar.gz for linux
.rpm for linux
.deb for Ubuntu 8.04+
.apt for Ubuntu 9.04+
I also tried to toss a DVD in and it does not play

use deb for ubuntu 9.04+
then double click the downloaded file, then click install. then reboot browser
Or you can just put this in the terminal
sudo apt-get install chromium
(it will have the latest 10.1 flash player)

---

### Post by 340six on 2010-10-30
> **joshruehlig said:**
> **use deb for ubuntu 9.04+**
then double click the downloaded file, then click install. then reboot browser
**Or you can just put this in the terminal**
sudo apt-get install chromium
(it will have the latest 10.1 flash player)
They only have deb8.0+
what terminal? sorry not a computer guy just an old car restorer
Thanks everyone for all the help so far

---

### Post by joshruehlig on 2010-10-30
> **340six said:**
> They only have deb8.0+
what terminal? sorry not a computer guy just an old car restorer
Thanks everyone for all the help so far

Use deb8.0+, sorry

hold Alt+F2
type gnome-terminal
press enter

You now have control of your computer without a gui...

or click applications -> accessories -> terminal

---

### Post by TBerk on 2010-11-03
> **joshruehlig said:**
> use deb for ubuntu 9.04+
then double click the downloaded file, then click install. then reboot browser
Or you can just put this in the terminal
sudo apt-get install chromium
(it will have the latest 10.1 flash player)

Josh is being helpful (Thx Josh...), here is some annotations that might help;

The 'Terminal' is referring to the part of the Operating System that doesn't rely on a graphical interface. No graphics really, no pull down menus, no mouse to speak of. It's often ref'd as a Command Line interface, because, well, you control things directly by typing in commands. Think Microsoft DOS, circa 1981...
[http://en.wikipedia.org/wiki/DOS](http://en.wikipedia.org/wiki/DOS)
In fact before DOS, there was CP/M, and so on and so on.
[http://en.wikipedia.org/wiki/CP/M](http://en.wikipedia.org/wiki/CP/M)

Lots of fun UNIX goodness to be had by knowing at least ten basic Unix/Linux command line, er, commands. (Google is your freind, as is PsycoCats' website; 
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

```

sudo apt-get install chromium

```

Means you are asking the system to treat everything after 'sudo' as if you had Administrator's Rights, the 'apt-get' = an application that goes and gets applications (OK, I'm confusing myself now...) and installs them for you, and the 'chromium' is the application you want apt-get to install. 

As there are many roads that lead to Rome, this way is a quick way to install a given program, and along with it the Flash support this all started with. There are other ways, some given earlier in this thread, to gain the end result you are looking for; you have options.

Installing Chromium web browser might just do the trick, likely wont hurt anything, and you won't be stuck with it if you decide you don't like it after all.


TBerk

---


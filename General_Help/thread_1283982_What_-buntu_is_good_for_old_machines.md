---
title: "What -buntu is good for old machines?"
date: 2009-10-06
forum: General Help
---

### Post by xycris on 2009-10-06
Hello everyone,

I really want to use my old laptop for it is still working good as new with a fresh install of WindowsXP Home SP2. However, I have decided to have Linux in to do Internet browsing, mailing, and chat. However, I wanted to do more specifically writing documents, doing some spreadsheets, lay-outing and graphics editing, making presentations. I know that those tasks might be too much to ask out of my old machine, but, is that possible?

The good open source applications alternative, or probably even better than their commercial counterpart, I have used so far are as follows:
[LIST]
[*]OpenOffice.org
[INDENT][*]Writer
[*]Calc
[*]Impress
[*]Draw[/INDENT]
[*]Inkscape
[*]GIMP
[/LIST]

My old machine's specs has an Intel Celeron 1.3GHz with 256MB RAM and 40GB HD. I have Xubuntu 9.04 Jaunty Jackalope running but somehow it is slow and many unwanted applications are present and I am afraid to do some uninstalling for it might corrupt the OS.

Please do advise me if Xubuntu was a good choice considering the applications I wanted. Is there a way to tweak Xubuntu to make it lighter? I only wanted to do the tasks mentioned above and maybe a couple of music files.

Thank you very much for your help.

-Xyc

---

### Post by Bucky Ball on 2009-10-06
Try a different desktop manager like openbox.

The other thing you can do is install from the terminal (CLI install). You can get there from 'more options' I think, F4, on the options on the desktop installer. Then you can just drag in what you want. Load a desktop environment (Xfce4 perhaps) and Synaptics and you should be away.

---

### Post by XCan on 2009-10-06
I don't find XFCE that resource efficient. I think LXDE is a much better alternative.

---

### Post by rudy.b on 2009-10-06
> **XCan said:**
> I don't find XFCE that resource efficient. I think LXDE is a much better alternative.

I agree.  I installed LXDE on a Pentium 3 with 128 MB RAM and it was pretty snappy.  I used the [Alternate CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") to install a command line system and then added packages as needed.  See [Installation: Low Memory Systems]("https://help.ubuntu.com/community/Installation/LowMemorySystems") for some options.

---

### Post by STEELBAS on 2009-10-06
[CrunchBang Linux]("http://crunchbanglinux.org/")
=)

---

### Post by zeroseven0183 on 2009-10-06
> **STEELBAS said:**
> [CrunchBang Linux]("http://crunchbanglinux.org/")
=)

+1 with CrunchBang Linux

I love it. My sister loves it. Everyone in our house love it.

---

### Post by ottosykora on 2009-10-06
>My old machine's specs has an Intel Celeron 1.3GHz with 256MB RAM and 40GB HD. I have Xubuntu 9.04 Jaunty Jackalope running but somehow it is slow and many unwanted applications are present and I am afraid to do some uninstalling for it might corrupt the OS.
<


with 256mb ram, the problem seems to be the installation itself. I made the experience that with this amount of ram only xubuntu will work properly, and to install the os, the alternative install CD is better.
I am running xubuntu on old laptop similar to your one, it is vene older since came with w2k and not xp, and it still works with xubuntu 8.10.

---

### Post by snowpine on 2009-10-06
Increase your ram to 512mb (or 1gb if supported) and if that's still not fast enough, give Crunchbang a try.

Openoffice and Gimp can be installed in *any* Linux distribution, so don't be too concerned about that. Good luck! :)

---

### Post by xycris on 2009-10-13
Hi Guys!

Thank you so far for all your suggestions, I am currently trying crunchbang and see what I can get with my laptop's current specs.

I really don't want to install some hardware expansions into this unit because it is not worth the investment, you know what I mean.

I will post any problem or praises soon.

Thanks again. :)

---

### Post by bodhi.zazen on 2009-10-13
I would add lubuntu to the list as well as crunchbang.

---

### Post by xycris on 2009-10-19
Hi guys,

I was trying CrunchBang Linux based on the Jaunty Jackalope release of Ubuntu but I can't seem to burn it to a disc. I always get a corrupted disc. I am using my other desktop running Ubuntu Jaunty Jackalope to burn with Brasero.

Is there a problem with their distributed ISO image?

Thanks

---

### Post by XCan on 2009-10-19
Did you check out the md5checksum referenced in the download page? [http://www.crunchbanglinux.org/wiki/downloads#standard_edition_-_32-bit](http://www.crunchbanglinux.org/wiki/downloads#standard_edition_-_32-bit)

---

### Post by sabre2th on 2009-10-19
I've heard good things about Crunchbang; I'd say it's definitely worth a look.  If/when you get more comfortable with Ubuntu and Linux, though, I'd say install it yourself from the minimal CD.  Doing it this way lets you choose only what you need and avoids the cruft altogether.

I've found it feels a good bit snappier like this, even running full Gnome/KDE/whatever.  There's a good thread about minimal installs somewhere in these forums.  I'll see if I can find the link when I get home.  There are two main hangups (they're minor for me, but you decide if they're a problem).

[LIST=1]
[*]You have to download everything as you install it, meaning it takes longer to install and uses bandwidth.  This isn't a big deal for me because I'd be downloading updates immediately after anyway, but not everybody wants to do this.
[*]If you do it this way and use wireless, you'll need to plug in for internet access until you get it set up.
[/LIST]

---

### Post by xycris on 2009-10-23
> **XCan said:**
> Did you check out the md5checksum referenced in the download page? [http://www.crunchbanglinux.org/wiki/downloads#standard_edition_-_32-bit](http://www.crunchbanglinux.org/wiki/downloads#standard_edition_-_32-bit)

Hi XCan,

Yup, I did and it was a match. I just don't get it that when the disc reaches around 98% it hangs at that point using Brasero. I waited 24 hours and no progress.

Anyways, I was already able to burn a copy via Infrarecorder using WINE.

I am currently trying it out from "Live" and it is really fast. I like it.

I just don't know about Lubuntu, it is still a work in progress according to the wiki.

Do your best guys. Thanks for such great Linux flavours. :)

---

### Post by XCan on 2009-10-23
Ah, great thing you managed to burn it through other apps. Although k3b would probably have done it as well if one wants to stick with with linux apps, or some other burning apps. :) I know that Brasero is weird for some people.

---

### Post by xycris on 2009-10-29
Hi Guys!

I have confirmed that Ubuntu released the 9.10 Karmic today 29 Oct 2009. Would #!Crunchbang also release an updated distro based on the new Ubuntu release?

---

### Post by snowpine on 2009-10-29
> **xycris said:**
> Hi Guys!

I have confirmed that Ubuntu released the 9.10 Karmic today 29 Oct 2009. Would #!Crunchbang also release an updated distro based on the new Ubuntu release?

CrunchBang is an independent project; no official announcement yet. New releases usually follow 1 or 2 months behind Ubuntu. More info here: 

[http://crunchbanglinux.org/forums/topic/5216/crunchbang-910-release/](http://crunchbanglinux.org/forums/topic/5216/crunchbang-910-release/)

---

### Post by xycris on 2009-10-30
> **snowpine said:**
> CrunchBang is an independent project; no official announcement yet. New releases usually follow 1 or 2 months behind Ubuntu. More info here: 

[http://crunchbanglinux.org/forums/topic/5216/crunchbang-910-release/](http://crunchbanglinux.org/forums/topic/5216/crunchbang-910-release/)

Thank you very much for that snowpine :)

---

### Post by darkksyde on 2009-10-30
I reckon crunchbang linux is one of the best distributions for older computers, it is built on ubuntu using the openbox window manager

---

### Post by OneMixDJ on 2009-11-17
> **darkksyde said:**
> I reckon crunchbang linux is one of the best distributions for older computers, it is built on ubuntu using the openbox window manager

I got a Dell Optiplex GX-1 PII with 384MB RAM.

Right now it's running XP with MP3 Rocket and Vuze, but I'm considering a Linux alternative. I've been thinking about Masonux and Lubuntu but Crunchbang looks like one to also consider. Unfortunately neither MP3 Rocket and Vuze do not work well in Wine so I'll need to figure that out.

---

### Post by xycris on 2009-11-17
> **OneMixDJ said:**
> I got a Dell Optiplex GX-1 PII with 384MB RAM.

Right now it's running XP with MP3 Rocket and Vuze, but I'm considering a Linux alternative. I've been thinking about Masonux and Lubuntu but Crunchbang looks like one to also consider. Unfortunately neither MP3 Rocket and Vuze do not work well in Wine so I'll need to figure that out.

Crunchbang has its own pre-installed applications to handle music and video files, VLC, and torrent files, Transmission.

I love the Crunchbang for its ease of use and lightness.

---

### Post by nothingspecial on 2009-11-17
> **darkksyde said:**
> I reckon crunchbang linux is one of the best distributions for older computers, it is built on ubuntu using the openbox window manager

I reckon crunchbang linux is one of the best best distributions ..... of all.

I (we)use Ubuntu on all our fancy laptops and netbooks but on my actual computer - you know - the thing with the big box, plugged into the big monitor, with the separate keyboard etc, I use crunchbang. (Well, actually I use Ubuntu 8.04 server edition with highly modified default crunchbang configs, but it all started with crunchbang). 

If you want something superfast and super configurable, crunchbang is the way to go.

People call it minimalist but that`s just the way you look at it. It comes with dvd and mp3 playback, flash and 2 or 3 default apps for every purpose - in your menus.

And it`s just one guy`s tweaked ubuntu that`s taken off. It`s still ubuntu (and therefore debian) underneath and that means that most of the help you get or find, ubuntu or debian wise will probably work with crunchbang.

---

### Post by OneMixDJ on 2009-11-17
> **nothingspecial said:**
> I reckon crunchbang linux is one of the best best distributions ..... of all.

I (we)use Ubuntu on all our fancy laptops and netbooks but on my actual computer - you know - the thing with the big box, plugged into the big monitor, with the separate keyboard etc, I use crunchbang. (Well, actually I use Ubuntu 8.04 server edition with highly modified default crunchbang configs, but it all started with crunchbang). 

If you want something superfast and super configurable, crunchbang is the way to go.

People call it minimalist but that`s just the way you look at it. It comes with dvd and mp3 playback, flash and 2 or 3 default apps for every purpose - in your menus.

And it`s just one guy`s tweaked ubuntu that`s taken off. It`s still ubuntu (and therefore debian) underneath and that means that most of the help you get or find, ubuntu or debian wise will probably work with crunchbang.

Works for me, I'll give Crunchbang a shot. Thanks!  :D

---

### Post by darkksyde on 2009-11-17
crunchband is the best i rkon, worked well on an intel celeron 800mhz cpu with only 256mb ofram

---


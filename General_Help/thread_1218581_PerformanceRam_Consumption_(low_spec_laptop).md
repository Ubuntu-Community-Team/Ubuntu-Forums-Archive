---
title: "Performance/Ram Consumption (low spec laptop)"
date: 2009-07-20
forum: General Help
---

### Post by nunyez on 2009-07-20
At system idle my Xubuntu install is consuming ~250mb of ram (after fresh boot). I'm running 8.04 Hardy

DELL Inspiron B120
Ram: 512mb
CPU: Intel Celeron 1.40ghz

I'm often faced with total ram consumption leading to my swap space being filled and performance taking a nose dive. Though I am sure this is better than gnome at this point is hardly seems like it. Xubuntu installs are on much lower spec'd machines I have read though the posts were dated and running 7.10 if I remember correctly.

Is there something I can do to get increased performance? Older release? Other distro? I looked at fluxbuntu but it seems to have ceased development. This computer is for a novice user which is why i'd like to stick with a larger distro such as ubuntu but the performance is really taking a toll on basic use

Help appreciated

---

### Post by blueridgedog on 2009-07-20
You might give puppy or mint a try on that laptop - all for the price of a download and a blank disk.

---

### Post by kerry_s on 2009-07-20
do a base install and build up from there.
debian is faster on the old stuff.
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/i386/iso-cd/debian-testing-i386-businesscard.iso)

i use debian testing base install with xfce4, my start up ram use is around 43mb, my laptop is 450mhz 256mb ram.

after the base install i use:

**apt-get install xorg gdm xfce4 gnome-icon-theme mousepad synaptic iceweasel**

put sudo in front if you do the expert install to get a no root system.

---

### Post by snowpine on 2009-07-21
Have you tried Ubuntu 9.04 yet? In my experience, the latest version is also the fastest (in part due to the ext4 filesystem), and Ubuntu and Xubuntu run at about the same speed (the only difference really is the desktop environment, Gnome vs. Xfce).

If speed on older hardware is your #1 consideration, really the best thing you can do is explore distros outside the Ubuntu family. Here is an enlightening comparison of Xubuntu vs. Debian Xfce: [http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)

And of course, the "Ultra Light" distros such as Puppy, DSL, Slitaz, etc. will be faster still.

---

### Post by nunyez on 2009-07-21
These are all very good responses.  I especially appreciate the link to the distrowatch comparison.  Now I am torn with how much lower xubuntu jaunty's ram consumption seems to be than with my xubuntu hardy install.  Ibex really turned me off when it comes to going with a non-LTS install because so many things were broken that worked fine in hardy.

right now I am either going with xubuntu jaunty (9.04), mint xfce community edition (jaunty based), or debian 5 + xfce.

I don't want to be wasting half of my ram just on the desktop, but I also don't want to be knee deep in time making things first-time-linux-user friendly (the wife) with a debian install. I'm leaning towards mint's xfce right now. Suggestions appreciated

---

### Post by snowpine on 2009-07-21
I've never tried Mint personally, but I've heard a lot of positive reviews from first-time-users. Sounds like a good option.

I also forgot to mention CrunchBang; it is an Ubuntu derivative using Openbox: [http://crunchbanglinux.org/](http://crunchbanglinux.org/)

---

### Post by az on 2009-07-21
> **nunyez said:**
> At system idle my Xubuntu install is consuming ~250mb of ram (after fresh boot). I'm running 8.04 Hardy

DELL Inspiron B120
Ram: 512mb
CPU: Intel Celeron 1.40ghz

I'm often faced with total ram consumption leading to my swap space being filled and performance taking a nose dive. Though I am sure this is better than gnome at this point is hardly seems like it. Xubuntu installs are on much lower spec'd machines I have read though the posts were dated and running 7.10 if I remember correctly.

Is there something I can do to get increased performance? Older release? Other distro? I looked at fluxbuntu but it seems to have ceased development. This computer is for a novice user which is why i'd like to stick with a larger distro such as ubuntu but the performance is really taking a toll on basic use

Help appreciated

Well, the more ram that is used, the faster your computer will go.  In the case of Linux memory management, the more ram you keep empty, the slower your computer will go.

But regardless of how the ram is managed, you will need more ram.  I think 512 megs or ram is the bare minimum needed to run the full desktop - you will find a significant improvement by simply going up to 1 gig.

---

### Post by nunyez on 2009-07-21
I don't know about CrunchBang for her but I've heard of it before and never tried it, looks good for myself so I might have to :)

az, yes I understand it is low but she is using it as a netbook more or less, nothing but a web browser and some chat. Is it really worth it? Not to mention I don't even know what ram I could put in it. The specs page ([http://www.dell.com/us/en/dfb/notebooks/inspn_b120/pd.aspx?refid=inspn_b120&cs=28&s=dfb](http://www.dell.com/us/en/dfb/notebooks/inspn_b120/pd.aspx?refid=inspn_b120&cs=28&s=dfb)) under the Tech Specs tab says that only 1 slot is accessible plus its "shared" (used for the video card too I think??). This [review]("http://www.notebookreview.com/default.asp?newsID=2787") lists kingston as not compatible with the crap in it.

The shared memory bit might be why my consumption is so high after all, if anyone knows their hardware please chime in

---

### Post by snowpine on 2009-07-21
Another option for a fast, user-friendly, browser-only OS is the aptly-named browserpuppy: [http://www.browserpuppy.com/](http://www.browserpuppy.com/)

---

### Post by nunyez on 2009-07-23
Mint XFCE edition is working out well for her! I did install debian however on my VM and wow :D low memory usage!

---


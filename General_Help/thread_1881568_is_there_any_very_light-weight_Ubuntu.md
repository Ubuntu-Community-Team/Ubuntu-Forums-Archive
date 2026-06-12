---
title: "is there any very light-weight Ubuntu?"
date: 2011-11-15
forum: General Help
---

### Post by noisysoul on 2011-11-15
Hi! :D

I have to install an OS on a _really old machine from 2000_, I tried Lubuntu 11.10 (just trying) and Xubuntu 8.04 and after the beginning I got a black screen. I've been googling light-weight Linux distros like Puppy and even though they might work fine, I want something easier and simpler to use...

...**is there any very light-weight Ubuntu?** (and if possible: having Spanish support)

It's a Toshiba laptop, and it's got only an _850MHz processor_ along with _120MB RAM_... I know it's hard, but I prefer Ubuntu or any Ubuntu-based distro (or Debian-based) rather than another distribution, so, I don't know, there might be an old Xubuntu or Lubuntu or anything like that willing to work, I guess.

Any idea? Thank you so much.

Greetings from Chile.

---

### Post by bkratz on 2011-11-15
You might want to check out bodhi.

[http://www.bodhilinux.com/system.php](http://www.bodhilinux.com/system.php)

---

### Post by jjex22 on 2011-11-15
As I have been advised by amjjawad, Lubuntu seems a good try, though being the owner of a 1ghz linux machine i'd have thought you'd really want to up the ram - 512 would be my desired level, that's what my emac ran 10.04 on, before it's upgrade, so it'll definitely run lubuntu, and those sticks tend to be dirt cheap on ebay these days!

---

### Post by collisionystm on 2011-11-15
> **noisysoul said:**
> Hi! :D

I have to install an OS on a _really old machine from 2000_, I tried Lubuntu 11.10 (just trying) and Xubuntu 8.04 and after the beginning I got a black screen. I've been googling light-weight Linux distros like Puppy and even though they might work fine, I want something easier and simpler to use...

...**is there any very light-weight Ubuntu?** (and if possible: having Spanish support)

It's a Toshiba laptop, and it's got only an _850MHz processor_ along with _120MB RAM_... I know it's hard, but I prefer Ubuntu or any Ubuntu-based distro (or Debian-based) rather than another distribution, so, I don't know, there might be an old Xubuntu or Lubuntu or anything like that willing to work, I guess.

Any idea? Thank you so much.

Greetings from Chile.

[http://wiki.sugarlabs.org/go/Sugar_on_a_Stick](http://wiki.sugarlabs.org/go/Sugar_on_a_Stick)

[http://www.slax.org/](http://www.slax.org/)  << Can be installed to hard drive

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)  << Use OpenBox 105mb of ram when fully up and running

---

### Post by larrypg on 2011-11-15
I would think you are in very sticky territory to get even Lubuntu working.  If you only have 120 MB of ram I would think that some of that will be used by video. I am not sure how much but that will make a very low amount even lower.

---

### Post by jjex22 on 2011-11-15
> **collisionystm said:**
>  Use OpenBox 105mb of ram when fully up and running

Gotta love the crunchbang, but this is sort of what I was refering to with the ram issue - I find that puppy is circling 160/180 web browsing, surely even with crunchbang you start running more than a single web page and you're gonna start swapping like hell at 128?

The smallest I've seen is quirky - a puplet - but from my experience of vm'ing it, i'd sooner spend the fiver on ebay and have more choice.

---

### Post by collisionystm on 2011-11-15
> **jjex22 said:**
> Gotta love the crunchbang, but this is sort of what I was refering to with the ram issue - I find that puppy is circling 160/180 web browsing, surely even with crunchbang you start running more than a single web page and you're gonna start swapping like hell at 126?

The smallest I've seen is quirky - a puplet - but from my experience of vm'ing it, i'd sooner spend the fiver on ebay and have more choice.


Yeah... that was the problem with any OS which runs 128mb of ram.

I would go on a search for memory. It is pretty cheap right now. Check Crucial

[www.crucial.com](www.crucial.com)

---

### Post by noisysoul on 2011-11-15
I cannot increase the amount of RAM since it's not my laptop, I'm just meant to make it work.

I'l try your ideas, if you know any other nice light-weight distro please let me know.

Thank you so much guys!! :P

---

### Post by collisionystm on 2011-11-15
> **noisysoul said:**
> I cannot increase the amount of RAM since it's not my laptop, I'm just meant to make it work.

I'l try your ideas, if you know any other nice light-weight distro please let me know.

Thank you so much guys!! :P


lol fun fun!

Check this out

[http://porteus.org/](http://porteus.org/)

Apparently needs only 30mb of ram to run


Got from here

[http://en.wikipedia.org/wiki/Lightweight_Linux_distribution](http://en.wikipedia.org/wiki/Lightweight_Linux_distribution)

---

### Post by noisysoul on 2011-11-15
Thanks dude!

...hope's coming back hahahaha

---

### Post by collisionystm on 2011-11-15
good luck lol. You could also check out FreeDos

---

### Post by jjex22 on 2011-11-15
> **collisionystm said:**
> 
Apparently needs only 30mb of ram to run


should point out that's going to be text mode - runlevel 3. LXDE is the included lightweight user interface, and that's 96MB , but still the features you'll get over quirky at around 90mb are probably worth it!

---

### Post by jjex22 on 2011-11-15
If you go freedos, be sure to check out opengem for a gui - 16 bit, but then... you know.. dos!

---

### Post by TeamRocket1233c on 2011-11-15
Either Lubuntu, Xubuntu, or Puppy 5.2.8. Lubuntu's basically Ubuntu but it uses LXDE instead of GNOME, and Xubuntu's essentially in XFCE Ubuntu. Also, Lucid Puppy 5.2.8's the Ubuntu-compatible version of Puppy.

---

### Post by Hylas de Niall on 2011-11-16
Hmmm.... might try that on my Dell Latitude CPI-a.
Thanks for the link - there *are* distros beyond Distrowatch!

---

### Post by snowpine on 2011-11-16
My opinion is that you're wasting your time (unless you upgrade the RAM to 512mb or more).

That being said, you might find some good suggestions on this site: [http://kmandla.wordpress.com](http://kmandla.wordpress.com)

---

### Post by jjex22 on 2011-11-17
Sorry for the delay - If you're interested, I've been running some tests to figure it out for you. I installed these on a netbook and took the ram readings from the display/resource monitor once the system was booted, connected by wifi, with the browser, a word processor open and playing an mp3. If a system can't do this, then there's not a lot of choice.

The winner is crunchbang! =116MB no errors other than HAVING to install grub to the mbr.

Puppy did okay - 165MB all up and running, no install problems - but a very annoying quirk - can use wifi OR lan in a session - once you've used one, have to reboot to use the other.

Slax is probably better than Puppy, but I'm putting it third as it did not detect my wifi and I had to find a driver, and dispite looking more pleasing it just didn't feel as quality - 148MB

Porteus meets the needs of this system at 128MB however dispite full hardware support, felt like a beta release.

Finally quirky - based on puppy, and well within the limit at 118MB, probably good for a knackered desktop, but just too much of a pain for day to day laptop usage - didn't share the networking issue, but dropped the wireless (once I got THAT working!) constantly, maybe my fault, but couldn't live with it.


Hope that helps/is of interest to anyone else - crunchbang is openbox though, so noobs may take some getting used to, but it does theoretically offer the prospect of realistically running on 128MB RAM!

---

### Post by mörgæs on 2011-11-17
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by snowpine on 2011-11-17
> **jjex22 said:**
> Sorry for the delay - If you're interested, I've been running some tests to figure it out for you. I installed these on a netbook and took the ram readings from the display/resource monitor once the system was booted, connected by wifi, with the browser, a word processor open and playing an mp3. If a system can't do this, then there's not a lot of choice.

The winner is crunchbang! =116MB no errors other than HAVING to install grub to the mbr.

Puppy did okay - 165MB all up and running, no install problems - but a very annoying quirk - can use wifi OR lan in a session - once you've used one, have to reboot to use the other.

Slax is probably better than Puppy, but I'm putting it third as it did not detect my wifi and I had to find a driver, and dispite looking more pleasing it just didn't feel as quality - 148MB

Porteus meets the needs of this system at 128MB however dispite full hardware support, felt like a beta release.

Finally quirky - based on puppy, and well within the limit at 118MB, probably good for a knackered desktop, but just too much of a pain for day to day laptop usage - didn't share the networking issue, but dropped the wireless (once I got THAT working!) constantly, maybe my fault, but couldn't live with it.


Hope that helps/is of interest to anyone else - crunchbang is openbox though, so noobs may take some getting used to, but it does theoretically offer the prospect of realistically running on 128MB RAM!

Thanks for doing the research, but unfortunately there's one flaw in your testing. Distro A will not necessarily use the same amount of RAM running on your hardware as it does running on my hardware. Depending on the hardware modules/drivers that are necessary, and the amount of RAM available, Linux will use more or less RAM.

Also in many cases the stumbling block with any distro on a low-RAM computer is the installer. For example a distro might use 128mb of RAM under average load, but the installer requires 256mb.

Finally there is the fallacy that "less RAM usage is always better." This may be true in the case of a very old computer without much RAM, granted. However on modern hardware it is a waste not to use the available RAM. As a thought experiment, it's easy to imagine a well-designed distro that uses 1gb of RAM and runs blindingly fast, vs. a poorly-designed distro that uses 100mb RAM but is quite slow. :)

ps I am a long-time CrunchBang Forums enthusiast; the general consensus is that CrunchBang is quite painful to run with only 128mb.

---

### Post by jjex22 on 2011-11-17
> **snowpine said:**
> Thanks for doing the research

You're quite welcome ;) lol, no, don't worry about it I did it because it interested me - and thought some real world data could help the op - I usually just VM distros to try them out, so was quite refreshing to install some minimal distro's again. 

I definitely agree with the use what you got philosophy! my laptop and netbook have lxde based distro's on them that get good performance to battery life balance, but they also have full gnome 3 installs (well the little netbook has to use 2d mode, but as is life!) and my main desktop also runs a full blown ubuntu install (and possibly from now on - we'll see how it goes) a opensuse kde install - after testing yesterday, i found a kde I actually like so am giving it a go, and I also have a crunchbang install for vm testing! - all 64bits - as you say if you have the hardware why spare it?


I maintain my stance that the op should advice the laptop owner to up to 512, inmho if there is no choice, crunchbang would be the way to go :)

---

### Post by keithpeter on 2011-11-17
Hello All

AntiX Linux springs to mind. Same ilk as crunchbang. Below from the AntiX wiki...

> 
It should run on most computers, ranging from 64MB old PII 266 systems with pre-configured 128MB swap to the latest powerful boxes. 128MB RAM is recommended minimum for antiX. The installer needs minimum 2.2GB hard disk size. antiX can also be used as a fast-booting rescue cd. 


I'd second the general view that another 128Mb stick, or even an extra 256Mb would radically improve the experience of using the laptop. I'm posting this from a P3 850MHz Dell with 512 Mb of ram. I've installed Ubuntu 11.10 and the Unity 2d gui is working ok.

---

### Post by SoWhat.lv on 2011-11-20
Does anybody know something about Google Chrome OS?

---


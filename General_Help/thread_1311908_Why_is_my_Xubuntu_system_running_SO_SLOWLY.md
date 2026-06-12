---
title: "Why is my Xubuntu system running SO SLOWLY?"
date: 2009-11-02
forum: General Help
---

### Post by maxrocks_1 on 2009-11-02
For some reason, my Xubuntu system has been rather slow (*really* slow in fact, even browsing the internet it is noticeable), so I did the logical thing and tried a format and fresh install, thinking that the upgrade might have made it go all screwy: still really slow. I then tried installing Ubuntu (with GNOME), which was actually a bit faster feeling, but I much prefer xfce and would like to keep my xubuntu as I am used to it, and because it is *supposed* to be faster, so I re-installed Xubuntu.

My system specifications:

~Processor:AMD Athlon(tm) XP 1700+
           1470.331 MHz
           256 KB cache size

~RAM: 497 MB of which it says 420 is used

~Swap: 1458 MB of which it says 48 is used

~I have two hard drives, both 80.0GB, formatted to ext3 filesystem. The master has Xubuntu installed on it (and not much else, it's mostly empty), and the slave is just full of movies and isn't set to auto-mount.

~01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]

~01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

Any ideas anyone? Could it have something to do with my video/graphics card perhaps? Any suggestions on how I can fix this? My system is really slow and it's bloody annoying.

~Maxwell

---

### Post by kerry_s on 2009-11-02
xfce4 in ubuntu is just as heavy as gnome cause it's using a lot more gnome parts.

"slow" can mean lots of things, more detail please.
example: app's open slow, scrolling draws slow, etc...

---

### Post by maxrocks_1 on 2009-11-03
Applications open slowly, my web browser is a lot slower: windows/pages open slower, typing is slower, scrolling is slower, switching to other windows is slower. It just feels really bogged down in general D:!

---

### Post by DFlame on 2009-11-03
If you really like XFCE, you might want to consider installing the very basic command line Ubuntu, then building upwards from there. This ensures that it is only as big as you want it to be, and you'll likely see a speed increase. The following guide was written for Hardy, but should work with Jaunty (perhaps Karmic) too.

[Guide part 1](http://disambiguation.wordpress.com/2008/08/15/new-life-for-my-old-computhttp://disambiguation.wordpress.com/2008/08/15/new-life-for-my-old-computer/)
[Guide part 2](http://disambiguation.wordpress.com/2008/08/17/a-minimal-ubuntu-install-the-basics/)
[Guide part 3](http://disambiguation.wordpress.com/2008/08/18/minimal-ubuntu-panels-firefox-and-a-launcher/)

That covers setting up the initial CLI, installing XFCE on top, then configuring additional applications & panels.

There's also the Ubuntu based [Crunchbang Linux](http://crunchbanglinux.org/). It uses Openbox and is incredibly nippy. It might be worth a go if speed is your thing :)

---

### Post by running_rabbit07 on 2009-11-03
I would suggest a clean install of Xubuntu 9.04 or 9.10 with EXT4 for the boot drive. It will make programs snappier without the worries of losing data while moving the movies around.

Some say Xubuntu is heavy, but it is still lighter and faster than Ubuntu. I have installed it a few times and loved it. It was just missing a few functionalities that I like from gnome.

Good luck.

Edit. You may want to look into loading Debian. On average, it uses less memory and CPU, than Ubuntu.

---

### Post by maxrocks_1 on 2009-11-03
Sorry for not mentioning it earlier, but my master hard drive IS formatted to ext4, and was thus formatted during the fresh install.

And I don't WANT to build a system from scratch. If I had a burning desire to do that for speed, then I'd be running Debian+xfce, which I am obviously not. I'm running Xubuntu because I like Xubuntu, and see no reason why Xubuntu shouldn't work on my system. I came here seeking fixes for Xubuntu (this being an Ubuntu forum, and this thread having a Xubuntu tag).

I was thinking that perhaps the video/graphics card might be part of the problem as I recall reading something about screwy driver files? But could that really slow the hell out of one's system? Any *other*, constructive ideas there, people?

~Maxwell

---

### Post by Praxicoide on 2009-11-03
Yeah, check out top or system monitor to see what processes you have running.

Back in 8.10, I had a problem with apt-xapian-index hogging resources, without it really doing anything. I uninstalled it and problem solved.

You could try installing the xfce4-goodies package, which will replace a lot of gnome-dependencies with lighter xfce stuff.

---

### Post by running_rabbit07 on 2009-11-03
> **maxrocks_1 said:**
> Sorry for not mentioning it earlier, but my master hard drive IS formatted to ext4, and was thus formatted during the fresh install.

I was thinking that perhaps the video/graphics card might be part of the problem as I recall reading something about screwy driver files? But could that really slow the hell out of one's system? Any *other*, constructive ideas there, people?

~Maxwell

Are you using Karmic or Jaunty? Have you  used System Monitor to see what is using up the resources? What graphics card are you using?

---

### Post by winotree on 2009-11-03
Maybe try changing **network.dns.disableIPv6** from *false* to *true* in **about:config**.  I've read that has helped several users here.

---

### Post by maxrocks_1 on 2009-11-06
I am running Karmic, and am now noticing the same slowness in Karmic Ubuntu (not Xubuntu).

---


---
title: "Xorg CPU usage goes to 99%+ after idling with xbmc"
date: 2010-05-27
forum: General Help
---

### Post by mgchan on 2010-05-27
I use my second machine mainly as an xbmc box, but for the past few months it has come across a problem where if I idle for a certain period while running xbmc, eventually my Xorg process will basically hang, using 99% or more of my CPU. I can rescue my machine via ssh if I stop the gdm service and then kill the Xorg process, but re-starting gdm will cause Xorg to immediately use 99% again, even if xbmc is no longer running.

This will invariably occur if xbmc is running, and never occurs if not. I believe sometimes it also will happen if I am actually using xbmc, but usually it happens when idling. I have tried changing the screen saver to a blank screen, thinking that maybe the screen saver was causing some kind of graphics driver problem, to no avail.

I understand if this should be posted at the xbmc problems but the fact that the problem persists after shutting down xbmc and restarting gdm/Xorg suggests to me that something is going awry outside of xbmc. The logs for both xbmc and Xorg do not reveal anything that would suggest why things would all of a sudden break. 

I am running xbmc on a retired mythbuntu installation, x86_64, which has had most of the myth stuff removed. I already disabled/uninstalled pulseaudio and compiz. This phenomenon occured all way way back with Gutsy Gibbon and I have since tried every upgrade in between, now on Lucid Lynx. I have also tried with both stable and daily SVN builds of xbmc.

Any ideas on where I might start debugging this problem? What is confusing to me is that xbmc seems to be stable, and so does Xorg. If I had to guess it would be a driver issue, though I have also tried multiple versions of the Nvidia driver as well (currently using 195.36.07.03).

Any help is appreciated.

---

### Post by byStanderone on 2010-05-27
...that could burn your cpu if unnoticed for a long time, perhaps you should stop using xbmc until you got the issue solved.

---

### Post by mgchan on 2010-05-27
Yeah, for that reason I usually have xbmc shut off and set up my remote to open xbmc only when needed. That's how I know that it's fine without xbmc running, although sometimes while I am watching a movie it will kick in.

---

### Post by Dugger5688 on 2010-06-08
Maybe remove xbmc completely, remove all of the graphics drivers. Then go here:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Enable that PPA and get the newest graphics drivers (should be 256.~) and then do:

```

sudo apt-get install libvdpau1

```

Then, add the XBMC ppa again and reinstall XBMC. I had a similar problem, turned out that I was still using a Karmic repo for something.

Also, make sure no remote desktop connections are open. 

This problem seems weird, as I have a 64 bit running XBMC that routinely has uptimes of >30 days before I decide I should shut if off for the night and save some money.

---


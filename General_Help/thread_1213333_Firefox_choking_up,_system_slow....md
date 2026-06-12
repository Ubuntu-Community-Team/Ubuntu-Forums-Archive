---
title: "Firefox choking up, system slow..."
date: 2009-07-14
forum: General Help
---

### Post by Nazaroo on 2009-07-14
I have so far guessed it could be one of three things:

(1) low RAM memory (I had  512M installed when this started happening)

(2) disk space running out (I had a warning of only 750 Meg of diskspace in a copy operation.  This doesn't seem right, since although the boot drive is small (10 Gig) it is supposed to have about 4 Gig free at the moment.  Could the warning refer only to a system folder?)

(3) Both. 

(4) My internet service (Bell Canada) is intermittent/sucks, or is being monitored by horrible automated anti-terrorist piping streams, which add needless time to webpage loads, simply because I may have hit a few porn sites recently.

Any ideas?

The specific symptoms are that some pages load well (like harmless sites), while big ones like Google etc.  and searchs just stall to the point of me being forced to close a tab and try again.

Also, pages refresh slowly, i.e. they roll down the screen sluggishly.


thanks
Nazaroo

---

### Post by dlmarti on 2009-07-14
1. 512 is pretty small now a days.  If you really only want to run Linux with this much please make sure your running an older version of Ubuntu.

2. from the command line "df -h" will tell you how much space you have on each partition.

3. see above.

4. sites like you specified require a larger number of connections, not just a simple bandwidth calculation problem.  Keep a watch on your usable bandwidth by using one of the web's speedtest sites.  If the speedtest is slow, so will your browser experience be.

5. cut down on the porn, you'll have a better sex life.

---

### Post by lovinglinux on 2009-07-14
**Do you have the latest drivers for your graphic card?**

Go to "System >> Administration >> Hardware Drivers" and install the proper driver.

**Do you have an Intel graphics card?**

[Jaunty Intel Graphics Performance Guide](http://ubuntuforums.org/showthread.php?t=1130582)

**Do you have Remote Desktop enabled?**

Go to  "System >> Preferences >> Startup Applications (aka Session)", disable Remote Desktop there and reboot.

For additional tips and tweaks visit:

[Tips: Things that might improve Jaunty performance](http://ubuntuforums.org/showthread.php?t=1152095)

[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by Nazaroo on 2009-07-17
Okay I disabled the "remote desktop" feature on the System/Startup Applications.

Actually, I may have done too much.  I also deleted the entry accidentally from the list...

I don't know how to put it back.

I am now runing an nVidea MX 440 on a PCI slot.  I gave up trying to enable both it and the onboard card for two screens.  I hope to do this somehow later...and yes I have the proprietary driver (nVidea 96) enabled.

I still don't get 3d graphics enabled, but it may just be this shitty graphics card.

Anyway, I looked through some of the other suggestions in your links but  got overwhelmed.

**I am surprised that "Remote Desktop" was enabled by default. **  It sounds like a spyware backdoor entrance to my box.

I also tried to change the **"swappiness"** parameter in some conf file, but I couldn't find it there and was afraid to add it.
I now have 1 Gig of RAM and should be able to swap less often...any help on that?


thanks, hoping for more suggestions too.

Nazaroo

---

### Post by khelben1979 on 2009-07-17
You might also look at the [Opera web browser]("http://en.wikipedia.org/wiki/Opera_web_browser") to see if you can get more speed over there.

What version of Firefox are you using? [Firefox 3.5]("http://en.wikipedia.org/wiki/Firefox#Version_3.5") is pretty fast.

---


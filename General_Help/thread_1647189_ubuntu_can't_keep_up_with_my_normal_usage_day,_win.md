---
title: "ubuntu can't keep up with my normal usage day, windows vista can"
date: 2010-12-16
forum: General Help
---

### Post by mateomiguel on 2010-12-16
Man, I'm trying really hard to like Ubuntu, and I've been using it for about a year, but its getting really hard to justify continuing to use it.  My normal use day makes Ubuntu just crap out again and again, while Windows Vista has no problems at all.  I have a Dell Inspiron 1440 laptop dual-booting windows vista and ubuntu 10.10 on it, and I've just been using windows vista more and more because it just causes me less problems. Here are the issues that I keep running into:

Normal Day of Use:

1.  Pack up my laptop into my bag, go to work, unpack laptop.
 **- Windows Vista:**  no problems going to sleep/waking up
 **- Ubuntu 10.10:**  Doesn't wake up from sleep mode.  Have to pull battery and reboot from scratch every single morning.  (ubuntu 10.04 had no problems here)

2.  Plug in my horizontally-oriented 1080x1920 generic LG monitor that my boss bought especially for me to do my work.
 **- Windows Vista:**  no problems, in fact remembers the monitor from last time and automatically adjusts the desktop and settings with one or two flickers of the screens.
 **- Ubuntu 10.10:** Must open up ATI control panel and select multiple monitor configuration, specify 1680x1050 because 1080x1920 never works, then hit okay.  Note yet again that I have to restart the system for the changes to take place.  I log out and log back in and go back to the control panel again, this time changing the configuration of my external monitor from normal to 90 degrees left.  I also move the relationship of the monitors so that the bottom of my laptop monitor lines up with the bottom of my desktop monitor.  Hit okay.  It works, with my desktop monitor at a reduced resolution than maximum.  However, the desktop icons on my Ubuntu desktop are now gone, because they are sitting at the top left hand corner of the virtual screen which no monitor is displaying.  Also, there are several ways for the machine to hang during this process.  If I let it use the default resolution for the external monitor, 1080x1920, then relog, the machine will not successfully display anything.  If I have to reboot the machine while leaving the external monitor plugged in, it will hang after the initial screen.  If I try to plug in the monitor first in the morning before booting up the machine, it will hang on boot.  It took me a long time to figure out how to actually make the multi-monitor thing work at all.

3.  Edit Word .doc format documents while tracking changes.
 **- Windows Vista:** Using Microsoft Word 2007, I have zero problems with this.
 **- Ubuntu 10.10:** I also have zero problems editing documents using the track changes feature in OpenOffice Writer.  It is also snappier and faster, and the search/replace function works better.  This is one redeeming factor of Ubuntu 10.10 and one reason why I keep it around.

4.  Listen to music, chat with friends, surf the Internet, and keep tabs on Facebook.
 **- Windows Vista:** I can use Winamp, Digsby, Google Chrome, and Digsby again to somewhat adequately perform these tasks.  Slightly clunky and unintegrated, however.
 **- Ubuntu 10.10:** Ok Ubuntu shines here.  Everything is all on the bar, chrome runs like a dream.  This is the other redeeming factor and the other reason why I keep it around.

5.  Unplug everything and go home, where my vertically-aligned 1680x1040 widescreen monitor is waiting for me to watch movies on.
 **- Windows Vista:** Remembers this monitor too and automatically adjusts itself to previous settings.  Movies play adequately with VLC player, but sometimes stuttery, even on modern hardware.
 **- Ubuntu 10.10:** I have to go through the whole song and dance again to make things work here.  Takes about 5 minutes of annoyance.  Movies play wonderfully and smoothly at all times after I get the monitor set up though.

6.  Do web development for my second job.  
 **- Windows Vista:** I won't even go there.  Do not get me started.
 **- Ubuntu 10.10:** Ok the system was built for development.  It is a dream once again.

7.  Play World of Warcraft after a job is done.
 **- Windows Vista:** No problems, automatic start-up, smooth sailing.
 **- Ubuntu 10.10:** Supposedly you can get WoW to run via WINE, but I haven't done much more than install wine and try to make it run wow.exe, which failed.  I guess its a whole long process or something?

Ubuntu's two main problems for me are not waking up after closing the lid, and the inability for my system to fully exploit the monitors I plug into it.  But these two things create such annoyances that they are almost game breakers for me.  I've researched, experimented, changed settings, and nothing I do has fixed these problems.  Ubuntu is just not up to snuff.

---

### Post by Scunizi on 2010-12-17
Find an Nvidia card on ebay or similar then head over to google and search for PPA nvidia-vapau .. in there will be a link for the PPA holding the latest binary.

Next check your swap partition for it's size.. compare that against your ram.. if you leave programs open when you sleep the machine your swap should be at minimum the amount of your ram.. some say 2x of your ram but I'll leave that up to you.  My dell vostro 1400 and Thinkpad T42 have no issues sleeping..

---


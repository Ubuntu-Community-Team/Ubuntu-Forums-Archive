---
title: "Reverting Shiretoko to Firefox 3.0"
date: 2009-11-11
forum: General Help
---

### Post by Mixalis0 on 2009-11-11
Hello,

I recently followed the instructions at [http://www.ubuntugeek.com/install-firefox-3-5-or-firefox-3-6-beta-in-ubuntu-jauntyintrepidhardy.html](http://www.ubuntugeek.com/install-firefox-3-5-or-firefox-3-6-beta-in-ubuntu-jauntyintrepidhardy.html) to upgrade from Firefox 3.0 to what I admittedly thought was Firefox 3.5. (I'm using Jaunty --- don't really have the time right now to upgrade.) Instead, I now of course have Shiretoko, which I probably should have figured out would have happened. At any rate, I'd really like to revert to the more stable Firefox 3.0 for right now and begin using Firefox 3.5 when I upgrade to Karmic. 

Could anyone provide some help in undoing the instructions found at the above link?

Also, if anyone has a link to the correct way to upgrade to the stable Firefox 3.5 (instead of Shiretoko) while using Jaunty (if such a thing is even possible), it would be much appreciated.

Thanks in advance and sorry if this has already been asked.

---

### Post by fooman on 2009-11-11
shiretoko is the stable firefox 3.5....just branded as shiretoko.  i would stick with that over an older version if i were you.

there is a really simple fix to the branding issue,  which will change the name, icon and point links to the new version.  see here to fix it and enjoy firefox 3.5:

[http://ubuntuforums.org/showthread.php?t=1225754&highlight=firefox+branding](http://ubuntuforums.org/showthread.php?t=1225754&highlight=firefox+branding)

---

### Post by Zoot7 on 2009-11-11
```
sudo apt-get remove firefox-3.5 firefox-3.5-gnome-support && sudo apt-get install firefox
```
That should do it for you.

Another option is to simply download the archive from mozilla's site and extract to wherever you want (/opt is a good place IMO). Then add the command sh /opt/firefox (or wherever the main file is) to the menu in the form of a launcher.

---

### Post by 64bitguy on 2009-11-11
Hi

Regarding this subject, I have a few questions:

1) Is there a complete Firefox 3.0.15 "Package" for 9.10?  (I REALLY looked and can't find one anywhere)

2) What are the processes necessary to clean everything up and install Firefox 3.0.15 with all of the normal Ubuntu and Firefox add-ons?  Please note that I'm mainly talking about those applied by both the default 3.5.4 as well as to LATER and/or any other versions for (as i've already tried all of the LATER nightly builds of Shiretoko to resolve these issues too!)?  

**My** issues (and I'm not the only one) have always progressed from using any Firefox 3.5 (or beyond) build.  Because of this, I prefer 3.0.15 over all other Firefox builds as it is compatible with the add-ons that I use everyday and it doesn't hang (fail to load) pages, stick (huge latency issues just trying to find pages), have links not work at all or other REALLY annoying problems.  From my perspective, these issues outweigh the browser support timeline issues that I'm sure someone will mention.  I don't care, I'll take the 4 months (which I suspect will be extended).

I should mention that this is my situation with _**ALL**_ versions beyond 3.0.15 (regardless of Operating System Platform) on this computer. 

The Firefox options to which I refer (that is, being needed for 3.0.15) include Java, Acrobat, MPG, AVI, Quicktime, etc...

While I haven't had any problems using Mozilla's Firefox 3.0.15, what I am discovering is that getting these things into it 3.0.15 (and to a lesser extent removing the left-overs from the newer builds of Firefox) is an ongoing problem.  I've tried the Sun Java installation instructions without success (I suspect because there is so little documentation to address these issues specifically for 9.10 versus other, very much different Linux builds).  I even tried USC uninstall reinstall of the older (the only option) Sun Java; however, it doesn't appear to properly associate with 3.0.15 either. 

As for the commands on other help pages even here (of which there are many) fail to address this in 9.10 specifically.  

Thanks for any help that can be provided.

---

### Post by Zoot7 on 2009-11-12
> **64bitguy said:**
> Hi

Regarding this subject, I have a few questions:

1) Is there a complete Firefox 3.0.15 "Package" for 9.10?  (I REALLY looked and can't find one anywhere)
Not to my knowledge. Karmic by default comes with Firefox 3.5.

---


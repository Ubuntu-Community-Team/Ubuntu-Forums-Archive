---
title: "Making Ubuntu boot and run faster"
date: 2009-11-24
forum: General Help
---

### Post by konradpiskorz on 2009-11-24
After running Ubuntu for a couple years now.  I've learned astronomical amounts about proper computer administration.  In fact I can thank Linux for teaching me how to properly install, secure and strip windows of all the junk so it can be run reliably!

Although to do the same in Linux is a long and arduous and much more intimidating journey.

So how does one speed up an Ubuntu system?  I know my system is a lot slower now than it can and should be.  Its just a matter of not knowing where to go.

I installed bootchart and it gave me a pretty picture of my bootup and I know absolutely nothing about what to do with it.

I would like to make a custom boot using init 4 to test out what can and cannot be left out of my system, after all I don't need all of Ubuntu's default stuff loading.  Where is a good resource on how to do this?  I've been digging through man pages and the root directory and found SOME things that I am deftly afraid of touching.

Firefox especially has been running incredibly unreliably as of late(crashing).  Is it the java version being used? Is it just firefox?  Or is it plug-ins for flash and the like.  Also why do flash videos crash firefox when the 'firefox modifications for ubuntu' extension is activated?  How would I go about changing settings which may effect this?

Can I make my ubuntu also able to use XFCE and GNOME as the same user?  I feel this would impact performance greatly when I need it!  Also how(if I) can I strip down gnome to get rid of unnecessary resource use?

Can I also choose to load compiz on login or not?  It's pretty but sometimes productivity is more important than pretty looks, having an option on login/boot would be amazing!  Same goes for XFCE/GNOME as I mentioned before.

Where can I get at ubuntu's sound and video heart so that it I can get things like gnomes volume control to work?  I already removed pulse audio after the massive headache it caused.

These are just some questions I have.  If anyone can provide any help or resources to look into I would greatly appreciate it.  I want to step up my level of linux knowledge though I want to do it within the Ubuntu environment and not install a different distro which gives me more flexibility out of the box.  Ubuntu works but it can work better.  What can I do?

---

### Post by audiomick on 2009-11-24
Hi.
Can't help with most of that, although a fair bit of it would interest me too.

As far as Gnome and XFCE goes, if you have both installed, you can choose at login which one you want to log into. There is a dropdown at the bottom of the login screen that appears (in 9.10) after you select your user name. I think in 9.04 it was always visible.

Good luck with the rest of your questions.

---

### Post by konradpiskorz on 2009-11-24
Well thats good to know.  I did suspect that though I wasn't sure.  What would be the proper code to install it?  1 or 2?  I presume 1 though I am not sure.
```
1:sudo apt-get install xubuntu-desktop
2:sudo apt-get install xfce4
```

Also would there be a way to sync up gnome and xfce menus?

---

### Post by audiomick on 2009-11-24
I _guess_ the second variation. I get all my software with the GUI packt manager. system>administration > package manager.

I just did a search in there, and a meta package for xfce4 turns up. That would be the one you want, I reckon.

---

### Post by konradpiskorz on 2009-11-24
Well as it turns out the xfce4 package is a standard xfce4 desktop manager while xubuntu-desktop is xfce4 with all of ubuntu's tweaks and changes.  I ended up just installing the xfce4 package and it works FAST.

This is the first time my computer has been able to run 720p videos without any chopping whatsoever!  XFCE4 is extremely lightweight!  Fantastic!

Now if only any of my other questions could be answered

---

### Post by oldos2er on 2009-11-24
What are your system specs? Are you running 32-bit or 64-bit Ubuntu? Are you using ext4 file system?

 There's good info on optimizing Firefox and Flash: [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

 Also there's a lot of info on the 'net about speeding up Ubuntu in various ways (see [http://www.google.com/search?hl=en&lr=&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=joe&q=optimize+ubuntu+9.10+speed+&aq=f&oq=&aqi=g-p1](http://www.google.com/search?hl=en&lr=&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=joe&q=optimize+ubuntu+9.10+speed+&aq=f&oq=&aqi=g-p1)). You might want to ask here in the forums before making any system-wide changes; some of the info available is outdated. Make backup copies of any files you plan to edit.

---

### Post by sabre2th on 2009-11-24
If you want to get the most out of your system, I recommend doing a minimal install.  I use the [minimal CD image]("https://help.ubuntu.com/community/Installation/MinimalCD") and install the bare minimum of what I need.  You'd be surprised how many regular packages aren't necessary to have a fully-functional desktop.  I believe you can also do it with the Alternate CD image.  (Minimal CD will download the newest versions of everything; Alternate should not have to download during the install, though it will have to download updates after)

[This thread]("http://ubuntuforums.org/showthread.php?t=1155961") can get you started if you want to go down that path.

Edit: I don't do a ton of customization after that, but one thing I do recommend (if you have a decent amount of RAM) is setting swappiness to a low number (I generally use 5, but it's not an exact science.  Feel free to experiment).  [FAQ Link]("https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?")

Edit again: I'd also avoid the big metapackages like ubuntu-desktop when doing a minimal install, because those just put the majority of the extra stuff right back in.  Target specific packages that you need like Firefox, Pidgin, Network Manager, etc.

---

### Post by fluffman86 on 2009-11-24
Agreed with sabre2th.  Start with a minimal CD, then for a window manager install icewm or fluxbox.  They are orders of magnitude faster than XFCE, but take a bit of tweaking to get the menus to work right.  Tack on extra services only if you need them.

---

### Post by sabre2th on 2009-11-24
> **fluffman86 said:**
> Agreed with sabre2th.  Start with a minimal CD, then for a window manager install icewm or fluxbox.  They are orders of magnitude faster than XFCE, but take a bit of tweaking to get the menus to work right.  Tack on extra services only if you need them.
Thanks for the vote of confidence  :)

For the record, I'd say that Gnome is still fine to use on relatively modern computers, especially with the swappiness change I mentioned.  That's not to say there's anything wrong with other window managers; I'm just more comfortable with Gnome.

---

### Post by konradpiskorz on 2009-11-24
Interesting comments.  Doing a minimum reinstall is a bit more radical than what I am looking for right now.  I'm heavy into my research and having a dedicated laptop for databasing and heavy processing is a necessity.  I have been interested in seeing just how lightning fast I can get this laptop and icewm and fluxbox both look like good options.  I know I've taken a brief glance at their respective dev pages before.  Though my laptop is old, it still holds it own for everyday use.  I was just really impressed with the quality of high res video playback in xfce4.  (Planet Earth's Fresh Water segment has never been so clear!  Usually the data rate of thrashing water at 720p causes major issues!)   It's a significant step up from what I've seen in any OS config on this old boy.  Either way, I'm pretty happy with Gnome, I just want to know if I can push it a bit harder.

Now as far as perusing that level of optimization and personal configuration, I do have an old hard drive I can tinker on.  But I can't help but feel Ubuntu isn't the best suited for such things.  Each time a dist-upgrade occurs, the old one gets left behind in updates and doing a dist-upgrade always causes SOMETHING to break.  The horrors I experienced with pulse audio are enough to scar me there.  I think if I wanted to go that route, Open SUSE or Debian would be a better match.  I've got a Deb file server running on a 12 year old P2 and it hasn't skipped a beat yet.

As far as starting with a minimal CD though(and without ubuntu-desktop)  how much choice do I get?  Can I avoid pulseaudio that way?  It still lingers somewhere on my system now and if I just try to remove it apt-get grabs a few other packages I'm afraid to lose in case something breaks(one being ubuntu-desktop, what DOES that actually provide now that you said to avoid it?)

The resource for Firefox is FANTASTIC!  I'll let you guys know how big of a difference it makes once I actually test it out.

Now Ubuntu is my main system, so I try to keep it looking pretty.  A new wallpaper every 15 minutes.  Compiz (mainly for productivity, 2x2 desktops and the different variations on alt+tab but still have some eye candy going)

Now I am running a 32bit hardy heron 8.04 ubuntu on a toshiba tecra A6
Core Duo 1.83 Ghz 667MHz FSB
2.5GB RAM DDR2 667 MHz
250GB 5400rpm drive (Ubuntu sys on first sector)
Ati Radeon X1400

Hardly anything to write home about.  My HD is running ext3 file systems.  Been wary of going to ext4 for no reason.

I'm gonna take a look at the swapiness and see if that improves anything.  Just loaded up a bunch of programs(gimp, songbird playing,VLC high def movie,openoffice,firefox) and using free see that my swap partition isnt being used AT ALL...  Though compiz effects have turned a bit choppy...

Thanks a lot for all the advice so far guys!  Definitely got firefox working a lot better!  I think that was my only major issue!  Now I just want to trim some time off of start up.  Where can I find whats loading up and keep it from happening?

---

### Post by sabre2th on 2009-11-24
> **konradpiskorz said:**
> As far as starting with a minimal CD though(and without ubuntu-desktop)  how much choice do I get?  Can I avoid pulseaudio that way?  It still lingers somewhere on my system now and if I just try to remove it apt-get grabs a few other packages I'm afraid to lose in case something breaks(one being ubuntu-desktop, what DOES that actually provide now that you said to avoid it?)
Using a minimal install (doesn't have to be the minimal CD) gives you the maximum amount of choice possible.  It installs only the bare minimum to get you to a usable command line.  From there, you install whatever you want.  Pulse is only installed if you type the command to do it.

Ubuntu-desktop is really just a list of other packages that give you the default (Gnome) Ubuntu setup.  You can get the same thing by installing the individual packages without ubuntu-desktop.  A minimal install guarantees that nothing is there (and using resources) unless you specifically want it there.  It saves a bit of hard drive space too, but that's not usually an issue these days.

And, honestly, you could be done with a minimal install in the time it takes you to do your research.  Obviously make sure you have backups if you choose to make the jump, but it is the single best way to guarantee you have a slim, fast install.

---


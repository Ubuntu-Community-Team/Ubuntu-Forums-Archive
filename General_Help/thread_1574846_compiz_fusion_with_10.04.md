---
title: "compiz fusion with 10.04"
date: 2010-09-14
forum: General Help
---

### Post by mig96 on 2010-09-14
I run the final version of Lucid Lynx and have a 9800gt.  I followed the following procedure to install compiz (and I want compiz, not just the built in desktop effects) on my computer, all sudo with KDM disabled where necessary:
1. apt-get install nvidia-current
2. nvidia-xconfig
3. apt-get install build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc libwnck-dev python-dev python-pyrex
<- these were prerequisites mentioned by the guide on compiz.org
4. apt-get install  compiz compizconfig-settings-manager  compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra  emerald
At this point, everything installed successfully, and nvidia driver was working perfectly.  I verified this: desktop effects worked OOB.
5. compiz --replace &
6. emerald --replace &
At this point, compiz apparently started.  Emerald worked perfectly: all of the window decorations worked OOB.  I went and ran ccsm, and turned on quite a few settings.  It didn't enable ANYTHING.  When I reran ccsm, all of the settings were back to default, and enabling any new ones had no effect on window behavior.  Strange.  I looked on the web and found:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)
The ubuntu page said that I should not "Enable integration into the desktop environment" if gconf was selected.  BUT THE FLAT FILE CONFIGURATION WAS SELECTED BY DEFAULT.  Then I went back to the site and it said flat file configuration was recommended!
Maybe I shouldn't have enabled desktop effects first (NOTE THAT I LATER DISABLED IT and things still did not work)? I don't know what happened here.

---

### Post by hhh on 2010-09-14
mig, you're not allowed to double-post the same topic (especially 10 minutes apart). You need to wait 24 hours for a response and then you can bring your post up to the top of the forums again by making a new post in the same thread (posting "bump" is sufficient).

I don't use KDE but in Ubuntu Lucid compiz is almost completely installed by default, and I'd assume it's the same in Kubuntu. All you need to do is install compiz-config-settings-manager, compiz-fusion-plugins-extra and emerald to get the missing stuff.

Anyway, now that everything is installed and you've enabled both desktop integration and flat-file configuration, did you run the next sudo command and restarting X as stated in the community wiki page?

Be patient and someone with KDE experience will help you.

-edit- Did a mod already remove the double post? If so, thanks, if not, my apologies for hallucinating it!

---

### Post by mig96 on 2010-09-14
Thanks for your reply.  If I did double post, sorry, it was unintentional.
When I installed the packages, aptitude actually installed all of them.  None of the packages were skipped because they were already on the system.  I even checked KPackageManager, it didn't say I had any of the compiz packages.  Even if aptitude updated some of them, I don't know what issues that would cause.
Also, I restarted the entire computer after the install, and it still didn't work.
Also, a tl;dr to people new to the thread:
ccsm is just not saving any settings, not even temporarily.  It has absolutely no effect on window behavior :(

---

### Post by mig96 on 2010-09-15
Bump

---

### Post by hhh on 2010-09-16
Maybe try deleting ~/.config/compiz/compizconfig/Default.ini (a new one should get created by running compiz --replace again)?

---


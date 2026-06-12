---
title: "liborc-0.4-0 and ffmpeg (dependencies)"
date: 2011-04-04
forum: General Help
---

### Post by PABlanche on 2011-04-04
I try to install gstreamer0.10-ffmpeg but has the following error message trough synaptic:
The following package have unresolvable dependencies:
gstreamer0.10-ffmpeg:   Depends: liborc-0.4-0 (>=1:0.4.10) but 0.4.6-1 is to be installed

But when I look at liborc-0.4-0, the installed version is indeed 0.4.6-1.

I tried to remove and reinstall liborc without success.

Any suggestion?

I am running Ubuntu 10.10 64 bits.

---

### Post by PABlanche on 2011-04-12
I did not get too much help but will try my best to report how I solved this issue (might help someone).

Things began when the 0.6.2 version of ffmpeg was automatically installed by the update manager (03/26/2011). I noticed Kdenlive was no more able to upload any video clips. See bug report there: [http://www.kdenlive.org/mantis/view.php?id=2080](http://www.kdenlive.org/mantis/view.php?id=2080)

Report 2070 describe the same problem and fixed the issue by downgrading t offmpeg 0.6.1.
[http://www.kdenlive.org/mantis/view.php?id=2079](http://www.kdenlive.org/mantis/view.php?id=2079)

At that moment, avi and mp4 were still playing in movie player.

Then I had to convert a mp4 to avi and since kdenlive was not working anymore, I installed Avidemux GTK+. During the installation I had dependency error with Gstreamer and ffmpeg. I tried for a while to resolve the dependency problem but it get worst and worst each time (Liborc-0.4-0, ...). I tried reinstalling Ubuntu through the terminal but even if Ubuntu looked fine, it did not resolve the dependency.

So I decide to refresh my source list file (/etc/apt/sources.list) using the Ubuntu Source Liste Generator:[http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php), and that did it. It not only solved all the dependency problem between Gstreamer and ffmpeg but also solved the Kdenlive issue.

Everything fine now even if I do not really understand what happened.

---


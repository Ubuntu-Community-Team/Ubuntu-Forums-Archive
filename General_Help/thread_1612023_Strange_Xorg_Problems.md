---
title: "Strange Xorg Problems"
date: 2010-11-02
forum: General Help
---

### Post by Zookalicious on 2010-11-02
Hi, I looked around on the stickies and have been searching for forever but I don't think anyone else is having this problem. There's some weird things going on with Xorg I think.
 When I boot up at first, everythings OK, but after opening up any application (I tried several) the title bars and gnome-panel become unresponsive. I cannot switch to any other windows HOWEVER I can still type and interact with whatever happens to be open at the time and the compiz cube still works??? But compiz ring-switcher does not. If I wait for a while or click around furiously I will sometimes be able to interact normally, however it never lasts for long and inevitably I become unable to click on anything at all for longer periods of time. 

dmesg didn't turn up any warnings that I could see and I don't have any excesive RAM or CPU use (I checked top and everything was around 6 percent total). I also ran MemTest+ with no errors. 

Now when I type "sudo killall Xorg" into the terminal (sudo /etc/init.d/gdm restart and sudo service gdm restart both leave me hanging at the ubuntu logo for hours but I will deal with that later), it restarts X and I log back in and almost everything is fine. Except now I have no audio. The gnome indicator applet is grayed out and this has happened every time I have restarted X so far. 

Basically, does anyone have a clue what's happening here? I literally just had to do a reinstall last week because I screwed up stuff with nautilus-elementary and I finally got everything back the way I like it. I would really appreciate anyone's input. Thanks.

---

### Post by Zookalicious on 2010-11-05
I'm pretty sure the entire thing is done. I have a 300GB file called .xsessions.errors.old that keeps regenerating and eating all my disk space.... and booting up is a hit or miss situation, only works half the time.

---


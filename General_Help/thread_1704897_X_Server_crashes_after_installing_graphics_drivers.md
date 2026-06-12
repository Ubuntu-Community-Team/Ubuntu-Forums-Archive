---
title: "X Server crashes after installing graphics drivers."
date: 2011-03-11
forum: General Help
---

### Post by silkworm2.5 on 2011-03-11
Hi all!
I am having trouble with X after installing updated graphics drivers. I followed an online tutorial shown here: [http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

After installation, I noticed a massive increase in performance. unfortunately, X now seems to be unstable, and will crash sometimes when I use too many desktop effects at once. Usually when something is fading out while changing workspaces.

I can't use Ctrl-alt-backspace, but ctrl-alt-F* work to access a terminal.

The strange thing is, my friend who is more experienced with linux than me, showed me a command to use in the TTY* terminal to restart X
```
sudo /etc/init.d/gdm restart
```If I do this after X crashes, it will not crash at all any more. It is very strange, I decided to _try_ to break X with so many desktop effects and X didn't crash after using that code. I got around 10-15 Fps and it still wouldn't break.

Unfortunately, If I use this code before X crashes, it will still crash later, which is a big problem because I loose the data in any application I had open at the time.

I'm not sure if this is relevant, but that code opens X in TTY 8, when the default is 7. If I swap back to 7 after, it shows a frozen image of the code it usually displays during boot. (*Checking battery state... [OK] etc)

Any help is appreciated :) Additional info: Ubuntu 10.04 64 bit, Dual core 4.40 GHz processor with 4GB of RAM.

---


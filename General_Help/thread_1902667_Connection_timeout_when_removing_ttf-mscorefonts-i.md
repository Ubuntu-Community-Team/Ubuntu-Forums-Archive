---
title: "Connection timeout when removing ttf-mscorefonts-installer"
date: 2011-12-31
forum: General Help
---

### Post by taoy0123 on 2011-12-31
I'm new to Ubuntu (and linux in general). The version I'm using is Ubuntu 10.10

I wanted to burn mp3 on cd with Brasero, so I tried installing Ubuntu Restricted Extras from Software Center, it freezes on "applying changes" so I restarted my computer.

Then seeing Ubuntu Restricted Extras showing up as "installed" in Software Center I tried to burn mp3 with Brasero, but after drag/drop the file Brasero freezes. So I wanted to re-install using commandline this time.

First I tried removing Ubuntu Restricted Extras in software center, software center freezes so I had to restart my computer.

Then I tried removing Ubuntu Restricted Extras in terminal. However the process kept trying to connect to various networks including "download.source.net...". Most of the attempts failed with "timeout", some "Connected" but showed http ERROR 404

Then I tried removing ttf-mscorefonts-installer in terminal but the same problem - Connection timeouts, endless attempt to connect.

I then login as root and deleted ttf-mscorefonts-installer.deb in "var/.../archives", but seemed to make no difference to my situation.

Please help :)

---

### Post by 2F4U on 2011-12-31
Which download mirror do you use? It may be worth changing the mirror through the package manager.

---

### Post by taoy0123 on 2011-12-31
I referred to "http://www.ubuntugeek.com/how-to-select-fastest-mirror-in-ubuntu.html" but did not make any difference.

This is what it looks like in the terminal:

-- date time-- [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... failed: Connection timed out.
Giving up

-- date time-- [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
Resolving switch.dl.sourceforge.net... 32.1.6.32, 2001:620:0:1b::21
Connecting to switch.dl.sourceforge.net|32.1.6.32|:80... failed: Connection time out.
Connecting to switch.dl.sourceforge.net|2001:620:0:1b::21|:80... failed: Network is unreachable

---


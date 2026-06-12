---
title: "uninstall packages from synaptic history"
date: 2010-05-14
forum: General Help
---

### Post by ShizzlePDX503 on 2010-05-14
this is my commit log that I got from synaptic. I was trying to compile a application but was getting too many errors due to dependencies that I didn't have installed and so I tried installing them but kept getting more errors so I decided to cancel the compile altogether so I can I easily purge all of these packages?

```
Commit Log for Fri May 14 16:41:20 2010


Installed the following packages:
build-essential (11.4build1)
debhelper (7.4.15ubuntu1)
dpkg-dev (1.15.5.6ubuntu4)
g++ (4:4.4.3-1ubuntu1)
g++-4.4 (4.4.3-4ubuntu5)
html2text (1.3.2a-14build1)
intltool-debian (0.35.0+20060710.1)
libatk1.0-dev (1.30.0-0ubuntu2)
libcairo2-dev (1.8.10-2ubuntu1)
libcairomm-1.0-dev (1.8.0-1build2)
libdbus-1-dev (1.2.16-2ubuntu4)
libdirectfb-dev (1.2.8-5ubuntu2)
libdirectfb-extra (1.2.8-5ubuntu2)
libexpat1-dev (2.0.1-7ubuntu1)
libfontconfig1-dev (2.8.0-2ubuntu1)
libfreetype6-dev (2.3.11-1ubuntu2)
libgconf2-dev (2.28.1-0ubuntu1)
libgconfmm-2.6-1c2 (2.28.0-1)
libgconfmm-2.6-dev (2.28.0-1)
libglib2.0-dev (2.24.0-0ubuntu4)
libglibmm-2.4-dev (2.24.1-1)
libglibmm-utils-dev (0.4.1-0ubuntu1)
libglibmm-utils2 (0.4.1-0ubuntu1)
libgtk2.0-dev (2.20.0-0ubuntu4)
libgtkmm-2.4-dev (1:2.20.2-1)
libgtkmm-utils-dev (0.4.1-0ubuntu1)
libgtkmm-utils2 (0.4.1-0ubuntu1)
libice-dev (2:1.0.6-1)
libidl-dev (0.8.13-1)
libjpeg62-dev (6b-15ubuntu1)
libmail-sendmail-perl (0.79.16-1)
liborbit2-dev (1:2.14.18-0.1)
libpango1.0-dev (1.28.0-0ubuntu2)
libpangomm-1.4-dev (2.26.1-1)
libpixman-1-dev (0.16.4-1ubuntu2)
libpng12-dev (1.2.42-1ubuntu2)
libpthread-stubs0 (0.3-2)
libpthread-stubs0-dev (0.3-2)
libsigc++-2.0-dev (2.2.4.2-1)
libsm-dev (2:1.1.1-1)
libstdc++6-4.4-dev (4.4.3-4ubuntu5)
libsys-hostname-long-perl (1.4-2)
libsysfs-dev (2.1.0-6)
libx11-dev (2:1.3.2-1ubuntu3)
libxau-dev (1:1.0.5-1)
libxcb-render-util0-dev (0.3.6-1build1)
libxcb-render0-dev (1.5-2)
libxcb1-dev (1.5-2)
libxcomposite-dev (1:0.4.1-1)
libxcursor-dev (1:1.1.10-1)
libxdamage-dev (1:1.1.2-1)
libxdmcp-dev (1:1.0.3-1)
libxext-dev (2:1.1.1-2)
libxfixes-dev (1:4.0.4-1)
libxft-dev (2.1.14-1ubuntu1)
libxi-dev (2:1.3-3)
libxinerama-dev (2:1.1-2)
libxrandr-dev (2:1.3.0-3)
libxrender-dev (1:0.9.5-1)
orbit2 (1:2.14.18-0.1)
po-debconf (1.0.16)
x11proto-composite-dev (1:0.4.1-1)
x11proto-core-dev (7.0.16-1)
x11proto-damage-dev (1:1.2.0-1)
x11proto-fixes-dev (1:4.1.1-2)
x11proto-input-dev (2.0-2)
x11proto-kb-dev (1.0.4-1)
x11proto-randr-dev (1.3.1-1)
x11proto-render-dev (2:0.11-1)
x11proto-xext-dev (7.1.1-2)
x11proto-xinerama-dev (1.2-2)
xtrans-dev (1.2.5-1)
xz-utils (4.999.9beta+20091116-1)
zlib1g-dev (1:1.2.3.3.dfsg-15ubuntu1)
```

---

### Post by ShizzlePDX503 on 2010-05-14
alright so I kind of went and did it this way;

I copied the text from the commit log and removed the information that was in "()" and then pasted the leftovers in terminal like this:

```
sudo dpkg -P build-essential debhelper dpkg-dev g++ g++-4.4 html2text intltool-debian libatk1.0-dev libcairo2-dev libcairomm-1.0-dev libdbus-1-dev libdirectfb-dev libdirectfb-extra libexpat1-dev libfontconfig1-dev libfreetype6-dev libgconf2-dev libgconfmm-2.6-1c2 libgconfmm-2.6-dev libglib2.0-dev libglibmm-2.4-dev libglibmm-utils-dev libglibmm-utils2 libgtk2.0-dev libgtkmm-2.4-dev libgtkmm-utils-dev libgtkmm-utils2 libice-dev libidl-dev libjpeg62-dev libmail-sendmail-perl liborbit2-dev libpango1.0-dev libpangomm-1.4-dev libpixman-1-dev libpng12-dev libpthread-stubs0 libpthread-stubs0-dev libsigc++-2.0-dev libsm-dev libstdc++6-4.4-dev libsys-hostname-long-perl libsysfs-dev libx11-dev libxau-dev libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev orbit2 po-debconf x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev xz-utils zlib1g-dev
```

I was hoping there was a easier way but none the less it got the job done!

---


---
title: "WINE IE now default Nautilus image app?"
date: 2011-03-13
forum: General Help
---

### Post by nathan28 on 2011-03-13
10.04 64-bit.

Images in Nautilus are opening by default with Internet Explorer in WINE. This problem *appeared* to start when I installed and then removed the python-nautilus package in an effort to get nautilus tagging to work in tracker and zeitgeist. (Tags in tracker are also not working)

Here are |grep image results for defaults.list and ~/.local/share/applications/mimeapps.list
/usr/share/applications/defaults.list

mimeapps.list
> image/jpeg=eog.desktop;
image/png=eog.desktop;wine-extension-png.desktop;shutter.desktop;firefox-4.0.desktop;f-spot-view.desktop;kde4-okularApplication_kimgio.desktop;gimp.desktop;

defaults.list
> image/bmp=eog.desktop
**image/gif=eog.desktop**
image/jpeg=eog.desktop
image/jpg=eog.desktop
image/pjpeg=eog.desktop
image/png=eog.desktop
**image/svg+xml=eog.desktop**
image/tiff=eog.desktop
image/vnd.rn-realpix=totem.desktop
image/x-bmp=eog.desktop
image/x-gray=eog.desktop
image/x-icb=eog.desktop
image/x-ico=eog.desktop
image/x-png=eog.desktop
image/x-portable-anymap=eog.desktop
image/x-portable-bitmap=eog.desktop
image/x-portable-graymap=eog.desktop
image/x-portable-pixmap=eog.desktop
image/x-psd=gimp-2.2.desktop
image/x-xbitmap=eog.desktop
image/x-xpixmap=eog.desktop
x-content/image-dcf=f-spot-import.desktop
x-content/image-picturecd=f-spot-import.desktop

Permissions on the files:
> -rw-r--r-- 1 root root 8873 2011-03-09 23:32 /usr/share/applications/defaults.list
-rw-r--r-- 1 nathan nathan 923 2011-03-13 13:59 /home/nathan/.local/share/applications/mimeapps.list



JPG and PNG now open as desired in eog.desktop. But I know that SVG and GIF still default to wine-internet-explorer. Which is wrong--the default at the system level should be eog.desktop.

So where is this other default hiding?

If I do a locate mime, there's almost 1200 non-icon files that show up, many are XML. I looked in the system log to try and find something b/c I found some ppl having similar issues but couldn't find anything, though I'm not l33t enough to figure out the sys log really.

Changes made via right-click in Nautilus do *not* stick through logout or reboot. So far it looks like manual changes to mimeapps.list do work.

Should I go sudo apt-get remove --purge nautilus && sudo apt-get install nautilus? That's hardly the elegant choice here.

---


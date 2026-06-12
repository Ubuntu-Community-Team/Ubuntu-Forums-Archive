---
title: "Can't close Firefox + Flash player problem"
date: 2010-03-11
forum: General Help
---

### Post by RowanHanzi on 2010-03-11
Hi,

I'm using Ubuntu karmic.

1) I can't close Firefox. When I click on the close button, nothing happens. (firefox 3.5)

2) I can watch videos on Youtube but it's impossible to use button on the video player. It's a problem with flash player. Flash games doesn't work at all. I have already tried to uninstall and install new version of flash. It worked about 15min and the bug reappear :mad:

Do you have solutions?

Thanks to respond.

---

### Post by lovinglinux on 2010-03-11
For the problem with closing Firefox see [this](http://lovinglinux.megabyet.net/?page_id=220#Troubleshooting-1).

For the flash issue, use the [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595). This tool  will install the best flash version according to your CPU architecture and will also attempt to remove any left-overs from previous  installations, thus helping to avoid conflicts with manually installed plugins.

For additional tips and instructions see the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by ghostborg on 2010-03-11
Right click on top panel and select "Add to Panel" from the menu. Add Force quit from the list.

This should help close that Firefox until you get it fingered out.


I am running the AMD64 version.
I think you have to copy the latest Adobe flash beta to the
/home/(whateveryounamed)/.mozilla/plugins directory.

The .mozilla is a hidden directory in your home folder that can be revealed by selecting "show hidden files" in the View menu of Nautilus file browser.
If plugins is not there then create it and copy libflashplayer.so into it.
This is my path /home/mike/.mozilla/plugins

You can verify that your flash player has loaded by typing "about:plugins" in the firefox url.

Wierd the smile face is covering a colon and the leter p for about(colon)plugins

---


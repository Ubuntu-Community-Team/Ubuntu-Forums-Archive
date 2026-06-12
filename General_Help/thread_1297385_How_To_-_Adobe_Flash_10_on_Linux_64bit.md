---
title: "How To - Adobe Flash 10 on Linux 64bit"
date: 2009-10-21
forum: General Help
---

### Post by MountainX on 2009-10-21
[http://xkcd.com/619/](http://xkcd.com/619/)

[IMG]http://imgs.xkcd.com/comics/supported_features.png[/IMG]

Actually, that's not entirely true. I am finally enjoying good flash on ubuntu 9.04 amd 64 using Swiftweasel and Adobe Flash 10. But I enjoy the humor because I had to put up with that frustration for so long.

Here's how I installed Flash. You can do this installation just by copying and pasting the following in a terminal:

```
wget http://queleimporta.com/downloads/flash10_x64_en.sh && sudo chmod +x flash10_x64_en.sh && sudo sh ./flash10_x64_en.sh
```
You should always read and understand scripts before running them.

This script will install Native 64 Bit Flash 10 and will also remove previous versions of flash and the not needed anymore “nspluginwrapper”

Note: If you just want to see the code for the script, it is available here:
[http://queleimporta.com/downloads/flash10_x64_en.sh](http://queleimporta.com/downloads/flash10_x64_en.sh)

See more here:
[http://queleimporta.com/finally-adobe-releases-native-64-bit-flash-10-for-linux/](http://queleimporta.com/finally-adobe-releases-native-64-bit-flash-10-for-linux/)

I did not create any of this. Thank Alejandro Cuervo and others. I simply wanted to post the cartoon. :)

---

### Post by Woody1987 on 2009-10-21
cant you just do sudo apt-get install flashplugin-nonfree? On a 64bit system that will install the 64bit flash for you.

---


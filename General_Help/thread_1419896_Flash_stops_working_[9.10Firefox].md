---
title: "Flash stops working [9.10/Firefox]"
date: 2010-03-02
forum: General Help
---

### Post by Nuskrad on 2010-03-02
Hi all,

I installed Ubuntu 9.10 a few weeks ago using the Wubi installer and have so far been fine. The only problem I'm having is with Flash, it works fine for a while but then I'll go to a page and the flash applet won't appear. To fix it is a simple case of closing Firefox and reopening it, I can even save the tabs and when they are recovered the flash will work fine.

I've seen a few other threads on the issue that had various suggestions, such as completely removing all traces of Flash and reinstalling it and uninstalling AcroRead incase that caused conflicts, they have not solved the problem. I also tried disabling Adblock Pro in case that was causing the issues, but it has not helped either.

Can't think of anything else to try, like I say it's not a major issue, just a bit of an annoyance but I would like it solved if possible.

Details:
Ubuntu 9.10 (karmic)
Kernel: 2.6.31-19-generic (#56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010)
Processor: Intel(R) Core(TM)2 Duo CPU     T5450
Firefox: 3.5.8
Flash: 10,0,45,2 
Flash plugin details - File name:  npwrapper.libflashplayer.so Shockwave Flash 10.0 r45

Any more details that you need just let me know

---

### Post by lovinglinux on 2010-03-02
I guess you are using a 64bit system, so try the 64bit beta version of flash.

Use the [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595). This tool  will install the best flash version according to your CPU architecture and will also attempt to remove any left-overs from previous  installations, thus helping to avoid conflicts with manually installed plugins.

For additional tips and instructions see the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by dcstar on 2010-03-02
> **lovinglinux said:**
> I guess you are using a 64bit system, so try the 64bit beta version of flash.

Use the [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595). This tool  will install the best flash version according to your CPU architecture and will also attempt to remove any left-overs from previous  installations, thus helping to avoid conflicts with manually installed plugins.

For additional tips and instructions see the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Here is a script I just knocked up to fetch and install the latest 64-bit development Flash release from the Adobe site, it may be of use to some people as a root cron job to keep up to date or manually run (using sudo):

```
#!/bin/bash
# Get-Flash-64
# Fetch latest Linux 64-bit development Flash Player from Adobe site and extract and install automatically
# 03/03/2010 David Clayton
#
# Run as sudo!
#
#If not 64-bit then abort
if [ `uname -m` != 'x86_64' ]
then
 echo 'Not 64-bit system, exiting!'
 exit
fi
#
# First get rid of any old Flash stuff (this code taken from Ubuntu forums post):
#
apt-get remove --purge flashplugin-installer
apt-get remove --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash
apt-get remove --purge iceweasel-flashplugin mozilla-flashplugin firefox-flashplugin
apt-get remove --purge swfdec-mozilla libflashsupport nspluginwrapper iceape-flashplugin
apt-get remove --purge xulrunner-flashplugin midbrowser-flashplugin xulrunner-addons-flashplugin
rm -f ~/.mozilla/plugins/*flash*
rm -f /usr/lib/firefox-addons/plugins/*flash*
rm -f /usr/lib/firefox/plugins/*flash*
rm -f /usr/lib/iceape/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/flashplugin-alternative.so
rm -f /usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
rm -f /usr/lib/midbrowser/plugins/flashplugin-alternative.so
rm -f /usr/lib/mozilla/plugins/*flash*
rm -f /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so
rm -f /usr/lib/xulrunner/plugins/flashplugin-alternative.so
rm -f /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
#
#
# Now fetch the latest (delete any old web pages previously downloaded):
rm flashplayer10_64bit.html
wget http://labs.adobe.com/downloads/flashplayer10_64bit.html
Latest_File=$(grep "Download 64-bit Plugin for Linux" flashplayer10_64bit.html | awk -F 'href="|">' '{print $2}')
wget $Latest_File
tar -xvf libflashplayer* --directory /usr/lib/firefox-addons/plugins
# Clean up now
rm flashplayer10_64bit.html
rm libflashplayer*
```

---

### Post by phoolish on 2010-03-04
> **dcstar said:**
> Here is a script I just knocked up to fetch and install the latest 64-bit development Flash release from the Adobe site, it may be of use to some people as a root cron job to keep up to date or manually run (using sudo):


Checked code.  Seems to work. Thanks.

---


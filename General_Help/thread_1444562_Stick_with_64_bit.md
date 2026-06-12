---
title: "Stick with 64 bit?"
date: 2010-04-01
forum: General Help
---

### Post by Muskiet on 2010-04-01
My PC is a 64 bit AMD 3500 with 768 Mb DDR, on-board ATI Radeon XPress 200 and two 36 Gb SCSI 320 HD's in raid-0 with Ubuntu 9.10 64-bit for close to a month now and coming from Windows it was a difficult transition, but I'm glad I made it.
The only beef I have is with Flash, which unfortunately gets used in just about every website I look at.
Most things work with the experimental 10.0 r45, but every now and then Firefox crashes or some Flash buttons don't work (YouTube can be a pain).

For the last week I've been contemplating switching to 32 bit Ubuntu and seeing Ubuntu 10 on the horizon I figured I can wait a little to see if it is worth it to me to install the 32-bit version of the new Ubuntu in stead.
It took me a long time figuring out how to get things working and even installing my printer (for which there are only 32-bit drivers) was an adventure that cost me half a day, getting the system installed with the SCSI raid controller was more of an evolution then an adventure.
Now that I'm a bit wiser in the way of the Linux though the only thing I'm still wondering about is the difference between running my system with a 32-bit and a 64-bit OS.

Will the only difference be that Flash will actually work as intended or will my system's speed (which isn't all that powerful to begin with) be greatly affected?

Any thoughts on this are greatly appreciated.

---

### Post by oldos2er on 2010-04-01
Are you using 64-bit flash?

---

### Post by dabl on 2010-04-01
How did you install flash?

Hint: you should follow this guidance, which includes installation of flashplugin-nonfree:  [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


If flash performance is your only problem, that seems like a pretty thin rationale to reinstall a 32-bit architecture.  Chances are pretty good that something else will be a problem on the new system ....

---

### Post by NightwishFan on 2010-04-01
64-bit is epic. Stick with us!

I install flash from here and it works fine for me.
[https://launchpad.net/~brandonsnider/+archive/experimental-flash](https://launchpad.net/~brandonsnider/+archive/experimental-flash)

---

### Post by koolblue3 on 2010-04-01
Hi,

If your are not using the 64 bit flash you can try it by removing your current flash and downloading the latest 64 bit flash for Linux from this link [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html) and then extracting it into your /home/USERNAME/.mozilla/plugins/ folder.

---

### Post by mk1w86 on 2010-04-01
Flash should in theory, work fine now on 64bit, although people still have problems with flash on 32 and 64bit versions of Ubuntu.

Since you only have 768MB RAM the 32bit version should be fine on your machine, as long as no other problems crop up as other posters have said. ;)

---

### Post by bigsmitty64 on 2010-04-01
> **dabl said:**
> 

If flash performance is your only problem, that seems like a pretty thin rationale to reinstall a 32-bit architecture 
But it does stink if you are  a musician/actor or artist of any kind who is on youtube daily. He did mention youtube.

---

### Post by Muskiet on 2010-04-05
> **NightwishFan said:**
> 64-bit is epic. Stick with us!

I install flash from here and it works fine for me.
[https://launchpad.net/~brandonsnider/+archive/experimental-flash]("https://launchpad.net/%7Ebrandonsnider/+archive/experimental-flash")

You are the man!
I've tried a lot of "fixes", but this is the only one that works great!
Thank you very much... I'll be sticking with 64 bit!
And yeah... it was enough of a pain for me to consider switching.
Hulu, Youtube and even the TurboTax website had irritating issues which made them a pain to use.

---

### Post by KayakJim on 2010-04-05
> **NightwishFan said:**
> 64-bit is epic. Stick with us!

I install flash from here and it works fine for me.
[https://launchpad.net/~brandonsnider/+archive/experimental-flash](https://launchpad.net/~brandonsnider/+archive/experimental-flash)

With Jaunty I am getting a 404 error on the PPA when I do an update.

---

### Post by Agent ME on 2010-04-05
> **NightwishFan said:**
> 64-bit is epic. Stick with us!

I install flash from here and it works fine for me.
[https://launchpad.net/~brandonsnider/+archive/experimental-flash](https://launchpad.net/~brandonsnider/+archive/experimental-flash)
Works great! I kinda had wanted to upgrade to the newer 64-bit flash, but I really had wanted to find it packaged for Ubuntu in a repository instead of just manually installing it from its own website.

---

### Post by dcstar on 2010-04-06
> **Agent ME said:**
> Works great! I kinda had wanted to upgrade to the newer 64-bit flash, but I really had wanted to find it packaged for Ubuntu in a repository instead of just manually installing it from its own website.

If you save and call this script from a **root** cron job it will automatically keep your 64-bit flash updated:

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

### Post by Grenage on 2010-04-06
I always have problems with the x64 flash plugin; it's always fixed by manually downloading the latest from the Adobe site, and placing it in my plugins folder.

---

### Post by conmat on 2010-04-06
Ubuntu 9.10 64-bit, ext4
Lenovo T400


I'm a new Ubuntu user so I would like to ask for clarification.

If I use 64-bit Flash that means I have to use a 64-bit browser.  Is this correct?

I like to use SeaMonkey but Seamonkey is only 32-bit.  AFAIK I can not use 64-bit Flash with SeaMonkey.  Is this correct?

Thanks

---


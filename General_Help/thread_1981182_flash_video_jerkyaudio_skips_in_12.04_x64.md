---
title: "flash video jerky/audio skips in 12.04 x64"
date: 2012-05-16
forum: General Help
---

### Post by hamsandwich on 2012-05-16
I have searched quite a bit on this topic, tried several things, and none of them worked. After upgrading to 12.04, flash videos appear jerky and the audio skips or hesitates as well. I'm on the 64 bit version of Ubuntu and I'm using Firefox 12.

I finally was able to install an older version of flash that fixed this problem. Maybe it was already posted here and I didn't find it but I thought this might be helpful.

First, I had a hard time because I already tried various fixes leaving various versions of flash around. I would suggest removing firefox and adobe-flashplugin, and then reinstalling them to make sure you have the default setup.

Then download this flash version:
[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip)

Extract the contents. Go to the folder marked "11_1r102_63_64bit". Assuming you have the nifty nautilus-open-terminal installed, open a terminal in this folder. If not, open a terminal and navigate there. Then do the following: 

[FONT="Courier New"]sudo cp flashplayer11_1r102_63_linux.x86_64.tar.gz /
cd /
sudo tar -xzvf flashplayer11_1r102_63_linux.x86_64.tar.gz
sudo mv libflashplugin.so /usr/lib/mozilla/plugins/[/FONT]

if you don't follow that, the commands just moved the tar file to root, extracted it, and moved the resultant plugin to the right place.

Restart firefox and it should work. Worked for me. Initially I thought I could make this work by just copying the libflashplugin.so to various folders, but I think all the other support files in the tar file are needed, and need to be in the right place. That's why the tar file is extracted in the root directory. Also if you search in your /usr/lib for libflashplugin.so, you will see it in several places, but most of these are shortcuts (links) to the one in the /usr/lib/mozilla/plugins folder so the easiest step is to just copy it there.

Hope this is helpful.

---

### Post by whit on 2012-06-20
Trying to follow your recipe. It looks like the last step should instead be  

  cp libflashplayer.so /usr/lib/flashplugin-installer/

Since in /etc/alternatives there's this:

  mozilla-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so

and /usr/lib/mozilla/plugins has:

  flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

Also **it doesn't do any good anyway.** I'm sure it did on your system. But it's still broken in the same way on mine.

---

### Post by hamsandwich on 2012-06-20
> **whit said:**
> Trying to follow your recipe. It looks like the last step should instead be  

  cp libflashplayer.so /usr/lib/flashplugin-installer/

Since in /etc/alternatives there's this:

  mozilla-flashplugin -> /usr/lib/flashplugin-installer/libflashplayer.so

and /usr/lib/mozilla/plugins has:

  flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin

Also **it doesn't do any good anyway.** I'm sure it did on your system. But it's still broken in the same way on mine.

That seems right as I look at my current system. My instructions seem to have been correct (for me) for ubuntu 12.04 as it stood at the time. However I have since then had the opportunity to do clean installs of 12.04 elsewhere and do not have the same issues with jerky flash video. I have not read through any change or release notes to understand how they have changed things around but I'm pretty sure they have.

I had to install a couple of different older version to find one that works, so you might try that. And I think I uninstalled the prior flash previous to doing this. Also do move the tar file to / so that helper files get installed correctly as well. Sorry I can't be more help.

---

### Post by mrhhug on 2012-09-06
you savage!!!! can we change ```
/
``` to ```
~/
```?

---


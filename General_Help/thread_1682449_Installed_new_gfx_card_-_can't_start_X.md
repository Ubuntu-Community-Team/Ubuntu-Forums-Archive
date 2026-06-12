---
title: "Installed new gfx card - can't start X"
date: 2011-02-05
forum: General Help
---

### Post by moodog on 2011-02-05
I have a media centre running mythbuntu 10.10, with an Athlon X2 2400 in it. I've just replaced my aging nVidia GeForce 6200 with an nVidia gt430. After restarting the box with the new card in it, and an old VGA monitor plugged in X won't start properly. It fails with "Screens found but no valid configuration" or similar. I removed the old xorg.conf and tried restarting, and it will actually go into X, but when I try to run nvidia-settings, it tells me I'm not using the nVidia driver. I then tried deactivating the nvidia driver and reactivating it, then using sudo nvidia-xconfig, but when rebooting I get the same error as above. dpkg-reconfigure xserver-xorg seems to no longer do anything – i.e. if I delete xorg.conf and run this, no new xorg.conf is generated.
I'm at a bit of a loss as to how to get the new video card working properly. I'm going to put the box back together and plug it back into the flat screen tv and see if it all works.

no xorg.conf allows me into X, but without being able to configure with nvidia-settings.

running nvidia-xconfig gives me an xorg.conf, but won't allow X to start...

---

### Post by ikt on 2011-02-06
This may help:

[http://ubuntuforums.org/showpost.php?p=10324816&postcount=2](http://ubuntuforums.org/showpost.php?p=10324816&postcount=2)

Saw your post on whirlpool, you may be able to get some help joining #ubuntu-au on irc or sending a msg to the ubuntu au mailing list :)

---

### Post by moodog on 2011-02-06
Thanks for that tip - have added the new PPA, installed the lastest version (270.18 ) but still no love... will keep plugging...

---

### Post by moodog on 2011-02-07
I installed xubuntu amd64 from the alternate CD, and when it first booted up Jockey prompted me to install the "additional drivers" – which I think installed nvidia 260.<something>, and the graphics card worked straight away. I then wanted to get HDMI audio working, so added the x-swat ppa and updated again, and it all still worked.

Then had troubles getting the default audio card set (due to my own silly mistakes) and in the process removed xubuntu-desktop and added ubuntu-desktop.

Now the only (minor) issue is that for some reason it is only outputting 1080i to my 42" plasma – can't get it to do 1080p, and the audio over HDMI appears to only be stereo, and won't do 5.1. Still looking into those, but at least it's working now.

I also find that if I have "Upmix stereo to 5.1" set in mythtv's General audio settings or Music settings, it fails to output any audio when watching TV, and actually segfaults in MythMusic. Does anyone have any idea why this is?

---


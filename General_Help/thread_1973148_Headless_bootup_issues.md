---
title: "Headless bootup issues"
date: 2012-05-04
forum: General Help
---

### Post by jimminy_cricket on 2012-05-04
Hi all,

I'm not sure if this is in the right forum but I have been having issues getting 12.04 to boot.  Initially after the upgrade I had a lot of problems with unity and ended up just installing xfce as a replacement to get it working again.

I have ubuntu desktop edition installed but use it as a general file server so I need it to boot without a monitor plugged in.

I found various threads suggesting manually setting the xorg.conf file to enable it to boot with no screen plugged in.
I followed the xorg.conf laid out here: [http://exain.wordpress.com/2009/11/19/booting-ubuntu-without-monitor-plugged-in-switched-off/](http://exain.wordpress.com/2009/11/19/booting-ubuntu-without-monitor-plugged-in-switched-off/) which was copied from a thread on these forums. 

Unfortunately the fix appears to do nothing, if I boot the machine with no screen plugged in it still fails to start any sort of display manager and even if I plug in a screen at a later point it still doesn't display anything.

Does the xfce install change anything with the way the system looks at the xorg.conf file or is something else wrong here?


Any help would be appreciated, thanks!

---

### Post by jimminy_cricket on 2012-05-04
To update, i've found a load more suggestions and howto's but they are all dated 2009 so i'm a little dubious to try them.

[http://www.szewong.com/2009/06/setting-up-headless-ubuntu-with-xfce-and-vnc-slicehost/](http://www.szewong.com/2009/06/setting-up-headless-ubuntu-with-xfce-and-vnc-slicehost/)
[http://ubuntuforums.org/showthread.php?t=618965](http://ubuntuforums.org/showthread.php?t=618965)

---

### Post by QIII on 2012-05-06
Install xserver-xorg-video-dummy

That'll allow the machine to boot headless.

For remoting, I recommend Nomachine.  NX is far and away better than VNC, it's more secure since you use SSH, and the NX client will automatically resize the X session inside the client.  Almost as good as Microsoft's RDP.

---


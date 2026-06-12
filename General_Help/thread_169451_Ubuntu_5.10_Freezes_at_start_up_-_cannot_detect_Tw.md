---
title: "Ubuntu 5.10 Freezes at start up - cannot detect Twinhan 1020a DVB-S Card"
date: 2006-05-02
forum: General Help
---

### Post by winner999 on 2006-05-02
Hello,

I have a Twinhan 1020a DVB-S Card that I am trying to use with Ubuntu 5.10.

After I installed Ubuntu, it froze at the initializing hotplug subsystem step.  Removing the above twinhan card solved the problem and allowed it to boot.

But I still can't get the system to boot with the twinhan card - does anyone have this combination (twinhan 1020a + Ubuntu 5.10) working?

Please help!

---

### Post by lirender on 2006-05-02
I'm a Linux noob and eventually got some success in Gentoo with Twinhan, but no longer use it and plan to try out Dapper soon. There are issues with twinhan in many distros (need to give bttv driver params i2c_hw=1 card=0x71). Check dvbn.happysat.org's linux section. Here is a post from the vdr-live distro: [http://dvbn.happysat.org/viewtopic.php?p=179166&highlight=modprobe+dst#179166](http://dvbn.happysat.org/viewtopic.php?p=179166&highlight=modprobe+dst#179166) 

Stynker wrote: 
I am using an old 1020 twinahan. 
How would I go about adding parameters to the bttv module? 
IE 
modprobe bttv i2c_hw=1 card=0x71 

She locks up on boot. I tried this cd on a couple boxes. 


1. Remove the twinhan from the computer. 
2. Install vdr-live to hd. Follow above directions. To use the working kernel on live cd once you install to hd you will need to recompile the kernel from the /usr/src/linux dir. 
3. You add this here: 
nano -w /etc/modprobe.d/blacklist 
(at the very bottom) 

# DVB Modules 
blacklist dvb-ttpci 
blacklist bttv 
blacklist bt878 
4. Put twinhan back in and reboot

Also [http://www.mysettopbox.tv/phpBB2/viewtopic.php?p=20716&sid=c283fe13b3e012a40e7a72e4847e0cb1](http://www.mysettopbox.tv/phpBB2/viewtopic.php?p=20716&sid=c283fe13b3e012a40e7a72e4847e0cb1) 

Good luck

---


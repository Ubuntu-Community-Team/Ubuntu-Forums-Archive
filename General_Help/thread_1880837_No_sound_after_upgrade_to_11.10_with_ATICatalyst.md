---
title: "No sound after upgrade to 11.10 with ATI/Catalyst"
date: 2011-11-14
forum: General Help
---

### Post by deragun on 2011-11-14
Hello, I've spent a few days searching around on these (and other) forums for solutions to my issue and nothing has completely worked.

My issue is that after upgrading from 11.04 to 11.10 I've (almost) completely lost sound.  

I have an ATI HD 4200 video card on my HTPC.  It's connected to my TV via HDMI.

I have tried uninstalling / reinstalling the catalyst drivers.  On 11.04 I did a manual install of the driver from ATI's driver website.  After uninstalling, I've reinstalled via Jockey.

The first oddity is that I can install the main driver fine, but Jockey fails to install the "post-release updates" every time.  Not sure if I really need them, but either way, it won't install.

I've also checked for any muted channels, etc, on alsamixer.  Everything looks fine to me there.

However, when I try to play any video with VLC or XMBC, or play a youtube clip in Chromium, or play a song in the default player, etc, there is no sound coming through.

The other very odd part of this (which I've not seen mentioned anywhere) is that if I go to the sound settings Hardware tab and do "test speakers", I can hear the "left speaker"/"right speaker" clips perfectly fine through the TV.  So the hardware is obviously seen and configured correctly for sounds to play, but it just doesn't actually work with anything besides a hardware test.

Does anyone have any ideas or suggestions?  I really don't want to have to wipe and do a fresh install to fix this...

---

### Post by deragun on 2011-11-18
Trying 1 bump to see if anyone can help me before I do a wipe and reinstall this weekend.

Thanks in advance for any help.

---

### Post by jodiaq on 2011-11-18
Try this
> [http://give-a-try.blogspot.com/2011/10/unable-to-get-ubuntu-1110-login_26.html](http://give-a-try.blogspot.com/2011/10/unable-to-get-ubuntu-1110-login_26.html)

---

### Post by deragun on 2011-11-22
Problem solved.  Just in case this helps anyone else with a similar issue, this is what worked for me:

puvacontrol

I tried running this command, and found that it wasn't installed.  Not sure if it was installed under 11.04 and was removed in moving to 11.10 or not.  Either way, after I installed it I was able to run this.

Previously alsamixer, audio control on desktop, etc all showed every channel as on, unmuted, and at full volume.

However, after running this command and taking a quick look at the settings in the puvacontrol utility, I noticed that the "Master Volume" was down to 0.  It wasn't muted, just at 0%.  Changed it to 100% and viola.  Sound works perfectly.

---


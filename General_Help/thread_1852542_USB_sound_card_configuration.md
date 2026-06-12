---
title: "USB sound card configuration"
date: 2011-09-30
forum: General Help
---

### Post by Bradburts on 2011-09-30
I am trying to get mpd to work under ubuntu server 10.04. The server is running in VirtualBox 4.2.1. This may seem and may indeed be silly but I wanted to get the install straight before I mess my server up.
I plugged my USB sound dongle in and boot.
I have a sound device but not where I expect it:
 
cat /dev/snd/by-id
gives:
usb-0d8c_C-Media_USB_Headphone_Set-00
 
I install mpd and left with standard configuration.
Also in /dev is a file sndstat which contains text along the lines of:
'...C-Media ALSA emulation but Audio device not enabled in config.' (or something like that)
I added an internet radio:
 
mpc add [http://relay3.slayradio.org:8000/](http://relay3.slayradio.org:8000/)
mpc play
mpc volume 100
 
I can see that tracks are 'playin' as duration counters increase. I don't get any sound though.
Thinking that I may need usb 2.0 I installed the Virtual Box extension pack.
Unfortunately this resulted in the device /dev/snd disappearing. The file /dev/sndstat is now red & if I cat /dev/sndstat I get 'file or directory not found.' What does red mean?
I have since noted that boot.log has a fail under starting open sound system. It may have been failing on first configuration as well.
 
I uninstalled VirtualBox extensions but cannot recover the original discovered device.
 
I would appreciate pointer on how to diagnose & configure sound drivers or indeed general driver level debug. The error messages I have are not detailed enough.
I cannot see any reason why I should not be able to get a usb sound card to work through VirtualBox and although the configuration may be weird its a good learning environment!
I seem to have upset VirtualBox now and any help reseting would help.

---

### Post by Bradburts on 2011-09-30
Had some success, sort off.
Think I just needed to run alsamixer, unmute and crash VB.
The cards were present all along but I had not sudo the commands, e.g. 
aplay -l
no soundcards ...
sudo aplay -l
showed two cards
 
 
sudo aplay -D plughw:1,0 /usr/share/sounds/alsa/Front_Center.wav
reported that it was playin, no sound & VB hung.
Rebooted again and for some reason I now have /dev/dsp.
Sound is working!
 
sudo aplay -l
shows one card
 
Could not repeat the 'working' configuration using my clone's base.
On restarting the 'working' VM I am without sound again.
 
I am stuck. Also get format errors from mpd. 
Surely getting sound going is easier than this?

---

### Post by Bradburts on 2011-10-03
Working now.
 
Misunderstood what the tick in VB Devies->USB does.
When ticked the 'C Media..' device shows but this device cannot be made to work.
The Intel Card, available when VB Device not ticked, plays sounds ok.
Also the card sometimes adjusts my PC system volume which also mutes.
 
Still have problems mixing but will raise a fresh query.

---


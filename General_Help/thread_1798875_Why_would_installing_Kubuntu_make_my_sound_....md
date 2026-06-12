---
title: "Why would installing Kubuntu make my sound ..."
date: 2011-07-06
forum: General Help
---

### Post by xj0hnx on 2011-07-06
...disappear? everything was working perfectly with Ubuntu Classic, and I decided to try out Kubuntu, installed through the Ubuntu software manager, along with the restricted packages, and as soon as a booted into Kubuntu my sound was gone. Nothing I have done is able to bring it back, and it's gone in all desktop environments, not just Kubuntu. I tried a few methods in the sound thread on these forums, I'll try to find, and link it.

On that note I tried to uninstall Kubuntu following [these](http://www.psychocats.net/ubuntu/puregnome) instructions, and it will not uninstall, even though the terminal tells me that it was successfully uninstalled, I can still boot into it, and all applications are still showing in both windows environments.

This install is Ubuntu 11.04 64-bit, installed alongside Windows 7 (in which sound still works, so it's not hardware) using Wubi. Creative X-Fi sound card, optical cable out to a receiver and then to 5 speakers, LF, RF, C, LR, LL.

---

### Post by enimeizoo on 2011-07-06
On my computer too kubuntu did weird things, like putting my HDMI output as the default output (master chanel). Do you have a sound icon in your system tray?
If so, you should be able to click it and the click mixer. It will display a window with various volumes.  Make sure that all volumes you want are unmute.
Then, if it still doesn't work, you can go in "settings -> Select master chanel", and choose the right one. (if you don't know, feel free to try them all)

Also, I'm not sure it was the best way, but uninstalling pulseaudio solved some problems.

*I just saw you 'uninstalled' it, but the instructions are for kde, not sure the menus are the same with others managers.

---

### Post by xj0hnx on 2011-07-07
> **enimeizoo said:**
> On my computer too kubuntu did weird things, like putting my HDMI output as the default output (master chanel). Do you have a sound icon in your system tray?
If so, you should be able to click it and the click mixer. It will display a window with various volumes.  Make sure that all volumes you want are unmute.
Then, if it still doesn't work, you can go in "settings -> Select master chanel", and choose the right one. (if you don't know, feel free to try them all)

Also, I'm not sure it was the best way, but uninstalling pulseaudio solved some problems.

*I just saw you 'uninstalled' it, but the instructions are for kde, not sure the menus are the same with others managers.

I've tried all available hardware options in the settings, nothing. The sound icon is there, and showing that volume is 100%, my sound card is selected, and nothing is muted.

---

### Post by enimeizoo on 2011-07-07
Did you try to uninstall pulseaudio, just in case?

By the way, it must be some config modified by kde when installed. It is obviously something shared by all desktop environments. You could also try to create a new user and see if you have sound when logged in as this user. This is to try to locate the config file.

---

### Post by SeijiSensei on 2011-07-07
Check System Settings > Multimedia > Phonon and see which audio output device has priority for playback.

---

### Post by xj0hnx on 2011-07-07
> **enimeizoo said:**
> Did you try to uninstall pulseaudio, just in case?

By the way, it must be some config modified by kde when installed. It is obviously something shared by all desktop environments. You could also try to create a new user and see if you have sound when logged in as this user. This is to try to locate the config file.

I checked in the software manager, and everything from PulseAudio asked if I wanted to install it, so I went the opposite way, and nothing changed. I did notice that when I log into Kubuntu I get a message saying that it is falling back on my preferred sound device Creative X-Fi. For some reason it is choosing HD48x0 audio Digital Stereo (HDMI) as the first device every login, even though I don't have HDMI.

> **SeijiSensei said:**
> Check System Settings > Multimedia > Phonon and see which audio output device has priority for playback.

My soundcard is set to priority, except on boot up for some reason it defaults to the one above, but then switches to my card. Everytime I close System Setting > Multimedia > Phonon it goes back to the HD48x0 audio

---

### Post by SeijiSensei on 2011-07-07
That's a [known bug in 11.04]("https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274"), and one of the many reasons why I'm still running 10.10.

---

### Post by xj0hnx on 2011-07-09
> **SeijiSensei said:**
> That's a [known bug in 11.04]("https://bugs.launchpad.net/ubuntu/+source/phonon/+bug/769274"), and one of the many reasons why I'm still running 10.10.

Interesting, but shouldn't uninstalling Kubuntu sort it out? And what would be the best way to go about uninstalling Kubuntu on a Wubi install? I tried the methodon the site I linked to earlier, and it didn't appear to do ...anything.

---


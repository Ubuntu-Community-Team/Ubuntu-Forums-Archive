---
title: "alsamixer startup &quot;speaker&quot; level (and screen brightness startup level)"
date: 2010-05-23
forum: General Help
---

### Post by balta on 2010-05-23
Hi everyone!
 so, I just upgraded to the 10.04 and everything works just fine as before (except for skype but that really doesn't matters as it has already been 3 years I'm using ubuntu and I managed to get it to work only once, for miracle I believe ^^).
The only real issue I have is this:
when I start up my laptop, after the log-in, no sound will be heared as the "speaker" volume level in alsamixer is set to 0; if I raise it from the terminal running alsamixer (as I don't know any other alternative) everything plays just fine, but the next time I boot I do have to do it all over again...
So, how can I change the default startup level of the "speaker" in alsamixer? 

thanks for the help! I know it is not such an important problem but it is very annoying ...

PS: by the way I do have the very same issue with the screen luminosity but the other way round as is always starts at maximum brightness and I can't manage to get it to start at the minimum, as it did before. At least reducing the backlight if far more quick but a couple of times I forget it and the battery lasted something like half an hour :(
If you can tell me how to fix also this one, well, you're just great! :D

thanks!


EDIT: solution [here]("http://ubuntuforums.org/showthread.php?t=1491459&p=9596364")

EDIT: thanks to T_038 you can find a **really faster solution** [here]("http://ubuntuforums.org/showthread.php?t=1491459&p=9622856")! Kudos

---

### Post by kerry_s on 2010-05-23
are you using gnome?

---

### Post by balta on 2010-05-23
> **kerry_s said:**
> are you using gnome?

yes sir!

---

### Post by Zemblan on 2010-05-23
Try, after having set your alsamixer levels: "sudo alsactl store". This should store your mixer settings and have them restored when you reboot.
Your skype problems might have to do with mixer settings too, make sure that the right mic is selected in the gnome volume settings control, you should be able to see if it's working when you speak into the mic on the level indicator, also uncheck the box which says "allow skype to change mixer settings" in the skype sound devices dialogue, it tends to mess things up.

---

### Post by balta on 2010-05-23
thanks, hope in my next reboot everything will be fine!
sadly my mic can't hear me but well it's not such a great deal as i still have windows really just for skype, hope however i'll fix it ... sooner or later
(or maybe the nice guys at skype could make a nice new version as we poor linux users still have the ver 2 and on windows they released the 4 looooooong time ago :( )
thanks for the help!

---

### Post by balta on 2010-05-24
sadly ```
sudo alsactl store
``` didn't store the speaker level and still when I boot all is silent ...
... any more clues?

---

### Post by Alaric on 2010-05-30
Hey, actually this affects me too.  Everytime I restart the dang thing is back down to 0 volume.  "sudo alsactl store" also failed here.  I tried that a while back.  I would be very interested if anyone could offer up a solution.  

A bit more information, this is a regression as it did not happen back in 9.04.  Not sure if it started with the Lucid Beta, or 9.10, but I believe it was the upgrade to Karmic that introduced this bug.  Headphones play fine, but the speakers have *no* volume.  Oddly, this doesn't happen if I don't log in and play music (via a terminal), so I'd suspect it's a problem with gnome.

---

### Post by Jotomicron on 2010-06-15
This is an issue to me too.

I had used 9.10 since it came out, but the problem started with (or after, I'm not exactly sure about the first time it happen) the upgrade to Lucid. It seems that the setting for the master volume is stored between sessions, but the Speaker is always at 0.

Because I'm not sure if it was the upgrade itself that triggered the problem, I have a theory (totally unattested and speculative). The first time I plugged the headphones, somehow the system understood that I wanted to mute Speakers. But that change was erroneously made permanent...

---

### Post by balta on 2010-07-15
Hi there!
Lately I've been playing around with alsamixer's config file

```
/var/lib/alsa/asound.state
```

but I didn't manage nor to properly understand it's meaning neither to usefully modify it...

I'll post it's content ... maybe someone can teach me how to correctly modify the file ... if it can be useful 

```
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 57
		value.1 57
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 false
		value.1 false
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		value.0 false
		value.1 false
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Front Mic Playback Volume'
		value.0 24
		value.1 24
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Front Mic Playback Switch'
		value.0 false
		value.1 false
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 3'
		comment.dbmin 0
		comment.dbmax 3000
		iface MIXER
		name 'Front Mic Boost'
		value.0 3
		value.1 3
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Capture Switch'
		value.0 true
		value.1 true
	}
	control.9 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -1650
		comment.dbmax 3000
		iface MIXER
		name 'Capture Volume'
		value.0 0
		value.1 31
	}
	control.10 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 31'
		comment.dbmin -3450
		comment.dbmax 1200
		iface MIXER
		name 'Beep Playback Volume'
		value.0 0
		value.1 0
	}
	control.11 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Beep Playback Switch'
		value.0 false
		value.1 false
	}
	control.12 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -6400
		comment.dbmax 0
		iface MIXER
		name 'Master Playback Volume'
		value 52
	}
	control.13 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Master Playback Switch'
		value false
	}
	control.14 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 255'
		comment.tlv '0000000100000008ffffec1400000014'
		comment.dbmin -5100
		comment.dbmax 0
		iface MIXER
		name 'PCM Playback Volume'
		value.0 254
		value.1 254
	}
	control.15 {
		comment.access 'read write user'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 120'
		comment.tlv '0000000100000008fffff44800000032'
		comment.dbmin -3000
		comment.dbmax 3000
		iface MIXER
		name 'Digital Capture Volume'
		value.0 60
		value.1 60
	}
}

```

Hope it can lead us to a solution!:D

EDIT:
Ok, I've been fooling around and I can tell that configurations are correctly stored with ```
alsact store
``` and loaded with ```
alsactl restore
```, which I imagine is called during the boot as I can clearly hear the TR-TR-TR (lol) drum sound on the login screen, it seems that something after the log in modifies it (as I don't hear the desktop landing medley).
I don't think the problem can be headphone related as unplugging the headphones should restore speakers volume as permanently as it was muted.
Can maybe it be a conflict with pulse?
I'll keep on trying! Please post any ideas or clues you may have. Thanks!

EDIT:
Btw, I fixed my mic problem, I just muted it's volume left component as my mic is mono and pretending it was stereo caused it no to work ... odd but functional, now I can finally fully use Skype ;)

---

### Post by balta on 2010-07-16
Ok guys, sorry for the double post but it seems that I somehow managed to solve this.
Apparently is was a conflict between alsa and pulse.
What I did was:
- install "PulseAudio Device Chooser" (which cames with a bunch of other programs) from the Ubuntu repositories.
- reboot, everything silent as before.
- before messing with alsamixer start the program.
- left click on the traycon >> volume control >> output devices tab
- from the drop down I choose "Analog speakers" (before it was analog output).
- close.
- reboot, speakers are now on, and also aslamixer confirms that.

I think that the program is just a nice GUI and in theory the trick could be done without the "pulse suit" and only using the terminal in a faster way ... well I don't care, this method I found is quite fast and you can set also your mic levels once you are there :P  

Hope this sort of "guide" can help you ;)

... Now for the brightness ... well that's another story :D

---

### Post by T_038 on 2010-07-22
try leftclick on traycon with the speaker > sound preferences > output > change connector dropdown from analog output to analog speakers. This got the same result, without installing any program.

---

### Post by balta on 2010-07-22
Too bad that's a bit too late :P
Well I hope this will be helpful at least for those who will have the same issue as mine!

---

### Post by T_038 on 2010-07-22
maybe change the link in the TS  to the solution to my post, i think my way to fix is easier then yours ;)

---

### Post by balta on 2010-07-22
> **T_038 said:**
> maybe change the link in the TS  to the solution to my post, i think my way to fix is easier then yours ;)

Done it! Thanks!
Hope it simplifies someone's life ;)

---

### Post by T_038 on 2010-07-31
i actually think it does :)

---

### Post by Alaric on 2010-08-17
Hey guys,

I just found your thread on Google.  This quick fix seems to work, but it looks like it's just a workaround.  However, my guess is that this is at best a work around, as opposed to an actual fix.  I tried this today and it appears to work well enough at having sound enabled on Ubuntu's bootup, but I can't help but notice that if you switch the device back to analog output, than the problem still occurs.  I'm guessing that we're simply disabling the feature that grants gnome the ability to manage the speaker volume on Log in.  

TL;DR In conclusion, to my fellow Googlers, this workaround works satisfactorily, but the bug still exists in your system.

---


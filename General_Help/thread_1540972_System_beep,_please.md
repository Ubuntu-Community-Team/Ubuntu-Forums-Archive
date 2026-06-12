---
title: "System beep, please"
date: 2010-07-28
forum: General Help
---

### Post by Man_Beach on 2010-07-28
I don't want much - just a short beep from the computer speaker when I get mail in Thunderbird.

I don't want a fancy noise to play from my loudspeakers - they're only turned on when I want to listen to something, and that's a rare occurrence.

I just want a simple system beep.

What's so wrong with that?

---

### Post by quixote on 2010-07-30
In Thunderbird Preferences > General, you can tick the box for "Default system sound for new mail."  Then, presumably, if in System > Preferences > Sound you have an alert sound selected and the alerts unmuted, it'll play that sound.  

If it doesn't, the actual sound files are in /usr/share/sounds and you can just choose one you like.  The basic gnome alert sounds, for instance, as in /usr/share/sounds/gnome/default/alerts.  In Thunderbird, you could enter the path to that sound under "Use following sound file".  Eg /usr/share/sounds/gnome/default/alerts/drip.wav or /usr/share/sounds/ubuntu/stereo/message-new-instant.ogg

---

### Post by 3rdalbum on 2010-07-31
I'm not familiar with Thunderbird, but it might support running a shell command when you get new mail. Set the command to "beep", and install the "beep" package from the repositories.

---

### Post by Man_Beach on 2010-08-11
The computer speaker has been disabled in Lucid. End of story. All the people who don't like the noise that their computer makes seem to have won the argument.

I'd prefer the option to have it on if I want. _Then_ Thunderbird would beep for me.

---

### Post by quixote on 2010-08-11
I hadn't heard of computer speakers being off in Lucid.  Are you sure it's not that sound isn't working on your system?  A lot of people have had trouble with it under Lucid. 

Have you tried putting in the path to a sound file in Thunderbird itself?  Does that also not do anything?

---

### Post by d.vanheeckeren on 2010-09-16
> **quixote said:**
> I hadn't heard of computer speakers being off in Lucid.  Are you sure it's not that sound isn't working on your system?  A lot of people have had trouble with it under Lucid. 

Have you tried putting in the path to a sound file in Thunderbird itself?  Does that also not do anything?

You guys aren't getting what he's saying.  He doesn't want to use a sound system.  He doesn't want to play sound files.  You know that one little beep you hear immediately after you press the power button to turn your computer on?  THAT'S what we're looking for, nothing special.  Just a beep.  Like the old days.

[EDIT]
Just found something in another thread....  it seems if you install the beep module (sudo apt-get install beep) you can then run (modprobe pcspkr) and then the beep command (beep) after it and it works great.  I have ubuntu 10.04 on two different servers and just tried it on both, and it works.  However, you must run the modprobe command at least once before using beep and it doesn't carry across reboots.  Once you reboot you'd have to issue the modprobe again to enable beep.  I'm a novice linux user, but maybe this will give you some direction and help you find a way to make it permanent.  *shrug*

---


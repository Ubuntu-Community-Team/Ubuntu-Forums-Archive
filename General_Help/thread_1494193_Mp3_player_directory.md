---
title: "Mp3 player directory??"
date: 2010-05-26
forum: General Help
---

### Post by mountainmanmark on 2010-05-26
I know this is probably an extremely easy question... but does anyone know how to browse the files of an mp3 player in ubuntu 10.04? when i insert it it shows up in rhythmbox, but i'm unable to browse the files manually... i also looked under media and it isn't showing up. any ideas?

---

### Post by TheStroj on 2010-05-26
You can try opening it in menu. Go to Places - computer and search your device. It can also be only in Places, since some devices when mounted show up under Computer icon.

---

### Post by Robertjm on 2010-05-26
Under Places go to COMPUTER
Do you see your mp3 player there?
If so, right click on it and select MOUNT
Once it's mounted you should see its name appear on the left side, with the "eject" icon to the immediate left. 

Once mounted you should be able to double click on it and browse as normal.

You didn't mention which type of mp3 player you're using. I'm assuming it's an MTP player? Make sure it's not connected within your audio player (Amarok, Pana, Rythmbox etc) when you go to mount it.

I had a problem which sounds different than yours, but I'll toss it out anyways. I couldn't get into my Sony Walkman at all from within Pana 1.4 (fork of Amarok). Turns out it was an issue with HAL, or an actual lack of it since it was dropped in 10.04. In desperation I looked through all references to HAL in Synaptic and found a program called QLIX. Making a long story short, I ran QLIX, which detected the device. Next time I ran Pana I was able to detect my Walkman just fine.

Also, I ran a program called MountManager to deal with some CD mounting problems. Again, something that may not resolve your issue, but wanted to throw it out there anyways.

Good luck!!

Robert
Robert

---


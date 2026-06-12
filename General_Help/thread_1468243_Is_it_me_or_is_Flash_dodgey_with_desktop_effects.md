---
title: "Is it me or is Flash dodgey with desktop effects?"
date: 2010-05-01
forum: General Help
---

### Post by ELD on 2010-05-01
Am i the only one who has problems with Flash when desktop effects are enabled?

Say for example i tried viewing a video hosted by megavideo and with desktop effects enable i click the red play button in the middle and nothing happens, when desktop effects are off it seems to work fine though?

---

### Post by dino99 on 2010-05-01
> **ELD said:**
> Am i the only one who has problems with Flash when desktop effects are enabled?

Say for example i tried viewing a video hosted by megavideo and with desktop effects enable i click the red play button in the middle and nothing happens, when desktop effects are off it seems to work fine though?

Maybe Steve Jobs have the good answer  :lolflag:

hope we will see html5 soon in place of that crap

---

### Post by ELD on 2010-05-01
Well i am looking for help on getting it a bit more stable. HTML5 will take a long time, i am looking for a solution other than turning off effects.

---

### Post by wickedlester on 2010-05-01
I have not realized before, but same thing here. When effects are turned off the buttons work fine, when on they do not respond.

---

### Post by The Flying Penguin on 2010-05-01
I just went to megavideo and sure enough I can't play with video with desktop effects enabled but disabling it allows the video to play. Good thing I never watch megavideo.com.

---

### Post by dino99 on 2010-05-01
file a bug guys :P

---

### Post by wickedlester on 2010-05-01
I don't think it is just megavideo. You can watch videos @ youtube but can't use pause button or move the tracker, etc.

---

### Post by ELD on 2010-05-01
> **wickedlester said:**
> I don't think it is just megavideo. You can watch videos @ youtube but can't use pause button or move the tracker, etc.

Youtube works some of the time with effects enabled, but half the time videos won't play.

I have had to turn off desktop effects to use Flash properly.

---

### Post by ELD on 2010-05-09
An update after more testing with effects off.

With a flash video on one tab and switching between that tab and browsing in another tab the flash content stops and the whole block turns grey.

---

### Post by spoon_ on 2010-05-09
You guys are using 64-bit lucid, right?

---

### Post by ELD on 2010-05-09
> **spoon_ said:**
> You guys are using 64-bit lucid, right?

I am indeed.

---

### Post by spoon_ on 2010-05-09
> **ELD said:**
> I am indeed.

I found that this problem went away for me when I installed the native 64-bit flash player from adobe: [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

By default, ubuntu uses a 32-bit player with a wrapper library that's supposed to make it work on 64-bit systems (the nspluginwrapper package). It doesn't work that well.

You should uninstall nspluginwrapper and flashplugin-nonfree packages, and download the native player from the link above. Put libflashplugin.so in /usr/lib/mozilla/plugins/

---

### Post by ELD on 2010-05-09
I didn't install using those methods, i used the software centres "Adobe Flash Plug-in", is it still the same case of a 32bit download from that method?

Edit > I did a search and "nspluginwrapper" is installed, so logic tells me i do have the 32bit version, how annoying.

I guess this will change when adobe officially releases the 64bit plugin right?

---

### Post by spoon_ on 2010-05-09
Yeah when I said "by default" I meant "when you install it from the repositories". So it's still 32-bit. You should also remove flashplugin-installer, if it's installed.

Edit: Yeah, I assume canonical considers the 32-bit "final" version more stable than the 64-bit beta.

---

### Post by ELD on 2010-05-09
Well i've popped the 64bit download you linked me to into the plugins folder, will update this thread if i have any other issues or if i have none at all i will let people know how well it works ;)

I see it was updated this year too, so at least adobe are working on it :)

---


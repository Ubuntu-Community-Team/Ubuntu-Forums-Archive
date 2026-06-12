---
title: "no mail notification sound after thunderbird update"
date: 2012-05-07
forum: General Help
---

### Post by decrepit on 2012-05-07
Ubuntu 10.04.
Think it was the last thunderbird update that killed my mail notification sound.

The sound is still where thunderbird thinks it is, the browse button in edit-prferences-general points to the correct file, pressing the play button does nothing, but any other player can play it.

libaudiofile0 libesd0 esound-common are still installed.

---

### Post by seatopia on 2012-05-09
I have the same problem (also with 10.04).  I hope someone knows of a solution...

---

### Post by decrepit on 2012-05-13
So only 2 of us with this problem?
Can anybody help?

---

### Post by marstehr on 2012-05-13
[SIZE=2]> **decrepit said:**
> So only 2 of us with this problem?
Can anybody help?

There are more of us here and there...[/SIZE] [SIZE=2]
[/SIZE]                                   [FONT=Liberation Serif, serif][SIZE=2]**Linux Mint:**[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2][[FONT=Liberation Serif, serif]Thunderbird Notify Sound Gone[/FONT]]("http://forums.linuxmint.com/viewtopic.php?f=47&t=101707&start=0&hilit=thunderbird+sound")[/SIZE][/FONT]
 [FONT=Arial, sans-serif][SIZE=2][[FONT=Liberation Serif, serif]http://forums.linuxmint.com/viewtopic.php?f=47&t=101707&start=0&hilit=thunderbird+sound[/FONT]]("http://forums.linuxmint.com/viewtopic.php?f=47&t=101707&start=0&hilit=thunderbird+sound")[/SIZE][/FONT]
  [FONT=Liberation Serif, serif][SIZE=2]**Puppy Linux Discussion Forum:**[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=2]**No sound notification in Thunderbird**[/SIZE][/FONT]
 [FONT=Comic Sans MS, cursive][SIZE=2]**[[FONT=Liberation Serif, serif]http://www.murga-linux.com/puppy/viewtopic.php?t=69488&sid=c5cfcf7dc9329b829558785228c5dbed[/FONT]]("http://www.murga-linux.com/puppy/viewtopic.php?t=69488&sid=c5cfcf7dc9329b829558785228c5dbed")**[/SIZE][/FONT]
**Bodhi Linux:**
[http://forums.bodhilinux.com/index.php?/topic/5060-thunderbird-stopped-playing-sound-when-new-messages-arrive/page__p__46926__hl__tianlan__fromsearch__1#entry46926](http://forums.bodhilinux.com/index.php?/topic/5060-thunderbird-stopped-playing-sound-when-new-messages-arrive/page__p__46926__hl__tianlan__fromsearch__1#entry46926)
 [FONT=Liberation Serif, serif][SIZE=2][B]
Sometimes installing these helps: 
[/B][/SIZE][/FONT][FONT=Liberation Serif, serif][SIZE=2]esound/ESD daemon: gstreamer0.10-esd , which is a GStreamer plugin for ESD.[/SIZE][/FONT]

[FONT=Liberation Serif, serif][SIZE=2]However, it did not work for me and like you, I am still waiting for help.[/SIZE][/FONT]
[SIZE=2]

[/SIZE] 
  [SIZE=2]
[/SIZE]

---

### Post by decrepit on 2012-05-14
Thanks marstehr, don't feel so lonely now.

I tried installing esound, but package manager says I have to unistall ubuntu desktop first????

Installed gstreamer0.10-esd ok, but notification sound still not working

---

### Post by marstehr on 2012-05-19
When I joined this topic the sound did not work. Now  it does. I followed the instructions from this link and dared to try the  new: 
[http://www.omgubuntu.co.uk/2012/03/instant-messaging-comes-to-thunderbird-13-speed-dial-to-firefox-13/](http://www.omgubuntu.co.uk/2012/03/instant-messaging-comes-to-thunderbird-13-speed-dial-to-firefox-13/)

It works marvelous in BodhiLinux and I did not find any bugs yet, but should I, then I'll be happy to report them. 

For me the problem is solved. I like to thank all for their  contributions. 

With best wishes for the development and building of a better Internet, 

:guitar:
TianLan

---

### Post by decrepit on 2012-07-27
Well it's working now, sound came back as mysteriously as it went, guess it's just an update thing.

---


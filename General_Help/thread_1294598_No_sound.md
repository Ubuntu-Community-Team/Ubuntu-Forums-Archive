---
title: "No sound"
date: 2009-10-18
forum: General Help
---

### Post by brandon19 on 2009-10-18
I have ubuntu Jaunty and i have no sound. please help!

---

### Post by PorkyPie on 2009-10-18
Could you please provide some more info, like

[LIST=1]
[*]Your system specs
[*]What sound card?
[*]Have you tried Sound Properties?
[/LIST]

---

### Post by brandon19 on 2009-10-18
i have ADM Turion X2 Dual Core Mobile RM 72 Processor
 GNOME 2.26.1
Where can i go to find out what sound card i have. Sorry i am very new to all of this

---

### Post by PorkyPie on 2009-10-18
Thanks :)

At the top right corner of your screen, (where the notification area is) do you see an icon that looks like a loudspeaker? if so, right click it and select "Open Volume Control" At the top of the window that comes up, you should se your sound card.


If you see that the volume is down, put it up. Click on where I showed you the sound card would be and click all the options, and put the volume up on everything. Now, your sound should work. Hope it helps :)

---

### Post by brandon19 on 2009-10-18
> **PorkyPie said:**
> Thanks :)

At the top right corner of your screen, (where the notification area is) do you see an icon that looks like a loudspeaker? if so, right click it and select "Open Volume Control" At the top of the window that comes up, you should se your sound card.


If you see that the volume is down, put it up. Click on where I showed you the sound card would be and click all the options, and put the volume up on everything. Now, your sound should work. Hope it helps :)

I turned everything up and my sound still does not work. And my sound card is HDA ATI SB

---

### Post by PorkyPie on 2009-10-18
> **brandon19 said:**
> I turned everything up and my sound still does not work. And my sound card is HDA ATI SB

have you updated ubuntu? you should try it and see.

---

### Post by Random-penguin on 2009-10-18
Hi, try using the terminal and type the following:

uname -a

this will tell us the kernel version and the processor type.

then type:

cat /proc/asound/cards

this will tell us the soundcards you have installed.

Post the results as this will give us more specific info to help you.

---

### Post by brandon19 on 2009-10-18
yes still no sound

---

### Post by brandon19 on 2009-10-18
Linux brandon-laptop 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux
brandon@brandon-laptop:~$ cat/proc/asound/cards
bash: cat/proc/asound/cards: No such file or directory
brandon@brandon-laptop:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd2500000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xd2410000 irq 19

---

### Post by Random-penguin on 2009-10-18
Try typing the following into the Terminal:

find /lib/modules/`uname -r` | grep snd

A long list of sound modules should appear. If not these need to be installed using:

sudo aptitude install linux-restricted-modules-`uname -r` linux-generic

This will install the modules, then reboot and see if sound works.

---

### Post by brandon19 on 2009-10-18
still no sound guys

---

### Post by Random-penguin on 2009-10-18
Ok, I'll admit I am running out of ideas...... We could check to see what your motherboard recognizes as installed.

lspci -v | less

Look through the listing for "Audio Device". If you can't find your audio device you will need to go into the BIOS to enable it. Reboot and follow the onscreen instructions to do this (it varies between Motherboard, but is something like press ESC). Look for onboard audio and enable it.

---

### Post by Random-penguin on 2009-10-18
If it does detect your audio device cut and paste that section. Perhaps your soundcard is not supported.....

---

### Post by brandon19 on 2009-10-18
i went into my bios and couldnt find anything to do with audio. Any other ideas?

---

### Post by Random-penguin on 2009-10-18
Are you saying that "Audio Device" did not show in the list produced by "lspci -v | less".
If that is so then it does point to a hardware problem with the motherboard. There probably isn't a separate "Audio" section within your BIOS but it will be there somewhere within the menu system. I suggest another good look if that is the case!

---

### Post by brandon19 on 2009-10-18
My audio worked fine until i installed Ubuntu so its unlikely that its a hardware problem. Ill give it another look in my bios and i didnt find anything for audio

---

### Post by brandon19 on 2009-10-18
I went into the bios a third time and found the audio option. It was enabled so thats all good but my sound still will not work.

---

### Post by Random-penguin on 2009-10-18
Out of interest, did you get sound from the "live" install disc? It might be worth popping that in and seeing if you do... Also have you had sound working with other flavours of Linux or is this your first dip into Linux?

---

### Post by brandon19 on 2009-10-18
i havent had sound anywhere else in linux

---

### Post by Random-penguin on 2009-10-18
In that case, unfortunately it may be  that your soundcard is not yet supported by Linux.... I am not saying this is definitely the case but it might be worth doing some research with ALSA (looking for your model of soundcard and if it's not supported putting in a request).

I am sorry I cannot help further.... maybe I'm missing something and others can help on the forum. Good luck and if I think of anything else, I'll let you know!

---

### Post by Random-penguin on 2009-10-18
I've not read this thread through but these might prove helpful:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

Regards

---


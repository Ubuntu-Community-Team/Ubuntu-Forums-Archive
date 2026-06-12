---
title: "(solved)HOWTO: FIxing crackling/scratching/poping noise on HDA ausio cards 9.10"
date: 2009-11-23
forum: General Help
---

### Post by linuxgeek77 on 2009-11-23
hello there guys i found out how to fix the crackling noise you get with pulse audio on HDA cards its not that hard really. all you have to do is disable/ remove the new power-save option in the new audio drivers. here is what to do:

open the terminal and type:

```
sudo gedit /etc/modprobe.d/alsa-base.conf 
```
then type your password


and then the last two lines where you see power-save option, just delete it. and save it.

```
Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```
IF THAT DOES NOT WORK TRY MY NEW SOLUTION HERE: [http://ubuntuforums.org/showthread.php?p=8789064#post8789064](http://ubuntuforums.org/showthread.php?p=8789064#post8789064)

I hope i helped someone out there with my post :) please comment back and let me know if it works for you. 
this was tested on HP dv6636nr laptop with HDA NVIDIA card.

---

### Post by linuxgeek77 on 2009-11-23
AUDIO CARDS sorry  

you need to reboot after you do that. thank you.

---

### Post by reddox on 2009-11-23
Worked thanks!

But, I have a laptop and the white noise generated (you gotta listen closely) if I turn off the "power saving mode" would take up *some* battery...so I guess I gotta live with the crackling.

---

### Post by linuxgeek77 on 2009-11-23
> **reddox said:**
> Worked thanks!

But, I have a laptop and the white noise generated (you gotta listen closely) if I turn off the "power saving mode" would take up *some* battery...so I guess I gotta live with the crackling.
  Nope its not going to hurt your power. this feature was just aded in ubuntu 9.10, and my battery life is still giving me 3 hours of use. at least now when i boot up i dont hear crackles and noises that annoy me. it wont kill your power. i have tested it with and without power saving. for the whote noise ur experiencing try updating your alsa drivers to the newest version. i dont have a link on me. but you can go to alsa's website check out whats teh latest versions. and go to google and type "ubuntu ALSA driver updating" and follow teh steps.


: i found a link for you to follow. its to help compile teh lastest alsa drivers. 1.0.21a here you go. 
[http://www.webupd8.org/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html](http://www.webupd8.org/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html)

note: adjust the file names on Wget according to teh latest alsa drivers you find on teh site.

---

### Post by Xodiac13 on 2009-11-29
Nice it worked, thank you and for anyone else that has this problem follow the instructions, now makes my games run a whole lot smoother. :)

---

### Post by 4zdenek on 2009-12-02
Thanks, it's worknig. I couldn't stand that noise, it felt as someone was sticking needles into my speakers.

---

### Post by linuxgeek77 on 2009-12-07
> **4zdenek said:**
> Thanks, it's worknig. I couldn't stand that noise, it felt as someone was sticking needles into my speakers.

your welcomed i'm glad it works for you now :)

---

### Post by linuxgeek77 on 2009-12-07
> **Xodiac13 said:**
> Nice it worked, thank you and for anyone else that has this problem follow the instructions, now makes my games run a whole lot smoother. :)

thx for posting. im glad it helped you :)

---

### Post by DouglasCaixeta on 2009-12-09
Where is the power save option?

Here is my alsa-base.conf content:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

---

### Post by kapi on 2009-12-14
Brilliant, so far so good. 

Thankyou for the words of wisdom

---

### Post by hobo14 on 2009-12-15
For Realtek cards, that may not work.

If it doesn't, try this:

$ **sudo apt-get install linux-backports-modules-alsa-karmic-generic**

---

### Post by smerral on 2009-12-15
Yes, I also found this out - not from you but from somewhere else on this forum. Only difference is instead of deleting I commented the powersave line out by adding # at the beginning. Works just the same.

Brian

---

### Post by linuxgeek77 on 2009-12-19
> **DouglasCaixeta said:**
> Where is the power save option?

Here is my alsa-base.conf content:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```


Are you using an HDA card? this is for HDA cards. it diesnt seem you have an HDA card. if that case. try updating your alsa drivers should work fine after that. here is a great link to update your drivers. 
[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)  < find out what are teh latest drivers. teh complete list of drivers on their right panel. 
and follow these steps here. [http://www.webupd8.org/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html](http://www.webupd8.org/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html) and change the Wget links to teh latest drivers (numbers). and install them.

---

### Post by linuxgeek77 on 2009-12-19
> **hobo14 said:**
> For Realtek cards, that may not work.

If it doesn't, try this:

$ **sudo apt-get install linux-backports-modules-alsa-karmic-generic**

or you can simply update your alsa drivers to their latest release. works like a charm on my notebook.

---

### Post by saiganesh on 2009-12-19
Awesome! The sound was really annoying..what was more annoying was I spent a day searching for ubuntu sound issues...good job! How do you become a linuxgeek? :D:P

---

### Post by Michael_K_Vegfruit on 2009-12-30
I went the commenting out route suggested above. Then it struck me you could also try setting the power save time out to a more sensible limit: 900s (15min) will, I reckon, turn the sound card off when I am truly idle, and leave it on in most other cases.  Haven't rebooted yet, but will report back here in the next few minutes if it doesn't fix the problem as I expect it to.

Just saw this vaguely appropriate smiley and couldn't resist using it. 

:guitar:

Sorry.

---

### Post by LuisGMarine on 2009-12-30
Thanks for this I'll have to give it a try when I get back home to my desktop PC.  I can't tell you how annoying just listening to music really loud and forgetting to turn down the volume then in the middle of the night I think Jason is coming down the hallway.

---

### Post by dimaspivak on 2010-01-07
After applying the most recent recommended updates in Karmic, this problem has come back for me. I can confirm that the relevant portion of alsa-base.conf is still commented out, however. Anyone else seeing this again?

Update: And as strangely as it began, it ended. Another restart and the problem went away. Weird.

---

### Post by LuisGMarine on 2010-01-07
This still hasn't worked for me, I'm going to try to compile my own alsa drivers and see if maybe that fixes the problem :(

---

### Post by leorolla on 2010-03-07
Latest Karmic kernell already comes with ALSA 1.0.22

So no need for re-compiling everything and doing all that ugly job.

My Acer Aspire One works fine with ALSA 1.0.21 but has crackling sounds with 1.0.22, so I'm going back to the previous kernel.
My Medion 96419 has crackling and I will try this solution with it.

This crackling sound, it is a bug, right?
How should we report it to ALSA developers?

---


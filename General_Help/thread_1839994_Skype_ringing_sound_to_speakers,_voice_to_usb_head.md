---
title: "Skype ringing sound to speakers, voice to usb headset with pulseaudio"
date: 2011-09-06
forum: General Help
---

### Post by Ashrael on 2011-09-06
Hi all, 

since the change to pulseaudio it was impossible for me to route my ringing sound to the speakers and the voice/conversation to usb headphones.
Finally I found a solution to this problem which doesn't amount to downgrading to alsa.

If you are looking for a HOWTO on installing usb headsets: 
[http://ubuntuforums.org/showthread.php?p=11225062#post11225062](http://ubuntuforums.org/showthread.php?p=11225062#post11225062)
There I also posted the text below.

Thanks to Jim Hunziker for figuring it out!

At first glance (and even at second and third) it seems impossible to set the ringing sound to speakers and the conversation to usb headset.

But follow above HOWTO and then:

1) open pavucontrol and skype>options>sound devices next to each other.
2) press "make a test sound" and (be fast) you will be able to choose (in pavucontrol) the sounddevice to route the ringing sound to, e.g.: Internal audio ananlog stereo.
3) press make a test call and route the call sounds to a usb headset.

DONE!

---

### Post by sembagdod on 2011-12-03
Well It didn't work for me, when i change the sound in PAVC for "test call" it changed on "test sound" as well. 

Anyone knows alternative solution?

---

### Post by sembagdod on 2011-12-22
I found another workaround to solve this issue

1- Download the Skype incoming call sound from any website such as [[http://dc338.4shared.com/download/ALscuwbI/Skype_Ringtone.mp3?tsid=20120120-095342-bee8a5a1]](http://dc338.4shared.com/download/ALscuwbI/Skype_Ringtone.mp3?tsid=20120120-095342-bee8a5a1])
2- Install "Audacity" form Software Center 
3- Using Audacity convert the sound to "odg" format.
4- Should use Root acess - Open termnial type "su -" the put the password, then type "nautilus" a new window will open
5- Save the file as "s.odg" in [usr-share-sounds-ubuntu-stereo]
6- Open Skype and go to (Options-Notification-Advanced View - choose incoming Call Rining and under "Execute the following script:" put the following command [/usr/bin/canberra-gtk-play --id="s"]

---

### Post by sembagdod on 2011-12-23
You can choose any other kind of notification you might need .. 

Enjoy

---

### Post by fraker13 on 2012-03-07
I am struggling with both these solutions.

The problem with Ashrael's solution is that when I play the test sound in Skype, the Playback tab in pavucontrol does not show the application/stream, so I cannot choose the output device. This happens for most of the sounds under "notifications", too, but not for the Test Call (nor Outgoing Call Ringing in notifications and a few other notifications). Whenever pavucontrol** doesn't** show the application/steam it displays the following on its console output:
[FONT=Courier New]
[/FONT][FONT=Courier New]Ignoring sink-input due to it being designated as an event and thus handled by the Event widget[/FONT]

The problem with sembagdod's solution is that /usr/bin/canberra-gtk-play --id="s" displays 

[FONT=Courier New]Failed to play sound: File or data not found[/FONT]

even though the file is in /usr/share/sounds/ubuntu/stereo. It works fine for other files in that folder. Note that I have exported the file as a .ogg (not .odg) from Audacity...

Any help gratefully received

---

### Post by Ashrael on 2012-04-26
I think this is an mplayer problem. mplayer.conf maybe.

Can you post your: /etc/mplayer/mplayer.conf file?

---

### Post by Ashrael on 2012-09-08
Since the update of skype to 4.0 I cannot route the ringing sound to one output and the speech sound to another output. It seems the folks at skype havent taken pulseaudio into account. The ringing sound used to be advertised to the soundserver under a different name than the speech sound, since the update it seems there is no difference anymore.

I will look into this, because I want it solved asap.... In the mean time all tips and questions are welcome!


TIA!

---

### Post by Ashrael on 2012-09-30
For now I use sembagdod's method. Except I've made a bit simpler howto:

Only step 6 is vital, since I use an existing sound, so I changed it to:

Open Skype and go to (Options-Notification-Advanced View - choose incoming Call Ringing, uncheck play soundfile and check: "Execute the following script:" put the following command [/usr/bin/canberra-gtk-play --id="phone-incoming-call"

Et voila!:popcorn:

Still hope the folks at skype fix this problem soon....

---


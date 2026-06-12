---
title: "Logitech C260 Webcam (mic not funtioning)"
date: 2011-09-10
forum: General Help
---

### Post by johnsmoke on 2011-09-10
So I hooked up my usb logitech webcam, model C260. I brought up the Cheese Webcam Booth and try to record some video to test the audio and all... when I record it is a bit choppy, but when I play it back there's no sound at all. I'm trying to set this up so that I can use it with Skype. I tried the audio test in Skype, but that doesn't record from my mic either. How could I set up this webcam/mic so that my microphone is recognized in Ubuntu and I can use it in Skype?

---

### Post by papibe on 2011-09-10
I have a Logitech webcam pro 9000. In order to make the mic work in Skype, I have to change the sound settings before creating a chat.

I go to Sound Preferences -> Input. There it is usually set to 'Internal Audio Analog Stereo, but I change it to '0809 Analog Mono'. Which is my web cam microphone.

Hope it helps,
Regards.

BTW, the '0809' coincides with the USB id if my camera:
```
$ lsusb | grep -i logitech
Bus 002 Device 003: ID 046d:**0809** Logitech, Inc. 

```

---

### Post by johnsmoke on 2011-09-11
> **papibe said:**
> I have a Logitech webcam pro 9000. In order to make the mic work in Skype, I have to change the sound settings before creating a chat.

I go to Sound Preferences -> Input. There it is usually set to 'Internal Audio Analog Stereo, but I change it to '0809 Analog Mono'. Which is my web cam microphone.

Hope it helps,
Regards.

BTW, the '0809' coincides with the USB id if my camera:
```
$ lsusb | grep -i logitech
Bus 002 Device 003: ID 046d:**0809** Logitech, Inc. 

```

Thanks very much for the advice! I just went into the little sound icon on the top right of the screen and went into "Sound Preferences" and from there I could change my input device to my webcam! This is awesome, just this morning I managed to get my scanner working and now my webcam is fully functional! I have everything I need running in Ubuntu now!!

---

### Post by papibe on 2011-09-11
:p Glad you solve it. Mark the thread solved when you have the chance.

Regards.

---

### Post by craig.o on 2012-04-12
Just an fyi:

The same solution worked on my 32-bit v11.10 (Oneiric Ocelot).  The device listed was '081a'

thanks & hth,
-Craig
[IMG]http://www.flickr.com/photos/ocraig/6925310368/[/IMG]

---


---
title: "How to make linux recognize your camera!"
date: 2010-12-30
forum: General Help
---

### Post by Cotopaxi on 2010-12-30
I am observing all the time people are having trouble getting their cameras recognized by Linux, so I am going to write this primitive “How-to”: How to connect your camera to Linux.

0)
If you have the camera switched off and you plug it into the USB port, the camera only goes into BATTERY CHARGING MODE without any identification of the operative system!

1)
Download: 
“gphoto2” and “gtkkam” (for Ubuntu) or
„gphoto2“ and “digikam” (for Kubuntu)

2)
BEFORE plugging the camera into the computer's USB port, SWICH IT ON and put the camera on PHOTO SHOOTING MODE! 

3)
NOW you plug the camera into the USB port of your computer and the camera should be recognized immediately.  the respective program („gtkkam“ or „digikam“, gphoto2 acts in the background) opens up immediately and you are ready to go!

Every Kodak EasyShare camara is recognized immediately!

Good luck!

---

### Post by Cotopaxi on 2010-12-30
This is a duplicate post, the other one is in "Multimedia". I am doing it on purpose, because I think people really need some help about this stuff.

---

### Post by no2498 on 2010-12-30
? 
do they need to unmount the cam
just unplug it ?
turn it off ?
i turn mine on after i plug it in
i unmount and turn it off before i unplug it

---

### Post by Cotopaxi on 2011-01-20
no,

Sorry I am replying so late, I just realized your post.

In my case, I don't mount the camera, I just:

1) switch in on,

2) plug it into the USB port,

3) "Digikam" opens up and I am ready to go.

In my case (Kodak Easyshare M340) if I turn the camera on AFTER plugging it in, the camera doesn't do anything.

I also don't unmount the camera, I just shutdown "Digikam". If I afterwards open the file-manager (Dolphin in Kubuntu), the camera is not shown, which leads me to believe thet Digikam unmounts the camera.

---

### Post by lithopsian on 2011-01-20
I have had all sorts of trouble with the gphoto USB detection.  It is way too touchy.  So I use thunar-volman to automatically mount the camera and send the results to gphoto.  It works whether the camera is plugged in and then turned on or just plugged in already on.  I had to disable the gphoto volume detection which it complains about in the logs from time to time because it won't provide a clean way of doing this.

Digikam is nice but a huge bloated thing unless you already have its libraries installed.  Early versions have some quirks but the new ones are pretty slick.  I didn't like gtkkam at all.

---

### Post by rimibchatterjee on 2011-11-02
Tried this method with my Kodak Easyshare Z915 and Ubuntu 11.10. No luck. Previously I got the error : Unable to mount....could not lock the camera. Nevertheless I was able to access my photos ONCE with shotwell. Now the camera does nothing whether I turn it on and plug it in or vice versa. It doesn't even show up in Nautilus or Desktop. I see elsewhere on this forum that lots of people have struggled with this and it seems to be a systemic Kodak problem. However the last message int hat thread was 2010. Has there been any progress since? Any ideas?

---

### Post by RayArdia on 2012-01-03
> **rimibchatterjee said:**
> Tried this method with my Kodak Easyshare Z915 and Ubuntu 11.10. No luck. Previously I got the error : Unable to mount....could not lock the camera. Nevertheless I was able to access my photos ONCE with shotwell. Now the camera does nothing whether I turn it on and plug it in or vice versa. It doesn't even show up in Nautilus or Desktop. I see elsewhere on this forum that lots of people have struggled with this and it seems to be a systemic Kodak problem. However the last message int hat thread was 2010. Has there been any progress since? Any ideas?

I too have been trying to make sense of all this! I have two Kodak Easyshare (sic) cameras a C713 and a Z740. Just out of curiosity I posted a question on the Kodak Support website, with this rather unhelpful reply:-
 Response Via Email (Therese R.)	01/03/2012 03:34 AM
Customer Reference Number: 111231-000355
Dear Mr Ray Allinson
Thank you for your e-mail regarding Kodak doesn't support Linux.
This is correct that Kodak does not support Linux.
If we can be of any further assistance please do not hesitate to contact us, quoting your reference number above.
Yours sincerely, 
Therese R
Kodak Technical Support
[http://www.kodak.com/go/support/(-](http://www.kodak.com/go/support/(-) don't bother if you're a Linux type, we don't want to know you)

As both cameras _had_ been recognised when I was using an older Ubuntu distro, I tried installing gphoto2. Now no doubt the man page for gphoto2 means something to the 'experts' but not to me. Anyway gphoto2 doesn't help  because I still get the error msg "Error initializing camera:-60: Could not lock the device"

Now, just before someone barks "Why don't you just slot the  SD card into your SD cardreader?" -well I can, and do, but much prefer to use a USB cable for various reasons, one of them being that on the smaller cameras, like the C713, you have to take out the batteries to get at the SD card. Besides, not everyone's computer has a card reader.

Is there really no simple solution to this niggling little annoyance?

---


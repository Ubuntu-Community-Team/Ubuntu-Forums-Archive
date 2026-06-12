---
title: "usb webcams work fine in Cheese but not in Skype"
date: 2010-11-04
forum: General Help
---

### Post by jakelute on 2010-11-04
Hi,

I wonder if someone might be able to help with a webcam problem I'm having (or point me in the direction of a previous thread on the subject?). Thanks in advance.

I'm trying Xubuntu on my wife's elderly Dell Inspiron 1100 laptop. It's working beautifully for the most part. But I've tried two different usb webcams, both of which are recognized by Cheese but don't work in Skype.

In Skype, what happens is that Skype is aware that a webcam is present. It does NOT say "no webcam detected". But in Skype Options, when I visit the Options for "Video Devices", and click on the "Test" button to test the webcam, nothing happens at all. 

And when I make a test video call to a friend, with video turned on, all the friend sees is a black screen where the image should be, and a little turning symbol presumably to indicate "please wait for image to appear". It never appears.

Any advice would be very much appreciated.

Thanks!

---

### Post by joshzam on 2010-11-04
I had the same problem. Try running Skype using the following in the Terminal:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

If this works, you can change the way your program runs via the Applications menu:
go to System > Preferences > Main Menu > Internet > Skype > Properties
change Command: from
```
skype
```
to
```
env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

Hope this helps!

---

### Post by jakelute on 2010-11-04
Many thanks for this reply!

When I open Skype as you describe, it opens just fine. And when I go into Options, I find that I CAN test the webcam, and I get a perfectly good image, so that's progress.

But when I do a test call to a friend, Skype crashes (error message "Segmentation fault" or "Aborted" -- sometimes one, sometimes the other) as soon as the video starts up.

Any thoughts about why that might be?

Thanks again.

---


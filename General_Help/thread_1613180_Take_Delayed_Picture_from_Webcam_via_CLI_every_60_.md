---
title: "Take Delayed Picture from Webcam via CLI every 60 seconds"
date: 2010-11-04
forum: General Help
---

### Post by HornedBeast on 2010-11-04
Hello,

I have a script running at the moment via cron which takes a picture every minute from my webcam.

gst-launch-0.10 v4l2src num-buffers=1 ! jpegenc quality=95 ! filesink location=/home/user/$picture.jpg

However, the camera is only on for one second and takes the picture which leads to very dark images as the light sensor hasn't had a chance to work yet.

However, if I load up Cheese, it brightens after about 10 seconds of the camera being on.

Is there anyway of adding in a delay to the pipeline above so the camera stays on for 10 seconds before actually saving the file to a jpg?

Cheers,

Horned

---

### Post by HornedBeast on 2010-11-07
Ok, more importantly then, is this even possible at all? Or do I need to use Python or something to add the "Snapshot" part to the pipeline dynamically?

Horned

---

### Post by Hippytaff on 2010-11-07
You might be able to use the sleep command in the bash script. Have a look at the man page
```

man sleep

```

---


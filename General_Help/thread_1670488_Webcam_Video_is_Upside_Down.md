---
title: "Webcam Video is Upside Down"
date: 2011-01-19
forum: General Help
---

### Post by colmeweb on 2011-01-19
Hi everybody,

I am running Ubuntu 10.04 on a Toshiba Satellite A215 with a USB Toshiba webcam (PA3554U-1CAM). The camera works but the image is upside down in both skype and cheese. I have been looking through some other threads and none of their solutions work. My vid driver library is up to date as far as i know.

Thanks.

---

### Post by hawthornso23 on 2011-01-19
Some laptop manufacturers install the camera upside down I guess because it fits in the case better that way or something. They then flip the image back in the video driver (the windows one) which is installed in the laptop at time of sale. The trouble that ubuntu has is that it didn't make your laptop and doesn't know the camera is installed upside down.

Unless you feel like opening up your case and turning the camera right way up (don't laugh - some people do this), the best solution is to tell v4l - the linux driver - to flip the image.  The more recent v4l can do this easily.  

For detailed instructions as to how to install it go to this thread and read post 12.

[http://ubuntuforums.org/showthread.php?t=1449263](http://ubuntuforums.org/showthread.php?t=1449263)

Good Luck

---

### Post by colmeweb on 2011-01-19
My camera is an external one. The camera isn't upside down, just the output. 
Thanks

---

### Post by colmeweb on 2011-01-19
My camera is an external one. The camera isn't upside down, just the output. 
Thanks

---

### Post by colmeweb on 2011-01-19
I am using an external usb camera. Only the output is upside down, not the camera. 

Thanks

---

### Post by colmeweb on 2011-01-19
I am using an external usb camera. Only the output is upside down, not the camera. 

Thanks

---


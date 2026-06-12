---
title: "can't get image from web cam"
date: 2011-12-19
forum: General Help
---

### Post by JCM_Pico on 2011-12-19
hello,

I can't get any video from my web cam in Skype... neither in cheese, in the last one I got this error  ```
 One or more needed GStreamer elements are missing: gconfaudiosrc, gconfvideosink.
```

In Skype I don't get any error output....

Any one knows how to solve this?

I recently installed kdenlive and I'm running ubuntu...

---

### Post by JCM_Pico on 2011-12-20
Bump!!!!

---

### Post by lukeiamyourfather on 2011-12-20
What camera are you using? Is it a UVC device?

---

### Post by howefield on 2011-12-20
Do you have the package gstreamer0.10-gconf installed ?

---

### Post by JCM_Pico on 2011-12-20
It isn't UVC device... Its my laptop buitin camera... That already worked before :(

Been searching and found some people solving it by doing 
```
sudo apt-get install gstreamer0.10-gconf
```

But this packaged isn not found
```
 Couldn't find package gstreamer0.10-gconf
```

---

### Post by JCM_Pico on 2011-12-20
> **howefield said:**
> Do you have the package gstreamer0.10-gconf installed ?

I tried but I cant find the package :(

---

### Post by JCM_Pico on 2011-12-20
SOLVED !!!

I added the repository for gstreamer-developers
```
sudo add-apt-repository ppa:gstreamer-developers/ppa
```

and then installed gstreamer0.10-gconf
```
sudo apt-get install gstreamer0.10-gconf
```

Thank you all :P

---

### Post by howefield on 2011-12-20
Are you using Ubuntu 10.04 as per your profile ?

---

### Post by JCM_Pico on 2011-12-20
> **JCM_Pico said:**
> SOLVED !!!

I added the repository for gstreamer-developers
```
sudo add-apt-repository ppa:gstreamer-developers/ppa
```and then installed gstreamer0.10-gconf
```
sudo apt-get install gstreamer0.10-gconf
```Thank you all :P

BUT.... that just one part of the problem.... I still have not video in skype :(

---

### Post by JCM_Pico on 2011-12-20
> **howefield said:**
> Are you using Ubuntu 10.04 as per your profile ?

yes I'm using 10.04 :)... 

Solved the problem with skype running in terminal the following```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 
```

Is there any way to make ubuntu run this when I click in skype launcher?

Already tried to add the entry in  the application menu... but it does not worked ....

---

### Post by plucky on 2011-12-20
> **JCM_Pico said:**
> yes I'm using 10.04 :)... 

Solved the problem with skype running in terminal the following```

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 
```

Is there any way to make ubuntu run this when I click in skype launcher?

Already tried to add the entry in  the application menu... but it does not worked ....

This is what I have in my skype launcher on the panel ```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
``` but I am using 10.04 64-bit so yours should possibly be ```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```

Good Luck

---

### Post by JCM_Pico on 2011-12-20
> **plucky said:**
> This is what I have in my skype launcher on the panel ```
bash -c 'LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype'
``` but I am using 10.04 64-bit so yours should possibly be ```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```Good Luck

Worked

Thank you all for helping me

---


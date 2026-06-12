---
title: "mp3 use blackberry pearl flip 8230"
date: 2010-06-07
forum: General Help
---

### Post by laineywolff on 2010-06-07
I have a 8 GB memory card in blackberry pearl flip 8230.  I have Ubuntu 10.04 Lucid Lynx.  When I plug in the usb to micro connection cord the phone does charge so it would appear that something in the computer and the phone are talking.  However, the computer does ever identify that it is connected to anything.  I am therefore unable to download music and/or other media to my phone which functions as a 8GB mp3 player. 

My Memory-Media Card settings on the phone are Media Card Support:  ON
    Encryption Mode:   None
    Mass Storage Mode Support:  On
    Auto Enable Mass Storage Mode When Connected:   YES

Applcation Memory Free Space:   56.4mb

MediaCard
    Total Space  7.5 GB
    Free Space   7.5 GB

I get no error messages from my computer.  

ANYONE have any suggestions on how to proceed?

Thanks

Lainey

---

### Post by pytheas22 on 2010-06-07
It could be the case that your phone is simply not supported, but even if it is, you may need to install additional software to allow Linux to communicate with it.  So let's gather a little more information and then google.  What is the output of:
```

lsusb
```

when the phone is plugged in?

Unfortunately, the phone being able to charge while plugged in doesn't necessarily mean anything other than that your USB cable has electricity running through it, which works independent of the operating system.

---


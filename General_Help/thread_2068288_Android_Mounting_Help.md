---
title: "Android Mounting Help"
date: 2012-10-08
forum: General Help
---

### Post by Malvazar on 2012-10-08
Mkay I've have officially exhausted my search engine skills on this matter. I would really like to be able to simply connect my samsung intercept with android 2.2.2 to my computer (Ubuntu 10.04 x64) and mount the sd card and  sync it with banshee. The problem is I can't get Ubuntu to recognize the phone is connected. The phone knows its connected to a usb power source but beyond that nothing. I have usb debugging mode turned on (hell I've tried with it off too), and have to phone fully updated as far as i can (2.2.2). I just can't seem to get Ubuntu to recognize the phone. I could really use some insight on this matter please.

---

### Post by sneaky1 on 2012-10-08
> **Malvazar said:**
> The phone knows its connected to a usb power source but beyond that nothing.

Did you actually tap the "usb connected" notification and click your way through the "okay" messages?

---

### Post by Malvazar on 2012-10-09
> **sneaky1 said:**
> Did you actually tap the "usb connected" notification and click your way through the "okay" messages?

I don't get that prompt on my phone anymore. I got it once when I first got the phone but never scene. (and yes I did tell it to connect the one time i had it)

---

### Post by sneaky1 on 2012-10-09
I have generally used the newer versions of Android, but the only time I've had that issue is when I enabled Fast Charge. As soon as I disabled it, everything worked ok. If you have that option in your kernel or in an app or something, you could try disabling it. I'm not certain but it sounds to me like this is not your problem since it's registering as USB power, and I seem to remember mine registered as AC when on fast charge.

So, thinking more broadly, I've noticed with some USB sticks and adapters, they only work when plugged into a certain USB port on my netbook. Perhaps try switching things around a little? Even try using a different usb cable if you have one.

Another suggestion is to boot Ubuntu from the live CD, and see if it recognizes the phone that way. This should let you figure out if it's an Ubuntu or Android problem.

---

### Post by Malvazar on 2012-10-09
Thanks for the info, but I don't recall seeing anything like fast charge on the phone. I guess I'll give the live cd a try.

---

### Post by surajkumarr on 2012-10-09
Add your device to udev. you will get the vid and pid from lsusb command. just search for "howto set android developer device permissions with udev"

---

### Post by Malvazar on 2012-10-09
That finally did it! It finally showed up on the computer! Thankyou so much thats been driving me nuts.

---

### Post by buzby01 on 2012-10-30
Can you give us instructions for the reply that worked. I'm having the same problem and I'm not sure what the vid and pid is or which udev file to add it to

Cheers

---

### Post by surajkumarr on 2012-11-10
> **buzby01 said:**
> Can you give us instructions for the reply that worked. I'm having the same problem and I'm not sure what the vid and pid is or which udev file to add it to

Cheers
vid is vendor ID and pid is product ID. type ```
lsusb
``` in terminal.The 4 characters after the ID and before : is VID and four character after : is PID.
Please check this link from [wiki.cyanogenmod]("http://wiki.cyanogenmod.org/wiki/Udev") for more information

---


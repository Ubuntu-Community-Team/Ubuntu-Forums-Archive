---
title: "boot splash problem in ubuntu 10.10"
date: 2010-10-03
forum: General Help
---

### Post by macdonaldjnew on 2010-10-03
Hi everyone,

I recently upgraded to 64-bit maverick (from 64-bit lucid) and I'm getting this ugly boot splash now - it's a purple screen with a very basic "ubuntu 10.10" written in terminal font and four dots underneath. I am running a dell xps m1530 with nvidia graphics card, and haven't had any trouble with the boot splash before. I have run the additional hardware drivers utility and it says I have the latest Nvidia driver already loaded apparently. 

I have looked around the forums and tried a few suggested solutions, like updating the initramfs with the framebuffer=y line but that didn't do anything. I also tried adding a new theme in plymouth and switched to that instead, but it still doesn't come up. 

Is it a 10.10 bug or can someone help? 
Thanks!

---

### Post by meatball on 2010-10-03
Here you go... see if this does the trick for you.


[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

---

### Post by macdonaldjnew on 2010-10-04
Worked a charm, thanks very much!

---

### Post by K_REY_C on 2010-10-11
Yes --- follow the instructions on the link above... just make sure to input your desired resolution everywhere (instead of simply copy & pasting). Mine was 1440x900... and it worked like a charm.

---

### Post by K_REY_C on 2010-10-14
Not sure if this is related (but I suspect it might be) --- I'm now having graphical glitches when shutting down. Is that still referred to as the "bootsplash?" At any rate --- is this a problem that anyone else is having? Can it be resolved?

Thanks!

---

### Post by Kvothe on 2011-03-13
My resolution is 1336x768, and no matter what I do with that tutorial I still get a very large or glitched boot screen. Anyone have any help for me?

---

### Post by ApocryphalAuthor on 2011-03-18
> **Kvothe said:**
> My resolution is 1336x768, and no matter what I do with that tutorial I still get a very large or glitched boot screen. Anyone have any help for me?

Try in the terminal:
```
sudo apt-get install hwinfo
```
and
```
sudo hwinfo --framebuffer
```
This will show you which screen resolutions are available.  Use one of those in the */etc/default/grub*.

Hope this helps.

---


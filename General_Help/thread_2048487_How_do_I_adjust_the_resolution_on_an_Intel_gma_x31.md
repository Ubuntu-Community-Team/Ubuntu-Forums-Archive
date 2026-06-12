---
title: "How do I adjust the resolution on an Intel gma x3100?"
date: 2012-08-26
forum: General Help
---

### Post by syb3ria on 2012-08-26
Hello everyone. I'm with fresh install of 12.04, having gma x3100 on G31 motherboard. The problem is I own 19" monitor with native resolution of 1280x1024 but can't force screen resolution on more then 1024x768.
```

~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
```

I been digging up some info for the past 4 days, yet haven't found any solution. Even tried using gdm instead of lightdm.

Any help is appreciated.

---

### Post by syb3ria on 2012-08-28
If that might help, when i ran upgrade from 11.10 to 12.04 it was all fine. Can someone come up with solution? I don't want to migrate on 12.10 yet or spend few hours running upgrade from 11.10 > 12.04.

---

### Post by mörgæs on 2012-08-28
In your case I would stick to 11.10 for as long as it's supported (april 2013). When support runs out you will have 12.10 and 13.04 to choose from.

---

### Post by syb3ria on 2012-08-29
Thank you for the suggestion. But I would still like to have high resolution on 12.04 with that specific box. Seem the only way is to put 11.10 and run an upgrade to 12.04 because that already has prooven to work fine. Which reminds me, isn't there any way to hack the xorg or whatever it is on the lastest ubuntu to help me out with this?

---

### Post by syb3ria on 2012-10-23
I managed to find out how to fix this issue with 12.04 and 12.10. I have an 9800GT video card which i'm not using. I set it up, booted and the resolution was 1280x1024, which was exactly what i wanted. Checking the drivers let me know that some generic nvidia driver was used. I shutted down the machine, pluged out the video card and booted again. Voilla, ubuntu was wise enough to keep the resolution at 1280x1024. 

Also I found out that this issue with gma x3100 is starting with 11.04 till the most recent one. So.. if you have the same problem and you can borrow a video card for simple plug in/out, you will continue using your gma happily :-\"

---


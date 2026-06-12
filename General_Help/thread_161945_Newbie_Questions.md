---
title: "Newbie Questions"
date: 2006-04-18
forum: General Help
---

### Post by LBadvance on 2006-04-18
Im using this on my laptop Acer Aspire 3623WXCi and i have a few issues with running ubuntu on it

1.) Mouse on the touchpad is tooooo fast. I have played around with the sensitivity and acceleration thing in System -> mouse to no avail. 

2.) Disable double tap as a click o touchpad. I like just clicking the button.

3.) Ubuntu can't adjust the fan on the laptop correctly, resulting in the fan making a high-pitch whine. This does not happen inside windows. 

4.) Newbie question: How do i install kate, or any other programs for the matter.

Thanks,
Ubuntu newbie.

---

### Post by sYs^ on 2006-04-18
Touchpad, check this, might help: [http://ubuntuforums.org/showthread.php?t=132626&highlight=touchpad+fast](http://ubuntuforums.org/showthread.php?t=132626&highlight=touchpad+fast)

Installing software: Open up a terminal:
```

sudo apt-get update
sudo apt-get install kate
```

---

### Post by LBadvance on 2006-04-18
Thanks! But thats too advance for me to understand... 
 
Now for the buzzing issue, seems it is not the fan's fault. Whilst searching I did find i am not alone, there is a tread already on whine occuring when running on laptops. 

[http://ubuntuforums.org/showthread.php?t=21232](http://ubuntuforums.org/showthread.php?t=21232)

If only i could understand how to do the fix for it :(

---

### Post by sYs^ on 2006-04-18
Then just ask :> with which part have you problems?

---

### Post by LBadvance on 2006-04-18
He did not explicitly say which part you are suppose to put the commands in or i just missed that part in his post althought i've read it 10x.  Figured it out myself :) Its to go in the /boot/grub/menu.lst, now im typing ubuntu noise-free!

---

### Post by LBadvance on 2006-04-18
Oh only problem left is i see no option in the lin you provided to turn off the click on touchpad.

---

### Post by sYs^ on 2006-04-18
I never had a notebook before so I never tried to configure it, but I found this:

> How can I configure tap-to-click behavior?

1. If you set MaxTapTime=0 in the X config file then the touchpad will not use tapping at all, i.e. touching/tapping will not be taken as a mouse click.
2. If, instead, you set MaxTapMove=0 in the X config file, then the touchpad will not use tapping for a single finger tap (left mouse button click) but will for the two and three finger tap (middle and right button click).

More: [http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/)

---


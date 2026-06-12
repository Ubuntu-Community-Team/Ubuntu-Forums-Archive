---
title: "Can't stop Ubuntu from dimming TV screen"
date: 2012-10-08
forum: General Help
---

### Post by xCaptainAmazing on 2012-10-08
To start, I'll say that I have all the latest updates installed for 12.04 and the most current stable nvidia driver release by the x-team.

I'm running Twinview mode in the nvidia-settings to achieve a dual monitor layout for my dell computer monitor and samsung tv. It seems to work just fine for the most part, but the samsung tv instantly dims a lot just mere seconds after it connects.

I've been searching for hours and I've come up completely dry. What I do know is that the only way I've been able to adjust brightness on either is via nvidia-settings because the slider in ubuntu settings and the tickbox for dimming both do nothing.

The dimming effect is identical to the one where you leave your computer idle for "x" number of minutes. I recognize it from my laptop. Can anyone point me in the right direction? If there's some way of manually disabling dimming, I'd be all for trying it. I don't need it. I also tried just raising the brightness, but since the dimming effect appears to be more than just affecting brightness, it looks really odd when you do this.

---

### Post by hawthornso23 on 2012-10-08
Not sure if this is what you want but try 

```
 xset -dpms 
```to prevent power management dimming the screen and 

```
 xset +dpms 
```to reenable it. If this is what you want try setting up some keyboard shortcuts for these.

---

### Post by mike555 on 2012-10-08
I use the program " Caffeine " it works well at not letting your computer sleep or dim.

---


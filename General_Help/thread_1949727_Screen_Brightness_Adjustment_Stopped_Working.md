---
title: "Screen Brightness Adjustment Stopped Working"
date: 2012-03-30
forum: General Help
---

### Post by rcrampton on 2012-03-30
Posted in Apple Support forum first but no response so I thought I'd try here.



My screen brightness function keys used to work just fine. I hooked up an external monitor and used both the built-in "displays" application and then the "nvidia xserver settings" application to change my settings.

I have since then used the nvidia app to reset everything back to a single display.

Only problem is that my display function keys no longer control the brightness. The icon and brightness scale appear on the screen when I hit the keys and the scale goes up and down. Sometimes the laptop will come out of suspend fully bright, sometimes fully dim.

I did not backup my xorg.conf settings file (oops).

I'm running an Intel Macbook Pro 5.4, Ubuntu 11.10, 32bit.

Any help is appreciated!

---

### Post by JC Cheloven on 2012-03-30
Not exactly an answer, and perhaps old news, but from the nvidia application you can adjust brightness (and much more). 
Launch ```
nvidia-settings
``` and click in 'X server color correction'. There you'll find sliders for brightness, contrast and gamma.
Hope this helps
JC

---

### Post by rcrampton on 2012-04-01
> **JC Cheloven said:**
> Not exactly an answer, and perhaps old news, but from the nvidia application you can adjust brightness (and much more). 
Launch ```
nvidia-settings
``` and click in 'X server color correction'. There you'll find sliders for brightness, contrast and gamma.
Hope this helps
JC

Thanks, that works and is at least a workaround for the time being.

Of course it requires messing with three sliders so it's not too convenient.

If anyone has ideas on how to map the brightness function keys to the actual screen brightness it would be greatly appreciated!

---

### Post by JC Cheloven on 2012-04-02
> **rcrampton said:**
> Of course it requires messing with three sliders so it's not too convenient. Adjusting brightness should suffice.

> If anyone has ideas on how to map the brightness function keys to the actual screen brightness it would be greatly appreciated!
In fact I'm posting again to somehow bump your thread. Hope someone jumps in with an exact fix for you!  ):P

---

### Post by rcrampton on 2012-04-04
The plot thickens - When I come out of suspend the screen brightness will be at whatever I set it to when I went into suspend mode.

In other words - I can click the brightness up/down with the function keys - nothing happens. I suspend and resume and it will come up wherever I left the setting.

---


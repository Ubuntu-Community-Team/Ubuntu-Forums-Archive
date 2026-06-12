---
title: "Hdtv problems."
date: 2010-07-02
forum: General Help
---

### Post by kingrobdun on 2010-07-02
My friends bought me a 22" Sylvania lc220ss1 HDTV a while ago. The problem is that I cant change the resolution with out it looking weird. On the box it recommends 1366x768, and it still wont work. Graphics cards that I used: Nvidia gt 240 and ati hd 5570 ( had to return the nvidia card cause it died)

---

### Post by papibe on 2010-07-02
What 5570's output are you using to connect to the TV?
What kind of cable?
Which TV's input are you using?

I own a Sony HDTV. The resolutions supported depend on which input do you use. For example when I use TV's VGA input, I pretty much can any "regular" PC-monitor resolution.

On the other hand, HDMI inupt works best with TV's resolution: 720p (1280x720) and 1080p (1920x1080).

If I have to guess, try first 1280x720. Sounds to me like a good start when testing res on TVs.

Good Luck.

---

### Post by kingrobdun on 2010-07-02
I was able to fix the problem. I tried my male to male HDMI cable and switched the resolutions to 1280x720 and it showed up with a black border, and the text was blurry. I switched to a male to male vga cable and it auto switched the resolution to 1360x768 and everything was displaying correctly. The text is slightly blurry, but I can fix that. Is there any other way to get HDMI to display the image correctly?

Thanks for your help
-The King

---

### Post by papibe on 2010-07-03
I'm glad you're getting closer. Some blurriness is expected since most TVs are better playing movies than displaying text (although adjusting the TV's sharpness control works wonders).

Looks like your TV has a unique timing/modeline. The best solution would be to find it some how, so you can use the TV's native resolution. Unfortunately, I wouldn't know how to help you there. Try google some combination of the terms "Sylvania", "lc220ss1", "1366x768", and "modeline". You're looking for something like this (but specifically for yout TV!):

```
Modeline "1360x768" 85.500 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync
```

In the case you used the hdmi cable and got black borders: You can fix that on the TV side by adjusting the way the signal is displayed. In the case of my Sony, it's under Display -> Display Area. When resolutions match perfectly you can use "Full Pixel". if not, I would use "Normal" or "-1".

I hope it helps.
Regards.

---


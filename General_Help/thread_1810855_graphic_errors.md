---
title: "graphic errors"
date: 2011-07-23
forum: General Help
---

### Post by Keypel on 2011-07-23
Anyone else getting these graphic errors? Anything that is black or white gets replaced with whatever is in the video ram. Hard to explain, here is a video:

[http://www.youtube.com/watch?v=MYar47Hfb28](http://www.youtube.com/watch?v=MYar47Hfb28)

I would have used screen capture software but these graphic errors can't not be captured so I had to use a beat up camera instead.

I have a zotac ion itx-b-e mother board with on board nVidia video.

This happens on both 10.04 and 10.10 however it happens more often and more severe on the 10.10. I have a dual boot and does not effect Windows.

---

### Post by UCSBGauchosRock on 2011-07-23
> **Keypel said:**
> Anyone else getting these graphic errors? Anything that is black or white gets replaced with whatever is in the video ram. Hard to explain, here is a video:

[http://www.youtube.com/watch?v=MYar47Hfb28](http://www.youtube.com/watch?v=MYar47Hfb28)

I would have used screen capture software but these graphic errors can't not be captured so I had to use a beat up camera instead.

I have a zotac ion itx-b-e mother board with on board nVidia video.

This happens on both 10.04 and 10.10 however it happens more often and more severe on the 10.10. I have a dual boot and does not effect Windows.

It looks like you have accessibility features enabled. It looks like that is the virtual keyboard in ubuntu on the background on your browser. If you have compiz config settings manager installed, open it and disable "Opacity, Brightness, and Saturation", and "Opacify" under Accessibility and see if that fixes the problem. Additionally in "Startup Applications" disable the visual assistance option and reboot.

---

### Post by Keypel on 2011-07-23
haha no, that was a typing game I was playing last. Anything white or black gets replaced with what was last stored in ram.

Here is a screen shot of me replying to you. 

[[IMG]http://img146.imageshack.us/img146/6629/dscn6639444.th.jpg[/IMG]](http://img146.imageshack.us/img146/6629/dscn6639444.jpg)


As you can see I was last viewing youtube.



--

---

### Post by UCSBGauchosRock on 2011-07-23
oh sorry about that. I couldn't quite tell from the video. Did you try disabling Opacify and the Accessibility features?

---

### Post by Keypel on 2011-07-24
I didn't have ccsm installed but I did uncheck Accessibility features from startup.

I kind of have a feeling this will not fix it but I will try it and report back.

The only 2 temp fixes I have found:

-Logout Gnome
-Reboot

Like I said before, I have a dual boot so if I boot into a real WinXP no problems occur however a "virtual box WinXP" displays the same graphical errors.

Once apon a time, this never happen. Then a few months ago (maybe 6?) an update came down and then this problem. One solution would be a fresh 10.04 or 10.10 install and then turn off all updates. I'm not sure if that's a good fix. Or I could try isolating the update but after a fresh install I would have no way of telling out of the 500 updates, which one is the problem.

I've tried many fresh installs, different versions, and updating the nvidia drivers.


--

---


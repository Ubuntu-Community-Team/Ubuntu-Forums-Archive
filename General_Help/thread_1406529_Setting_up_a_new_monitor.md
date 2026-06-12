---
title: "Setting up a new monitor"
date: 2010-02-14
forum: General Help
---

### Post by DeMus on 2010-02-14
Hi all,

My monitor is in the process of making the jump to the after life. This means I will have to get a new one soon. Since it will be a larger one in size and resolution I need to set it up accordingly.
What do I need to do to setup my new monitor, whatever type it will be?

Some details:

I run Jaunty 64-bit
I have an nVidia 8500GT card with driver version 195.30
Now I use a resolution of 1280 x 1024 (5:4)
My xorg.conf file looks like this:


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


Should I present you more details about my computer don't hesitate to ask. Thanks.

---

### Post by Elfy on 2010-02-14
I just plugged in my new one and it worked fine. You might need to do the resolution you want with nvidia-settings.

I would think the best thing would be to get the monitor and try it.

---

### Post by DeMus on 2010-02-14
> **forestpiskie said:**
> I just plugged in my new one and it worked fine. You might need to do the resolution you want with nvidia-settings.

I would think the best thing would be to get the monitor and try it.

So you think (or now) it will all be very simple to make it work on the desired resolution. As long as the card can handle it of course. Well, I sure hope so.
Thanks for your answer.

---

### Post by underquark on 2010-02-14
Most newer monitors will work; just check that your graphics card supports the native resolution for best results.  I've had a 1280x1024 recently and now a 1920 x 1080 with onboard Nvidia GeForce 8200 with no problems.  If you have a particular monitor in mind then do a search to see if anyone is reporting problems with it.  If you install your monitor and still get problems then post again.

---

### Post by DeMus on 2010-02-14
> **underquark said:**
> Most newer monitors will work; just check that your graphics card supports the native resolution for best results.  I've had a 1280x1024 recently and now a 1920 x 1080 with onboard Nvidia GeForce 8200 with no problems.  If you have a particular monitor in mind then do a search to see if anyone is reporting problems with it.  If you install your monitor and still get problems then post again.

I don't have a monitor in mind yet. The thing with the old one just started so I will look around now for a new one. Any ideas about a good one? Any special brand or type which is better than others?

---

### Post by Elfy on 2010-02-14
With a nVidia 8500GT and a no-name monitor xrandr gives me 

```
xrandr
Screen 0: minimum 320 x 175, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0* 
   1360x768       51.0     52.0  
   1280x800       53.0  
   1280x720       54.0  
   1152x864       55.0     56.0     57.0     58.0  
   1024x768       59.0     60.0     61.0     62.0     63.0  
   960x600        64.0  
   960x540        65.0  
   928x696        66.0  
   896x672        67.0  
   840x525        68.0     69.0     70.0     71.0     72.0  
   832x624        73.0  
   800x600        74.0     75.0     76.0     77.0     78.0     79.0     80.0     81.0     82.0  
   800x512        83.0  
   720x450        84.0  
   720x400        85.0  
   700x525        86.0     87.0     88.0     89.0  
   680x384        90.0     91.0  
   640x512        92.0     93.0     94.0  
   640x480        95.0     96.0     97.0     98.0     99.0    100.0    101.0    102.0  
   640x400       103.0  
   640x350       104.0  
   576x432       105.0    106.0    107.0    108.0    109.0    110.0    111.0  
   512x384       112.0    113.0    114.0    115.0    116.0  
   416x312       117.0  
   400x300       118.0    119.0    120.0    121.0    122.0  
   360x200       123.0  
   320x240       124.0    125.0    126.0    127.0  
   320x200       128.0  
   320x175       129.0  
```

Hope that is of some help.

---

### Post by DeMus on 2010-02-14
> **forestpiskie said:**
> With a nVidia 8500GT and a no-name monitor xrandr gives me 

```
xrandr
Screen 0: minimum 320 x 175, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       50.0* 

```

Hope that is of some help.

When I do that it gives me:
```
xrandr
Screen 0: minimum 320 x 175, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      50.0*    51.0     52.0  
```

Does this mean the maximum resolution given here is the standard resolution of the connected monitor? I saw at the nVidia site my card should be able to go up to 1920 x 1200. So I guess there is not a problem here.

Thanks all for your answers.

---

### Post by efflandt on 2010-02-14
I haven't been able to find anything definite about maximum in xrandr represents or how much video RAM you need for resolutions, but I think it is either the current maximum of your display, or virtual desktop if set larger.  For example when I change the resolution on an old laptop for an external display, maximum changes.  But another laptop with integrated Intel video always shows maximum 4096 x 4096.

Your video card has either 256 MB or 512 MB video RAM and I have no trouble doing 1080p (1920x1080) DVI to HDMI on a different brand with 256 MB.

If you use a digital connection (DVI or HDMI), you may need to temporarily disable "splash" as a boot parameter until settings in /etc/usplash.conf match native resolution of the new monitor.  X should automatically use best resolution for DVI or HDMI unless something in your xorg.conf limits that.

If connected with VGA, you might need to make other adjustments to get optimum resolution (not sure how nVidia drivers handle things).

---

### Post by Easy Limits on 2010-02-14
I just upgraded my monitor from a 19" Viewsonic to a 24" Asus.  I was worried about the resolution with my older video card GeForce 7300 GS not being able to do the newer higher resolutions of the new monitor.  Well, I plugged in the new monitor and it worked great.  Plug and Play

---

### Post by DeMus on 2010-02-14
> **Easy Limits said:**
> I just upgraded my monitor from a 19" Viewsonic to a 24" Asus.  I was worried about the resolution with my older video card GeForce 7300 GS not being able to do the newer higher resolutions of the new monitor.  Well, I plugged in the new monitor and it worked great.  Plug and Play

Now that is what I wanted to read. Thank you. Now I only hope for me it will also be that simple.

---

### Post by DeMus on 2010-02-20
Okay, I just bought a 23" Samsung Syncmaster P2370 because the old LCD screen died this morning, may he rest in peace.

I had a resolution of 1280 x 1024 but once I connected the new screen the resolution changed automatically to 1920 x 1080. No drivers needed, no settings changed by hand, everything just worked. Thank you Ubuntu.
Thank you all for your advice and help.

---


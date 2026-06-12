---
title: "Stuck in 59.93 Hz refresh rate. Want 75, it should be possible."
date: 2009-09-27
forum: General Help
---

### Post by cooolr on 2009-09-27
Hey everyone. I'm trying to get a higher refresh rate on my **LG W2442PA-BF **monitor but I'm new to linux and don't know how to.
It should be possible but it isn't letting me.

 I found these specs for my monitor:
[IMG]http://images.tigerdirect.ca/main/gfx-blkbullet.jpg[/IMG]                          Vertical Refresh Rate:                           56-75Hz   [IMG]http://images.tigerdirect.ca/main/pixel-clr.gif[/IMG] [IMG]http://images.tigerdirect.ca/main/pixel-clr.gif[/IMG]   [IMG]http://images.tigerdirect.ca/main/pixel-clr.gif[/IMG]   
[IMG]http://images.tigerdirect.ca/main/gfx-blkbullet.jpg[/IMG]                          Horizontal Frequency:                           30-83kHz
What would be the best way to change it?
I have an nvidia 8800 gt graphics card if that helps.

---

### Post by t0p on 2009-09-27
I suggest use of **grandr**.

Install grandr

```
sudo apt-get install grandr
```

Run it with the command:

```
grandr
```The resolution and refresh rate you desire should appear in the list if available.

---

### Post by cooolr on 2009-09-27
> **t0p said:**
> I suggest use of **grandr**.

Install grandr

```
sudo apt-get install grandr
```Run it with the command:

```
grandr
```The resolution and refresh rate you desire should appear in the list if available.

oh darn so the highest refresh rate I can have with my resolution at 1920 x 1080 is 50 HZ, isn't that kinda bad? 

I don't play a lot of games but that still is horrible for browsing. What a rip off, I'm turning this back in and buying something more costly.

---

### Post by fragos on 2009-09-27
It's my understanding that refresh rate was more important with CRTs because the pixel persistence was very short. Faster refresh gave a better image and slower gave a pulsating effect. LCDs aren't as fast as CRTs and a rate of 60 HZ gives good visual performance.

---

### Post by CatKiller on 2009-09-28
> **cooolr said:**
> oh darn so the highest refresh rate I can have with my resolution at 1920 x 1080 is 50 HZ, isn't that kinda bad?

Presumably you're using the proprietary nVidia driver then? You're refresh rate isn't 50. The nVidia driver deliberately mis-reports the refresh rate. The nvidia-settings tool will tell you what the refresh rate actually is.

Refresh rates are pretty meaningless on LCD monitors - there is no full-screen refresh. Some monitors won't accept a signal that's higher than 60 Hz, though, and so the nVidia driver sometimes limits the timing of the signal. From the driver documentation:

>        o "AllowNon60HzDFPModes": some lower quality TMDS encoders are only
         rated to drive DFPs at 60Hz; the driver will determine when only 60Hz
         DFP modes are allowed. This argument disables this stage of the mode
         validation pipeline.


So you could use ```
        Option          "ModeValidation"               "AllowNon60HzDFPModes"
```in the Device Section to turn off this feature.

---

### Post by trodas on 2009-10-03
> Refresh rates are pretty meaningless on LCD monitors - there is no full-screen refresh.

That is only partly true. In games you need your refreshrate as high, as you can get. Also scrolling is way nicer in 75Hz that in 60 - God forbid 50Hz...

So, AllowNon60HzDFPModes it is? Great to know Linux users find a solution for this problem.

Now let's hope I can find a way to fix this problem in Windows too...

I reasonably believe that since the 5600XT can do 2048x1538 pixels in 80Hz refresh, then it sure can do 1280x1024 in 75Hz. eVGA says 5600XT it can do 150Hz in 1280x1024:
[www.evga.com/products/pdf/N317.pdf](www.evga.com/products/pdf/N317.pdf)

As the Linux solution suggest, the drivers cap the refreshrate to 60Hz, because they detect "some lower quality TMDS encoders are only rated to drive DFPs at 60Hz"... But since the very same TMDS encoder can give me output resolution of 2048x1538 pixels in 60Hz refresh, then sure as hell it can give me 1280x1024 in 75Hz. As on Linux :)

Now the question is only how to duplicate the Linux nVidia drivers option "AllowNon60HzDFPModes". Anyone can shred some light at this?

I, personally, see only two ways.
1) change/patch/modify the drivers somehow to allow the non 60Hz DFP modes even on 5600XT card
2) change/patch/modify the GFX card bios to not report lower quality TMDS encoder, thus allowing drivers to set up higher refreshrates

Now let's find some Windows geek who will insist that Winblows are superior over Linux and can't stand that Linux users can push the TMDS encoder harder that Windows users :)

And I was drawn to this and similar threads because I would like to have more that 60Hz refresh using FX 5600XT card on BenQ FP75G monitor, what can do 76Hz in 1280x1024 anyway:

[IMG]http://i37.tinypic.com/25qy93r.jpg[/IMG]



However nVidia drivers (and not only my lovely old 45.48) see it that way - Forceware 53.03 WHQ:

[IMG]http://i36.tinypic.com/2mzabsl.jpg[/IMG]

Forceware 81.95 WHQ:

[IMG]http://i33.tinypic.com/13zr8nr.jpg[/IMG]

...even in low resolution...  Simply as Gates once put it - 640k should be plenty for everybody - 60Hz seems to be fine for everybody.

Yet some complain! :)

---


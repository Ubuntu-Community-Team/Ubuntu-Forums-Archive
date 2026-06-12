---
title: "refresh rate in 12.04 LTS (irregular)"
date: 2012-05-26
forum: General Help
---

### Post by scottsdale on 2012-05-26
Hello, and thanks for looking at my thread - this is a great community.

I have used the search function and haven't found a solution to put my refresh woes to rest.

I am using proprietary nvidia driver 295.53 (because otherwise I cannot run dual screen).

I am keeping the other screen unplugged for now though until I get the refresh rate worked out on my CRT monitor (Viewsonic UltraBright A91f+).

I think my problem is somehow stemming from the fact that I am using a DVI to VGA connector. So my monitor settings are not being picked up.

When i try "xrandr -r 72" in the terminal i get.

"Rate 72.0 Hz not available for this size"

I have a pretty much blank xorg.conf

I cannot select any other refresh rates besides 60hz in the Nvidia X Server settings nor Ubuntu Systems settings. 

I could run this monitor at 80hz on windows although I only need 72 to not be bothered by flicker. I know that it is also capable of other resolutions but I am mostly concerned about refresh rate at the moment. 

I have a Nvidia 8600GT with dual DVI


Please let me know if there is any info commands you need me to post to understand what is happening on this machine.

---

### Post by haittah on 2012-05-26
This might help (it helped me and I have the same card as u do). This is no real solution, more workaround, but saves me from changing my refresh rate every time I restart computer.
> 
*        I found this thread by googling after I had a similar problem. I wanted to add the comment that for someone who just wants to keep a good refresh rate on their CRT, the easiest solution seems to be to add the option line:
**Option "IncludeImplicitMetaModes" "false"**
to the device section for their nvidia card. This basically causes the driver to only use the modes defined in the xconfig instead of doing what it pleases.


Taken from: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/89640/comments/7](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/89640/comments/7)
So u need to modify xorg.conf:                                    
```
sudo gedit /etc/X11/xorg.conf

```by adding the line under section "Monitor" 

```
Option "IncludeImplicitMetaModes" "false"
```


P.S.
> 
I have a pretty much blank xorg.conf
nvidia settings offer u posiblity to save ur xorg.conf

---

### Post by scottsdale on 2012-05-26
Your post has me headed in the right direction because I had to research how to get nvidia to save my settings to xorg (it was parse erroring before)

However,

I added the line you suggested saved and rebooted.

Still cannot set a refresh rate other than 60 though.

xrandr still says not available for this size when I try 72 (its capable though) and I don't see anywhere in nvidia to change it either.

---

### Post by haittah on 2012-05-26
When you change the nvidia settings, for example refresh rate, does it keeps settings till the next reboot? I suppose it does, but I had to ask just to make sure that u did everything according to the tutorial that isn't that clear.

What I did was this:
1. After boot set up my prefered nvidia settings and saved them
2. Saved the xorg.conf
3. Added the line and rebooted
4. After reboot, my screen didn't hurt my eyes and I knew it worked.

xrandr is entirely different case, the CRT monitor issue isn't by any means fixed, so you will not have option to choose preferred refresh rate. Mine still says 55 as the highest available option.But, the line u added will tell your computer to load nvidia settings and not xrandr ones. I am noob in this area but this is how I understood this problem. Hope it helps.


[IMG]http://img835.imageshack.us/img835/6093/screenshotfrom201205262.png[/IMG]

---

### Post by scottsdale on 2012-05-26
Thanks for taking so much time to help me.

So when I go into nvidia settings and select any resolution above 800x600 my only refresh rate option is 60. However when I select 800x600 (or lower) I am given 72hz as an option.

This monitor is **definitely** capable of 72hz for 1024x768. - Ive used it with windows for years at 1280x1024 @ 75hz with no problems.

I suspect that ubuntu may not like my dvi to vga adapter?

I'm pretty stumped.

---

### Post by scottsdale on 2012-05-27
After 2 weeks of trying I finally gave up like everyone else and bought a newer high end gaming monitor with DVI. 

I will miss my CRT dearly

But at least now I don't have to worry about the whole refresh rate thing :)

---

### Post by haittah on 2012-05-27
Sorry i couldn't help u keep the trusty CRT :) best wishes with the new one! ):P

---


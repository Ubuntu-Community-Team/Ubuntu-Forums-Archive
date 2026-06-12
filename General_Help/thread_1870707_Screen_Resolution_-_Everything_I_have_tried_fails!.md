---
title: "Screen Resolution - Everything I have tried fails!"
date: 2011-10-27
forum: General Help
---

### Post by tman69 on 2011-10-27
Here is the Reader's Digest version of a couple weeks of trying:

A full install of Ubuntu 11.10 with an Nvidia 8800GTS video card connected to an older 51" 1080i rear projection TV through the on-board S-Video (actually it is an adapter which looks like S-Video on the card side but goes out to R,G, B cables). The max resolution it is showing is 1024x768 which makes it so the side and top bars are not visible.

Here are some of the steps I have tried:

```

cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync 

 xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr: Failed to get size of gamma for output default


xrandr --addmode default 1920x1080_60.00


```

I was able to get the 1920x1080 to show under System Settings > Display but when I attempted to set it to that it gave an error about the virtual screen size. I then added a line to /etc/X11/xorg.conf under the Display section for Virtual 2048 2048. Then I logged off and logged back in again and tried setting it to the 1920x1080 again and received the following error:


The selected configuration for displays could not be applied

could not set the configuration for CRTC 351


Of all the things I have tried I have never had the correct resolution show up under the nvidia-settings GUI. I have also never been able to get it to switch to the correct resolution.

It does seem that before logging in the display is at the correct resolution but I can't be certain.

Please...any help is much appreciated as I have been fighting with this for weeks! I can try to provide any additional information you need. Also and I am not certain if it is related by Firefox crashes every time it is opened and I think it is related to screen position.

Thanks

---

### Post by papibe on 2011-10-28
I've never been able to get more than 1024x768 on a S-Video connection. That's an analog connection, may be 1080i would work?

Just a thought,
Regards.

---

### Post by tman69 on 2011-10-28
It isn't actually S-Video it is an Nvidia proprietary connection. As mentioned when the machine boots before putting in my password it appears to be at a higher more acceptable resolution. The 1024x768 resolution is unacceptable as the top and side bars are not visible.

---

### Post by tman69 on 2011-10-28
Anyone? I know there must be people out there that have experienced this issue and know how to fix it. I would imagine it is something simple that I am missing but as I said I have tried everything I can find and still no luck. I could really use the help of someone who knows what they are doing!
 
Thanks

---

### Post by Blaqksheep on 2011-10-28
Yup, it's your connection, not your GPU/drivers, TV, or computer.

[quote="Wikipedia"]S-Video carries standard definition video (typically at 480i or 576i resolution), but does not carry audio on the same cable.[/quote]

The gist is S-Video and the triple RCA it becomes can only output in VGA resolutions (4:3 aspect).  The default and standard for the cable is VGA (640x480) but it can handle the image stretched up to XGA (1024x768).  DVI will let you output in the proper 16:9 aspect for your TV, even if you have to convert it to HDMI.  You can read more [here](http://en.wikipedia.org/wiki/S-video), [here](http://en.wikipedia.org/wiki/480i), and get your knowledge on [here](http://en.wikipedia.org/wiki/Vga).

You should be using one of those shiny DVI ports.  If your TV doesn't support it, I'm darn sure it'll support HDMI.  You can get a DVI to HDMI converter for cheapies these days, but you'll have to find a different solution for your audio output.  Sorry.

---

### Post by tman69 on 2011-10-28
> **Blaqksheep said:**
> Yup, it's your connection, not your GPU/drivers, TV, or computer.



The gist is S-Video and the triple RCA it becomes can only output in VGA resolutions (4:3 aspect).  The default and standard for the cable is VGA (640x480) but it can handle the image stretched up to XGA (1024x768).  DVI will let you output in the proper 16:9 aspect for your TV, even if you have to convert it to HDMI.  You can read more [here](http://en.wikipedia.org/wiki/S-video), [here](http://en.wikipedia.org/wiki/480i), and get your knowledge on [here](http://en.wikipedia.org/wiki/Vga).

You should be using one of those shiny DVI ports.  If your TV doesn't support it, I'm darn sure it'll support HDMI.  You can get a DVI to HDMI converter for cheapies these days, but you'll have to find a different solution for your audio output.  Sorry.

I took your advice and switched to a DVI-HDMI cable and it does now recognize the higher resolutions. The problem is I still am unable to see the launcher and the top menu bar. No matter which resolution I select the launcher and top menu stay off the screen. Do you have any idea on how I can correct this? Perhaps set some sort of offset or something?

---

### Post by papibe on 2011-10-28
May be you are suffering from another problem: [Overscan]("http://en.wikipedia.org/wiki/Overscan")

If so, you have 2 options to solve it:

First (recommended): Some TV's have the ability to set how the signal is reproduced. In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Play with the options available on your TV, may be the option is not easy to see. Check your manual or research about it on the Internet.

Second: the 'Nvidia X Server Settings' has an option to correct overscan manually. Check [this]("http://www.ypass.net/blog/2010/04/nvidia-overscan-correction-fixed-in-latest-drivers/") article.

Tell us how it goes,
Regards.

---

### Post by tman69 on 2011-10-28
> **papibe said:**
> May be you are suffering from another problem: [Overscan]("http://en.wikipedia.org/wiki/Overscan")

If so, you have 2 options to solve it:

First (recommended): Some TV's have the ability to set how the signal is reproduced. In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Play with the options available on your TV, may be the option is not easy to see. Check your manual or research about it on the Internet.

Second: the 'Nvidia X Server Settings' has an option to correct overscan manually. Check [this]("http://www.ypass.net/blog/2010/04/nvidia-overscan-correction-fixed-in-latest-drivers/") article.

Tell us how it goes,
Regards.

THANKS!!! I had figured out it was an overscan issue but my TV didn't have a way to adjust but the Nvidia-Settings for me did have the option just like the link showed!

THANK YOU SO VERY MUCH!!!!

---

### Post by papibe on 2011-10-28
:P Glad it's working. Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

Regards.

---

### Post by dr_james2k on 2011-12-04
Wow, I've been battling with overscan for a while with my set up (Philips Aquos as a 2nd monitor with a Nvidia 9600 GT through a DVI to HDMI cable).

This does the job perfectly, Can't believe I never noticed that slider before.

---


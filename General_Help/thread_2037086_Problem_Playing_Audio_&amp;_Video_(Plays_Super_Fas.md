---
title: "Problem Playing Audio &amp; Video (Plays Super Fast)"
date: 2012-08-03
forum: General Help
---

### Post by jmooney5115 on 2012-08-03
Hello. My problem is that all local/streaming audio and video plays about 4x speed. This computer isn't but a week old. I am running a [Radeon HD 6750]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814161379"), which has OpenGL 4.1 support. I've installed everything I can think of. Have tried Mint, Kubuntu, and Ubuntu. Windows is not an option.

ATI binary X.Org driver wan't installed until after I tried the manufacturers driver.

What I have tried:
[LIST=1]
[*]OpenJDK Java 6(and 7) Runtime
[*]Default Ubuntu Driver
[*]Manufacturers Driver
[*]ATI binary X.Org driver (Optimized hardware acceleration of OpenGL with newer ATI Graphics cards
[*]Streaming audio/video
[*]Local audio/video
[/LIST]

I need to get this worked out. Any ideas?

Edit: Ubuntu v12.04 32-bit LTS
Kernel: 3.2.0-27-generic-pae

---

### Post by Dylan1473 on 2012-08-03
What happens if you play directly with mplayer? Open a terminal and type
```

mplayer [FILENAME/PATH TO FILE]

```

e.g. to play video.avi in your home directory

```

cd ~
mplayer video.avi

```

---

### Post by jmooney5115 on 2012-08-03
Dylan1473: Thanks for the reply.

**New Problem**
The driver I had installed when I first posted this was the one through 'Additional Drivers'. Just after I posted this I installed the one from AMDs website. Now I can watch 1080p YouTube videos perfectly and I get audio through the HDMI. But this driver introduced two new problems:

[LIST=1]
[*] I cannot add a second monitor, when I apply the settings for the second monitor I get an error: ```
requested position/size for CRTC 72 is outside the allowed limit: position=(1920, 0), size=(1440, 900), maximum=(1920, 1920)
```

I click ok and another error window is shown saying:```
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: requested position/size for CRTC 72 is outside the allowed limit: position=(1920, 0), size=(1440, 900), maximum=(1920, 1920)
```

[*]When moving windows, the screen is very slow to refresh and it basically flickers.

[*]My main monitor is a 24" 1080p television. It is set to 1920x1080 but the screen is shrunk, there is about 1/2" black bar around the entire display. I also tried 1440x900 and the blackness persists.
[/LIST]

Image Description: You can see where the flash hits the bezel of the monitor and where the screen image starts. There is black space there.

Edit: Drive I'm using:  AMD Catalyst(TM) Proprietary Driver-8.98

---


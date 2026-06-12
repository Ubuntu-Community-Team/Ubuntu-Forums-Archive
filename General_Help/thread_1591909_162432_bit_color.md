---
title: "16/24/32 bit color"
date: 2010-10-10
forum: General Help
---

### Post by bradleyshorwith on 2010-10-10
Hello. I am having a little trouble here. The system I have supports a maximum of 24 bit color in Windows. I am only able to get 16 bit color here.
As I understand, 32 bit color in Windows is 24 bit color in Linux, so what is the Linux equivalent of 24 bit color in Windows and how would I switch to it? I am asking because there is a noticeable difference between 16 bit (terrible) and 24 bit (better).
Any help would be greatly appreciated.

---

### Post by DeMus on 2010-10-10
> **bradleyshorwith said:**
> Hello. I am having a little trouble here. The system I have supports a maximum of 24 bit color in Windows. I am only able to get 16 bit color here.
As I understand, 32 bit color in Windows is 24 bit color in Linux, so what is the Linux equivalent of 24 bit color in Windows and how would I switch to it? I am asking because there is a noticeable difference between 16 bit (terrible) and 24 bit (better).
Any help would be greatly appreciated.

24 bits is still 24 bits. Windows uses 32 bits but also that is only 24 bits of color information. You have 3 bytes, of 8 bits each, making 24bits color info.
The last 8 bits is used for light and dark I believe. I must admit watching colors in Windows is nicer than in Linux. So maybe we have to start using the last 8 bits as well.

---

### Post by mcduck on 2010-10-10
> **DeMus said:**
> 24 bits is still 24 bits. Windows uses 32 bits but also that is only 24 bits of color information. You have 3 bytes, of 8 bits each, making 24bits color info.
The last 8 bits is used for light and dark I believe. I must admit watching colors in Windows is nicer than in Linux. So maybe we have to start using the last 8 bits as well.

The last 8 bits would be the alpha channel (transparency) but that's pointless when talking about display colors (your display can't become transparent!), which is the reason why the highest color mode Linux uses is called 24 bits. (claiming to use 32-bit colors for display would be a lie, really) I suppose the guys at Microsoft just thought that calling it 32-bit colors would sound better or something like that, it still only contains 24 bits of data that the display can use.

32-bit colors are only relevant when talking about image colors, and even then only if you are using an image format that supports alpha channel. The amount of displayed colors is exactly the same as with 24-bit colors.

If you feel that you get better colors in Windows than in Linux I recommend doing some color calibration for your display first, and if that doesn't help then it's probably your graphics card's drivers that are to blame.

---

### Post by mcduck on 2010-10-10
> **bradleyshorwith said:**
> Hello. I am having a little trouble here. The system I have supports a maximum of 24 bit color in Windows. I am only able to get 16 bit color here.
As I understand, 32 bit color in Windows is 24 bit color in Linux, so what is the Linux equivalent of 24 bit color in Windows and how would I switch to it? I am asking because there is a noticeable difference between 16 bit (terrible) and 24 bit (better).
Any help would be greatly appreciated.

What graphics card are you using, and have you already installed drivers for it (if it's a fairly new Ati or nVidia card)?

If you have, then all you can do is create xorg.conf -file in /etc and define your display settings there. (latest Ubuntu verions don't have such file by default any more, and instead try to automatically detect everything, but if you create the file it will be used)

---

### Post by bradleyshorwith on 2010-10-10
> **mcduck said:**
> The last 8 bits is used for light and dark I believe. I must admit  watching colors in Windows is nicer than in Linux. So maybe we have to  start using the last 8 bits as well. 
That doesn't explain why my Ubuntu display looks like Windows 16 bit, while Windows 24 bit is noticeably better.
 
> **mcduck said:**
> What graphics card are you using, and have you  already installed drivers for it (if it's a fairly new Ati or nVidia  card)?

If you have, then all you can do is create xorg.conf -file in /etc and  define your display settings there. (latest Ubuntu verions don't have  such file by default any more, and instead try to automatically detect  everything, but if you create the file it will be used)
 My graphics are onboard graphics for a Pentium III board.

> **mcduck said:**
> The last 8 bits would be the alpha channel (transparency) but that's pointless when talking about display colors (your display can't become transparent!), which is the reason why the highest color mode Linux uses is called 24 bits. (claiming to use 32-bit colors for display would be a lie, really) I suppose the guys at Microsoft just thought that calling it 32-bit colors would sound better or something like that, it still only contains 24 bits of data that the display can use.

32-bit colors are only relevant when talking about image colors, and even then only if you are using an image format that supports alpha channel. The amount of displayed colors is exactly the same as with 24-bit colors.

If you feel that you get better colors in Windows than in Linux I recommend doing some color calibration for your display first, and if that doesn't help then it's probably your graphics card's drivers that are to blame.
Think of a color gradient that should be smooth. Then make the gradient blocky with rough edges, and apply that to everything. You'll get the color quality I have by default in Ubuntu or with 16bit selected in Windows.

Thanks for all the help everyone.

---

### Post by dcstar on 2010-10-10
> **DeMus said:**
> 24 bits is still 24 bits. Windows uses 32 bits but also that is only 24 bits of color information. You have 3 bytes, of 8 bits each, making 24bits color info.
The last 8 bits is used for light and dark I believe.
.......
No, they are just not used at all.

The human eye cannot differentiate 24-bit colour, so it would be a pointless waste of processing power and other resources to do full 32-bit but since data sections in modern computers use multiples of 16 bits then 32-bit is the next step up from 16-bit, but only 24-bits of data is ever used (or needed).

---

### Post by DeMus on 2010-10-10
mcduck,

I have an nvidia 8500GT card with 512MB ram and the 260.19.06 driver on the 64 bits version of 10.04.
When I see an large area which slowly changes in color I can see the different colors very clearly. The transition is not smooth, just as what the OP says when you use 16-bits colors. I use the 24-bits settings, still it is not as good as it used to be when I still used Windows several years ago. That's a shame. I have used several Ubuntu's so it's not only one, I have used several mediaplayers, 2 monitors (last one Samsung SyncMaster P2370 full HD), several drivers along the way. The videocard itself is not the best nvidia has made but it most certainly is not bad. So what can this be?
I could install Windows again to see if there still is a difference but I don't like to do that. I'm Windows free and would like to stay that way.
Any ideas what we could check to see what's going on?
Thanks.

---

### Post by HermanAB on 2010-10-10
If there is a difference between Windows and Linux, then your video device driver is to blame.

---

### Post by bradleyshorwith on 2010-10-10
Just to clear things up, the menu items in Windows under color in XP were 16 bit and 24 bit I have used other more powerful systems running XP and 32 bit is shown as an option. I cannot, however, compare 24 and 32 bit since I have not been able to see them long enough side by side.
@dcstar: I notice a HUGE difference between the two.

---

### Post by mcduck on 2010-10-10
> **DeMus said:**
> mcduck,

I have an nvidia 8500GT card with 512MB ram and the 260.19.06 driver on the 64 bits version of 10.04.
When I see an large area which slowly changes in color I can see the different colors very clearly. The transition is not smooth, just as what the OP says when you use 16-bits colors. I use the 24-bits settings, still it is not as good as it used to be when I still used Windows several years ago. That's a shame. I have used several Ubuntu's so it's not only one, I have used several mediaplayers, 2 monitors (last one Samsung SyncMaster P2370 full HD), several drivers along the way. The videocard itself is not the best nvidia has made but it most certainly is not bad. So what can this be?
I could install Windows again to see if there still is a difference but I don't like to do that. I'm Windows free and would like to stay that way.
Any ideas what we could check to see what's going on?
Thanks.

If you are sure you are using 24-bit colors, then I have no idea what could be your problem. But it definitely isn't color depth. Perhaps a bad Gamma setting? That would easily result in bad-looking colors and transients...

Like already said, 24-bit colors give you 8 bits per each color channel, red, green and blue, with the total of 32M different colors. Which is exactly the same amount of colors Windows gives you in "32-bit" color mode. And actually that's a lot more than you can reasonably expect your display to be able to handle (most TN panels actually only handle 6 bits per color channel, and have to do color dithering to give you the impression of being able to show 16777216 colors instead of the 262144 the panel is really capable of).

Also large-area color transients are a bit tricky, as the amount of possible colors to use in the transient depend on what colors you use. In worst case you only have 256 colors that can be used (in case it's a monochrome transient). So computer-generated transients tend to always easily show visible separation between color shades, especially on larger images. Dithering the colors helps a lot, but not all graphics apps do this automatically, often it's an option in the save dialog. (photographs are less of a problem, you could say that the way cameras and film/sensors work they are "naturally dithered" already so you never see such pure transients in photos.)


...and then the required Wikipedia quote about 32-bit colors:
> 
32-bit color

It is generally a misnomer in regard to display color depth. While actual 32-bit color at ten to eleven bits per channel produces over 4.2 billion distinct colors, the term &#8220;32-bit color&#8221; is most often a misuse referring to 24-bit color images with an additional eight bits of non-color data (I.E.: alpha, Z or bump data), or sometimes even to plain 24-bit data.

[http://en.wikipedia.org/wiki/Color_depth]("http://en.wikipedia.org/wiki/Color_depth")

---

### Post by DeMus on 2010-10-10
Thank you for all the info. I'm convinced now that we "only" have 24-bits. Still I'm having the transients in colors but apparently I have to live with that.
Thanks again.

---

### Post by formaldehyde_spoon on 2010-10-10
> **bradleyshorwith said:**
> Just to clear things up, the menu items in Windows under color in XP were 16 bit and 24 bit I have used other more powerful systems running XP and 32 bit is shown as an option. I cannot, however, compare 24 and 32 bit since I have not been able to see them long enough side by side.
@dcstar: I notice a HUGE difference between the two.
There is no need to compare "32 bit colour" and "24 bit colour".  What people here are trying to say is that these are one and the same.  32 bit colour is in fact just a slightly inaccurate name for 24 bit colour - there is no difference.

---

### Post by mcduck on 2010-10-10
> **DeMus said:**
> Thank you for all the info. I'm convinced now that we "only" have 24-bits. Still I'm having the transients in colors but apparently I have to live with that.
Thanks again.

Visible transients could be caused by something else than the color depth. And that's assuming the color depth really *is* 24-bit. If you have a separate monitor you could probably check the current bit depth directly from the monitor itself. Bit hard to do if you use a laptop, though. :)

It's hard to say, really, without seeing what it looks like. But the point really was just that 24-bits is as much as you can get apart from some really, really expensive professional displays. And that the "32-bit Truecolor" mode in Windows really is just the same 24 bits as in 24-bit color mode on Linux. And in the end many consumer-level LCD panels really display only 18-bit colors. :)

---

### Post by bradleyshorwith on 2010-10-23
I'm replying to this message again. I hope I state it more clearly now. My PC only supports up to 24 bit color in Windows XP. However, when I use Ubuntu, the highest color depth I can get is the equivalent of 16 bit in Windows. There is a HUGE difference between the two and Windows 16 bit is almost unbearable to look at. Is there a way to change the color depth? I am sorry to revive the thread, but my problem has not been solved and I have no idea what to do.

---

### Post by dcstar on 2010-10-23
> **bradleyshorwith said:**
> I'm replying to this message again. I hope I state it more clearly now. My PC only supports up to 24 bit color in Windows XP. However, when I use Ubuntu, the highest color depth I can get is the equivalent of 16 bit in Windows. There is a HUGE difference between the two and Windows 16 bit is almost unbearable to look at. Is there a way to change the color depth? I am sorry to revive the thread, but my problem has not been solved and I have no idea what to do.

Until you take the advice of the other posts and provide the details of your video hardware, then it probably won't ever get resolved.

---

### Post by mister_playboy on 2010-10-23
> **bradleyshorwith said:**
> but my problem has not been solved and I have no idea what to do.


We need to know what your video hardware is. Run ```
lspci
``` from the terminal and post the output.

---

### Post by bradleyshorwith on 2010-10-24
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
**00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)**
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
02:09.0 USB Controller: NEC Corporation USB (rev 41)
02:09.1 USB Controller: NEC Corporation USB (rev 41)
02:09.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
02:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

Sorry, I didn't really know what my video hardware was, just that it is onboard.

---

### Post by bradleyshorwith on 2010-10-25
I gave the output. Is there anything else I should be doing? Sorry for bumping but I really need help here.

---

### Post by 3Miro on 2010-10-25
I looked for your hardware on the Intel site. This is something ancient indeed. Back in 2000 there was no FOSS driver for your video card and the thing apparently came with couple of proprietary drivers in the form of RPM files. They are compiled for kernel 2.4 (or maybe even 2.2) and will not work on any modern system. Intel no longer supports the video card and since the driver is not open source the community cannot update it either. What you are using is some generic driver that works, but only so well.

You may try tweaking the xorg.conf settings to try and force the video card to do what you want. Here is something else that found for very similar to your hardware.
[http://www.linuxquestions.org/questions/linux-general-1/xorg-conf-for-intel-82815-chipset-608658/](http://www.linuxquestions.org/questions/linux-general-1/xorg-conf-for-intel-82815-chipset-608658/)

Other than that, things are not looking good.

(On the note of the video + driver, I had an EVGA 7300GT, worked OK under windows, but was ugly as hell under Ubuntu. Then the fan died after only a year, so the thing was a piece of garbage apparently. I moved to Asus 8600GT and I got huge improvement under both systems.)

---

### Post by bradleyshorwith on 2010-10-25
It seems I am having a bit of a hard time finding xorg.conf. Here is the output when I use the locate command.
> /usr/share/X11/xorg.conf.d
/usr/share/X11/xorg.conf.d/10-evdev.conf
/usr/share/X11/xorg.conf.d/50-synaptics.conf
/usr/share/X11/xorg.conf.d/50-vmmouse.conf
/usr/share/X11/xorg.conf.d/50-wacom.conf
/usr/share/X11/xorg.conf.d/51-synaptics-quirks.conf
/usr/share/X11/xorg.conf.d/60-magictrackpad.conf
/usr/share/doc/xserver-xorg-video-nouveau/examples/xorg.conf
/usr/share/man/man5/xorg.conf.5.gz
I expected it to be in /etc/x11/ but I don't really know which one I should modify (or create) now. Thanks, you have been the biggest help so far.

---

### Post by mcduck on 2010-10-26
the correct file would be /etc/X11/xorg.conf, and no, the file doesn't exist on the default install so you need to create it yourself. :)

---

### Post by 3Miro on 2010-10-26
On newer version of Xorg, xorg.conf is the sum total of all the .conf files in xorg.conf.d (directory of xorg.conf). This way you have separate files for the separate sections of xorg.cong that would otherwise have. You should make a new file, like 90-mysettings.conf and do the editing there.

---


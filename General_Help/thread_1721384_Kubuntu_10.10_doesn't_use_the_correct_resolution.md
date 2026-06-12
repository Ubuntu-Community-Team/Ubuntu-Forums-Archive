---
title: "Kubuntu 10.10 doesn't use the correct resolution"
date: 2011-04-04
forum: General Help
---

### Post by Drakmor on 2011-04-04
Hey all, I've looked around and found other people with this problem, but all of the posts were older and didn't work when I tried them. I recently set up Kubuntu for my parents, and its working fine, other than the screen resolution. When I log in, it uses 800x600 when it should be using 1280x1024. I've tried to generate/ edit xorg.conf, but Kubuntu doesn't seem to pay attention to it. Also, I don't know if it matters, but it seems to be detecting a second screen that doesn't exist (see picture). That "monitor" can only go up to 800x600, but when I disabled it, it stayed off. When it was on and I pressed identify monitors, however, it put both labels on the main monitor. 

Here's the picture of the two monitors:
[[IMG]http://farm6.static.flickr.com/5222/5589617464_cced855319.jpg[/IMG]]("http://www.flickr.com/photos/swgamer53/5589617464/")

Thanks!

---

### Post by Zorael on 2011-04-05
It may be that your videocard is always reporting that something is connected to your tv-out port. Then it assumes it can only output 800x600, and when it clones the output to both your monitor and that non-connected TV you end up with that your screen instead of 1280x1024.

You should be able to work around this by making kdm change some display settings before showing the login screen. Hopefully they should transfer to your user sessions then. (Or you could just make a startup script that does this after logging in, if you don't care about the login screen.)

What is the output of **xrandr**, entered in a terminal?

---

### Post by Drakmor on 2011-04-05
Here's the xrandr output.
```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
S-video connected (normal left inverted right x axis y axis)
   800x600        59.9 +
   640x480        59.9  

```
I don't really understand what its saying, but I do know that there's only one screen connected, so I'm not sure why its saying there's two.
I'm fine with either method of fixing the resolution, but as there's multiple use accounts on this computer, it would be nicer if I could just change some of the kdm settings rather than putting a copy of the script in all of the user's home folders.

---

### Post by Zorael on 2011-04-06
All right.

```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
**VGA-0 disconnected** (normal left inverted right x axis y axis)
**DVI-0 connected** 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
*[...]*
**S-video [COLOR="Red"]connected[/COLOR]** (normal left inverted right x axis y axis)
   **[COLOR="Red"]800x600[/COLOR]**        59.9 +
   640x480        59.9  

```

Going by what you pasted, your screen has three *outputs*; **VGA-0**, **DVI-0** and **S-video**. As you can see, it thinks something is connected to S-video, and so it tries to project a cloned screen onto both that output and DVI-0 (which is also connected). As S-video can only go up to 800x600, that's what it ends up as.

Try this in a terminal after logging in and see if it disables S-video and sets your DVI-0 resolution to 1280x1024.
```
$ xrandr --output S-video --off --output DVI-0 --auto
```
If it doesn't change the resolution to 1280x1024, try this instead.
```
$ xrandr --output S-video --off --output DVI-0 --mode 1280x1024
```

Paste your new xrandr output afterwards. If it works, we'll just have to copy and paste it into the proper file.

This can *most likely* be fixed with xorg.conf voodoo; I'm just rusty in that area after not having had to touch it for a good while now. Even better, you can probably set up an udev rule (if your videocard driver permits it), but I'm clueless at that.

---

### Post by Drakmor on 2011-04-06
So, the first option seemed to work- at least, it changed the resolution to the correct one. However, the xrandr output seems the same. 

```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
S-video connected (normal left inverted right x axis y axis)
   800x600        59.9 +
   640x480        59.9  
```

I don't really care about the login screen, so if there's just a way to make all of the accounts run this on login, I'll be happy. Thanks!

---

### Post by Zorael on 2011-04-07
Try adding that line to **/etc/kde4/kdm/Xsetup** so that it looks like this.

```
#! /bin/sh
# Xsetup - run as root before the login dialog appears

#xconsole -geometry 480x130-0-0 -notify -verbose -fn fixed -exitOnFail -file /dev/xconsole &

**[COLOR="Green"]xrandr --output S-video --off --output DVI-0 --auto[/COLOR]**

/sbin/initctl -q emit login-session-start DISPLAY_MANAGER=kdm
```

---

### Post by gpsvn on 2011-04-07
I am new to Ubuntu. Have just installed on my Compaq CQ70. Everything went well except two things:

1. The screen resolution does not seem right. All the texts are fine but the pictures and photos look funny. I went to System=> Preferences =>Monitors then a error message appeared that says "It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?" Clicking "No" led to a Monitor Preferences dialog box but none of the resolution settings can be used to improve the screen resolution. There is a Nvidia installed by Ubuntu but I don't know which settings would work. So I am posting it here, hoping for some guidance.

[IMG]https://lh6.googleusercontent.com/_jLLbfhfwbXI/TZ3eS9xdelI/AAAAAAAABAw/zCPxhU29KYI/s640/Screenshot.jpg[/IMG]

[IMG]https://lh4.googleusercontent.com/_jLLbfhfwbXI/TZ3eRd3R_SI/AAAAAAAABAs/wnvfMlCXX-o/s640/Screenshot-1.jpg[/IMG]

2. I tried playing a DVD with video clips organized in folders, also with music CD. The computer does not recognize the disc. I restart PC in Windows mode and windows has no problem at all reading the same disc.
[IMG]https://lh6.googleusercontent.com/_jLLbfhfwbXI/TZ6qKlllM_I/AAAAAAAABBU/ku9GKym4BAE/s800/Screenshot-4.jpg[/IMG]

Appreciate any guidance, comments.

---

### Post by Zorael on 2011-04-08
@gpsvn;

This is a bit unrelated to the thread at hand, but what you're describing is sort of to be expected of the proprietary Nvidia driver. It isn't fully compatible with later version of the *X Resize, Rotate and Reflect* extension (**RandR**), so you'll have to use (the very capable) Nvidia tool instead. Pick 'X Server Display Configuration' in the tree to the left, and then select the resolution you want.

As for the DVDs and CDs not being recognized, the error message suggests that the action associated with selecting the CD drive there is to start the GNOME CD ripper program Sound Juicer, and it fails at that. Perhaps it isn't even [installed](apt://sound-juicer)?

Regardless, you should be able to view the contents of a DVD using the normal file browser, and open them with programs that can play the video clips you have there. You may need to install some codecs if you haven't done so already; it should tell you. Likewise, you should be able to just click that 'Open Rhythmbox Music Player' button and have the CD be played in Rhythmbox.

What's at fault here is only the 'Audio Disc' link in the menu.

---

### Post by Drakmor on 2011-04-11
@Zorael Hey, thanks for the help! Its working great now! Sorry I've been so busy, or I would have let you know a few days ago. I'm not trying to be ungrateful or anything. Thanks again!

---


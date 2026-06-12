---
title: "no left click"
date: 2010-08-20
forum: General Help
---

### Post by CROLMAC on 2010-08-20
Hi, community. My eeepc 900 works well in general, i am very happy with it, and mostly with lucid.
  But I suddenly ,3 days ago, discovered that my left click button doesn't work anymore. Could it be software related?It happened on my 700 surf for a little while, but before I could really get worked up, it had resolved itself. Any ideas? thanks and take care. 
  btw my 900 is maybe old but has not till I aquired it seen much use, I doubt it could be from overuse, but then again, you never know..

---

### Post by madmax.santana on 2010-08-20
Can't rule out the hardware problem unless it works on some other OS or you are sure it is in order.
In case of a software problem, I think you will have to replace your X11 config file: /etc/x11/xorg.conf and declare explicitly the mouse that you are using.

---

### Post by CROLMAC on 2010-08-20
thanks for such a quick reply, and I will try it out. only as I am really a klutz, maybe you could give me a little detail?
  Is this in terminal? how do I declare the mouse? I use the touchpad.
  I don't use other OSes, but my son apparently used an external mouse and didn't report anything wrong...hmm

---

### Post by madmax.santana on 2010-08-21
That means that Linux has not recognized or is failing to recognize your touchpad...

I am sorry I am not sure I know a lot about touchpads. However, I guess confs for touchpad should be same as that of mouse. Actually I am not that much of a Ubuntu expert or, Linux expert for that matter... I was just looking for new posts and I came across your thread. I had the same problem with my mouse once... I searched and forum-ed to find a solution and in the end I found out that the mouse was faulty.

I can only give you a  few links and a bit of an overview.
xorg.conf is supposed to be responsible for the confs which help x-server (your window manager) start with correct configurations... It takes all confs for monitor, input devices etc... There are separate sections for monitor, resolution, mouse, kb and other i/p devices, if any.

> For a long time, editing xorg.conf was necessary for advanced input  devices and multiple monitor output to work correctly. This was regarded  to be a major usability obstacle. In modern systems this is seldom  necessary, thanks to input hotplugging and the [XRandR]("http://en.wikipedia.org/wiki/XRandR") extension integrated into new X.org releases. It is still needed for devices from some manufacturers, notably [NVIDIA]("http://en.wikipedia.org/wiki/NVIDIA") and [Wacom]("http://en.wikipedia.org/wiki/Wacom"),  whose drivers fail to provide support for those technologies. This also  cause confusion or even problems when changing an option that is no  longer explicitly entered is required.Courtesy: Wikipedia - [http://en.wikipedia.org/wiki/Xorg.conf](http://en.wikipedia.org/wiki/Xorg.conf)

So, if you look into /etc/X11/ and do not find an xorg.conf, do not panic, maybe your system doesn't use one. You can create one yourself.

Here is the manual to the xorg.conf.
[http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.1/doc/xorg.conf.5.html)

---

### Post by madmax.santana on 2010-08-21
And yet, an easier way would be to boot up a Hardy or Interpid Live Disk and copy the xorg.conf found in the /etc/X11/ of the Live Disk to the same dir in your installed distribution...
If that doesn't work (I have a feeling it would work), you might need to refer to my previous post and follow the manual to edit your xorg.conf manually.

Have a nice time. :)

---


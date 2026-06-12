---
title: "Detecting external monitor through C"
date: 2011-09-21
forum: General Help
---

### Post by boblettoj99 on 2011-09-21
Hello,
I need to print images to a projector through some programming language (I thought C would be easiest but if there's a better one suggestions are welcome!).

As far as I gather a projector is treated just like an external monitor, and through the monitor settings I can easily duplicate the screen. 

However I would like to be able to have a separate window running on the main monitor that I can press buttons on or whatever resulting in the image displayed on the projector to change. (If I just duplicate the screens that window will get in the way of the images!)

So my question is, how do I detect a projector (second monitor) through C, and then print stuff to it?
Just running a full-screen window would do fine, as long as it is sent to the projector only!

Thanks in advance!

---

### Post by boblettoj99 on 2011-09-21
Should probably say I'm much more confident in Java. Having found the magical google keyword "multi-monitor" it seems I can do this in Java!
I thought I'd have to fiddle around with horrible hardware stuff so originally dismissed it...

Using awt.GraphicsDevice and then extending the desktop over the projector (rather than duplicating), I think this should be possible!

Well...It's enough to get me going!

---


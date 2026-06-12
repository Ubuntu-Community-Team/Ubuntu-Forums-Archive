---
title: "Desktop help! - Intel Mobile 945GME Graphics"
date: 2012-04-09
forum: General Help
---

### Post by Zgamer01 on 2012-04-09
Hello, i'm new to the forums, and generally new to ubuntu. 
I've used it before, and i like it.
Anyway, i just put it on my Laptop. (Resolution 800x600)
I'm using an external monitor (1280x1024) and the default (800x600) seems to be stuck inside the 1280x1024. Any help?
I can post screen shots, but it'd be quite difficult, seeing as i'd have to upload to photobucket.

Thanks in advance

---

### Post by coffeecat on 2012-04-09
Welcome to the forum!

A few questions, and then someone may be able to help you.

You've tagged your thread "wubi". Do you have a wubi installation - that is one which is inside the Windows partition and installed with the wubi.exe installer?

A 800x600 resolution for a laptop sounds like an old laptop. What make and model? If you are running wubi, what version of Windows?

Lastly - do you know what type of video device you have? It could be that your problem is related to limitations of an old video chipset. If you don't know, open a terminal in Ubuntu and post the output of this commmand:

```
lspci | grep VGA
```

You can highlight the output with the mouse/trackpad, right-click -> copy and then paste it into your post.

---

### Post by Zgamer01 on 2012-04-09
I probably should of tagged it as ubuntu. I'm using ubuntu, but i installed it via Wubi.
It's not an old laptop. It's just a mini. Also, it's Windows XP.  
Here's an image.
[http://www.photoshack.com/displayimage.php?pid=6943](http://www.photoshack.com/displayimage.php?pid=6943)

Also; VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
[IMG]http://photoshack.com/displayimage.php?pid=6943&fullsize=1[/IMG]

---

### Post by Zgamer01 on 2012-04-09
> **Zgamer01 said:**
> [http://www.photoshack.com/displayimage.php?pid=6943](http://www.photoshack.com/displayimage.php?pid=6943)

Please note, this is a screencap of my desktop. The problem is shown in this picture.

---

### Post by coffeecat on 2012-04-09
> **Zgamer01 said:**
> Please note, this is a screencap of my desktop. The problem is shown in this picture.

That's a curious screenshot. I'm not sure what to make of it. With the monitor plugged in, click on the cogwheel symbol top-right, then "Displays". What does that tell you?

You didn't mention which version of Ubuntu, although that looks like 11.10 to me. Correct? Although the 945GME chipset is rather an old one (sorry!), it's doing quite well because I can see the drop shadow under the top panel, which means you are getting the Unity 3d desktop and hence acceleration. That's good going.

I'll add Intel 945GME to your thread title because that might attract someone with experience of that chipset.

When you tap the Windows key, does the dash (dashboard) appear OK, and does it obscure that strange screen within a screen effect? Also - can you move the mouse cursor outside of what you have defined as the 800x600 area?

---

### Post by coffeecat on 2012-04-09
By the way, you don't have to use Photobucket or an image hoster. You can upload images to the forum and they are automatically thumbnailed. Use the "Manage Attachments" button below the message field, or the [img]http://ubuntuforums.org/images/editor/attach.gif[/img] button in the message toolbar.

---


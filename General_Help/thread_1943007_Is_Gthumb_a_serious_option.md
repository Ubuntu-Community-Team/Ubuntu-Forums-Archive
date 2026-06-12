---
title: "Is Gthumb a serious option?"
date: 2012-03-18
forum: General Help
---

### Post by x-shaney-x on 2012-03-18
I have really struggled with photo management in linux and especially in Gnome/Unity.

However, I have come across Gthumb recently, which I haven't tried for some years.

It seemed to tick all the boxes for functionality I need but when I looked at the website, it appears it hasn't been updated since 2009.

So is it actively maintained (other than packaging) and is it worth continuing to use something that will eventually not work anymore?

---

### Post by fragos on 2012-03-18
I've always preferred gthumb as a viewer and now as a photo manager. The viewer preference is because it shows the animation in gifs that the default viewer dosen't. It has continually improved in small steps. As a manager it doesn't force me to use to file by date folders, I much prefer subject and project folders. The editor covers most of the basics without the complexity of gimp which I still use for serious editing. With gthumb 2.14.2 as my default photo ap, SD cards when inserted a reader come up nicely in gthumb for import. I get that particular version of gthumb with the webupd8 PPA from [https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8). I also get gimp from that PPA. I've never gotten anything unstable from that PPA and it's always more up to date than the Ubuntu PPAs.

---

### Post by x-shaney-x on 2012-03-18
It does have one very annoying problem though:

The window will not stay maximized in unity.  It maximizes ok but if I close it, the window does not open maximized the next time.

This is the only app I have used in unity that shows this behaviour.

It DOES open maximized in Gnome Shell and Unity 2D though.

---

### Post by fragos on 2012-03-18
I hadn't noticed that because I normally work with multiple windows open. With a 22" 1920x1080 monitor that works well for me. If you run gconf apps--gthumb-UI you'll find a window_height and window_width field with fixed values but no check box for fullscreen. Perhaps setting those fields for a larger window size will be acceptable.

---

### Post by x-shaney-x on 2012-03-22
Thanks for the gconf tip.

Setting window_height to my full y resolution has solved the problem (well, workaround more than solving) and it now opens maximized every time :)

Still concerned it won't be updated but it also handles video files much better than shotwell so I think I will stick with this and just keep an eye on other options just in case.

---

### Post by eric-yorba on 2012-03-22
> **x-shaney-x said:**
> Still concerned it won't be updated but it also handles video files much better than shotwell so I think I will stick with this and just keep an eye on other options just in case.

What issues have you had with video files in Shotwell?

---

### Post by x-shaney-x on 2012-03-22
> **eric-yorba said:**
> What issues have you had with video files in Shotwell?

Mainly that they play in an external player (Totem).
I tend to think if an app is dealing with a certain file type then it should handle them in the app itself?
That is how I am used to it working in Digikam anyway.

Gthumb does this very nicely and has thumbnails for the video files below the video playing.

---


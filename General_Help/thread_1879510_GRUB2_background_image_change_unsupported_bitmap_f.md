---
title: "GRUB2 background image change: unsupported bitmap format"
date: 2011-11-11
forum: General Help
---

### Post by zia.newversion on 2011-11-11
I've changed the GRUB default font successfully. It's a lot better now.

But I'm still having problem changing the background... I created a nice splash for myself using GIMP and put it in ~/Pictures/. Before putting it in /boot/grub or pointing the /etc/default/grub to it, I wanted to test the image and if it would actually get loaded.

So I rebooted and pressed 'e' at boot menu and then at the grub> prompt typed 
```
grub> background_image /home/zia/Pictures/grub-bg.png
```
And it says
```
:unsupported bitmap format
grub>
```

Is it a resolution problem?
Native resolution of my Graphics Card and LCD both is 1920x1080. The system also runs in this resolution. The plymouth splash runs in some weird resolution (it's happening since Maverick and it is because of ATI drivers, and I don't really care since it doesn't look that bad)... But I'm unsure about the GRUB resolution!
I tried
```
grub> vbeinfo
```
And it returns a long list of supported resolutions. In the end it says 
```
Preferred mode: 1920x1080
```
But 1920x1080 isn't listed in the supported resolutions!!! Also, the actual resolution looks kinda 1920x1080 and kinda doesn't. (Means I'm not sure). But one thing I'm sure of, I haven't set any GFXMODE in /etc/default/grub. Whatever resolution this is, GRUB is setting it up by itself.

I supposed that the resolution of GRUB is 1920x1080 and I created the grub-bg.png in the same resolution. So, that's why I'm asking, is it a resolution problem? If it is, how would I know what resolution I should give to the image?

I also tried download grub-splashimages package and tried to load them the same way in grub> prompt. They return the same error (they are all ttf images). I did try converting the grub-bg.png to jpg and it still returns the same error!

Please help! I'm starting to get fed up!
I wanna do it quick and move on to grub-themes...

---

### Post by Rodney9 on 2011-11-11
These sites I hope will help you - 

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

[http://www.multimediaboom.com/adding-background-on-grub2-in-ubuntu-11-04/](http://www.multimediaboom.com/adding-background-on-grub2-in-ubuntu-11-04/)

[http://ubuntucorner.blogspot.com/2011/02/configure-grub2-background-image.html](http://ubuntucorner.blogspot.com/2011/02/configure-grub2-background-image.html)

---

### Post by zia.newversion on 2011-11-12
Urgh!

I know all this. I've read it all...

But despite everything being accounted for, I cannot get it to work, and I can't figure out why! That is why I posted here...

(I searched Google before I started it, and I have bookmarked all the guides and tutorials in Ubuntu Forums and Ubuntu Community Documentation related to the subject)...

---


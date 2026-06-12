---
title: "Image rendered with border in Firefox when scaling"
date: 2010-03-10
forum: General Help
---

### Post by Nishanity on 2010-03-10
I'm using Ubuntu 9.10 and the latest version of Firefox. Screen resolution is 1280x800. If either the height or width properties have values below the actual image size, there is a 1px black border displayed on top and right of the image. For example, the header logo on guardian.co.uk's website looks [like this]("http://i.imgur.com/GE8SE.gif") to me.

I view Firefox at 100% zoom. Around 150% zoom the borders disappear but naturally everything else is too big and pictures get pixelated. I have tried googling around and found many bug reports but couldn't really find a fix. I tried creating a xorg.conf file so I could change the option XaaNoOffscreenPixmap, as this seemed to work for some people,  but only creating the .conf file seemed to mess up my setup so that didn't work either.

Is there a way to get rid of this problem? Thanks in advance!

---

### Post by dcstar on 2010-03-11
> **Nishanity said:**
> I'm using Ubuntu 9.10 and the latest version of Firefox. Screen resolution is 1280x800. If either the height or width properties have values below the actual image size, there is a 1px black border displayed on top and right of the image. For example, the header logo on guardian.co.uk's website looks [like this]("http://i.imgur.com/GE8SE.gif") to me.

I view Firefox at 100% zoom. Around 150% zoom the borders disappear but naturally everything else is too big and pictures get pixelated. I have tried googling around and found many bug reports but couldn't really find a fix. I tried creating a xorg.conf file so I could change the option XaaNoOffscreenPixmap, as this seemed to work for some people,  but only creating the .conf file seemed to mess up my setup so that didn't work either.

Is there a way to get rid of this problem? Thanks in advance!

Firefox 3.5/6 use different font rendering to FF 3.0.x in Linux.

Since you have not specified which version you are using I will assume it is 3.5 and it is possible that this is an issue. That site looks fine on my FF 3.0.18 system.

You should also disable all Add-ons/Ad blockers etc to check if this makes a difference.

---

### Post by Nishanity on 2010-03-11
**dcstar**, I was using FF 3.5.8. Upgraded to FF 3.6 and the problem persists. Disabling AdBlock Plus made no difference. [The problem is supposedly fixed]("http://www.reddit.com/r/linux/comments/bbron/please_help_image_rendered_with_border_in_firefox/c0lyl65") in an update to the  Intel driver? Hasn't reached my repo yet.

---

### Post by kio_http on 2010-03-11
Try deleting files in ```
/home/youruser/.firefox
```

Also you may like opera, its very fast and great at rendering.

---


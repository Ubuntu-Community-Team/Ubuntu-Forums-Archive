---
title: "sidebar and dash home are black."
date: 2012-08-13
forum: General Help
---

### Post by Alidaco on 2012-08-13
My sidebar and dash home are black and I'm not sure why, because they used to be purple. It first occurred after a restart. Does anyone know what's going on? For what it's worth, I'm running a dual monitor setup.

Here is a photo to show you what's going on.
[http://imgur.com/v3cz9](http://imgur.com/v3cz9)

---

### Post by Zorgoth on 2012-08-13
> **Alidaco said:**
> My sidebar and dash home are black and I'm not sure why, because they used to be purple. It first occurred after a restart. Does anyone know what's going on? For what it's worth, I'm running a dual monitor setup.

Here is a photo to show you what's going on.
[http://imgur.com/v3cz9](http://imgur.com/v3cz9)

It's possible that the transparency has been lost. Get ccsm and check the transparency settings for Unity. It's also possible that your graphics are not working correctly, which could stop the transparency from working.

Edit: the transparency is governed by Background Color in Ubuntu Unity Plugin. It should have opacity zero to be transparent (default setting). Yours was purple before because the desktop background is purple I am assuming.

Edit 2: to get ccsm, open Ubuntu Software Center (or Synaptic Package Manager, which I highly recommend getting if you don't have it) and install the program CompizConfig Settings Manager. Be careful with this program; it is fun to play with, but you could mess up your desktop if you are not careful.

---

### Post by Zorgoth on 2012-08-13
Does the command 

glxinfo | grep Direct 

in the terminal say you have Direct Rendering?

---


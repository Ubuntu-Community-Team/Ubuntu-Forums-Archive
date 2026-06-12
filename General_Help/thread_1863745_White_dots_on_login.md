---
title: "White dots on login"
date: 2011-10-18
forum: General Help
---

### Post by soulvoid on 2011-10-18
Hi,

I did an update of ubuntu to oneric that for some reason failed(black screen after I was on the phone). I ended up installing oneric to the same partition and now most things work again except for a few things. However I have a bunch of dots in a grid pattern on the login screen like every 20 pixels or so. Anyone know howto get rid of this?

---

### Post by dino99 on 2011-10-18
into a terminal (ctrl+F2) try:

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it)

---

### Post by mcduck on 2011-10-18
The default background image for the 11.10 login screen actually does have light dots at about 20 pixel intervals, so what you are seeing sounds like perfectly normal situation... ;)

If you don't like the default background, then Simple LightDM Manager might be a tool for you: [http://www.webupd8.org/2011/10/simple-lightdm-manager-change-lightdm.html]("http://www.webupd8.org/2011/10/simple-lightdm-manager-change-lightdm.html")

---


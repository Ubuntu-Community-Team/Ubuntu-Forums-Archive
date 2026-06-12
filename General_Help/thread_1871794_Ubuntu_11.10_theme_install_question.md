---
title: "Ubuntu 11.10 theme install question"
date: 2011-10-29
forum: General Help
---

### Post by JPBodner on 2011-10-29
Hi all

I've upgraded to 11.10 with Unity but I'd like to customize my desktop more.  Now that we've got Unity, what types of files from gnome-art or gnome-look should I be downloading?  GTK? GDM?  I'm looking to customize the background, icons, colors, etc.  



Thanks!

---

### Post by Frogs Hair on 2011-10-29
You will need GTK3 themes for 11.10 . Some of the themes at Gnome look are are for the shell only . Remember to install the Gnome Tweek Tool / Advanced Settings for theme selection . Ubuntu Tweak has been updated for 11.10 and works well for changing login background . Most newer icon themes should work in Gnome 3 .

(Downloaded Themes) 

 (Single User) Create a .themes and .icons folder in home / hidden folders . (All Users) Use gksudo nautilus > File System / usr / share / themes or icons .

 Download , extract the packages , and place the folders in either location making theme selections using Advanced Settings . Logout - in may be required.

---

### Post by raja.genupula on 2011-10-29
> **JPBodner said:**
> Hi all

I've upgraded to 11.10 with Unity but I'd like to customize my desktop more.  Now that we've got Unity, what types of files from gnome-art or gnome-look should I be downloading?  GTK? GDM?  I'm looking to customize the background, icons, colors, etc.  



Thanks!

[http://www.ubuntuvibes.com/2011/05/meet-unico-new-gtk3-theme-engine-in.html](http://www.ubuntuvibes.com/2011/05/meet-unico-new-gtk3-theme-engine-in.html)


[http://www.omgubuntu.co.uk/2011/10/how-to-install-gnome-shell-themes-in-ubuntu-11-10/](http://www.omgubuntu.co.uk/2011/10/how-to-install-gnome-shell-themes-in-ubuntu-11-10/)

---

### Post by JPBodner on 2011-10-29
Thanks!

So, am I alone in finding it strange that the tweak tool is needed to customize the user experience?  It seemed easy in earlier versions of Ubuntu.  Shouldn't a good Linux OS provide a clean way to do these things out of the box?

---

### Post by dhayfule on 2011-10-30
> **JPBodner said:**
> Thanks!

So, am I alone in finding it strange that the tweak tool is needed to customize the user experience?  It seemed easy in earlier versions of Ubuntu.  Shouldn't a good Linux OS provide a clean way to do these things out of the box?

I just upgraded to ubuntu 11.10 from 11.04 and found it frustrating that they have removed Ubuntu Classic desktop manager and so as workaround I installed XFCE desktop manager..... Why in the heavens did Canonical do this to us???????

---

### Post by vasa1 on 2011-10-30
> **Frogs Hair said:**
> ... Ubuntu Tweak has been updated for 11.10...
What is it called in the Ubuntu Software Center?

---

### Post by vasa1 on 2011-10-30
Okay. After reading [http://blog.ubuntu-tweak.com/2011/09/18/ubuntu-tweak-0-6-beta-is-ready-for-testers-and-developers.html#more-1077](http://blog.ubuntu-tweak.com/2011/09/18/ubuntu-tweak-0-6-beta-is-ready-for-testers-and-developers.html#more-1077), I'll hold off on trying it. I'll just stick to editing css and ini files.

---

### Post by JPBodner on 2011-10-30
> **dhayfule said:**
> I just upgraded to ubuntu 11.10 from 11.04 and found it frustrating that they have removed Ubuntu Classic desktop manager and so as workaround I installed XFCE desktop manager..... Why in the heavens did Canonical do this to us???????

I agree.  Overall, I've always been a big fan of Ubuntu, but the last release seems harder to work with and harder to customize.  Canonical should assume that I want to fine tune the user experience and make it easy for me to do.  If I wanted an out-of-the-box UI with limited ability to customize, I'd buy a Mac! 

I know the reception of the last two releases has been mixed, to say the least.  I hope they're listening!

---

### Post by dhayfule on 2011-10-31
Thanks to XFCE... Gnome 3 and Unity should have been released in two editions i.e. Tablet and Desktop, so that User Experience of desktop users would not have been compromised!!!!!  I think, its time to look beyond Gnome... hope so XFCE doesnt follow footsteps of Gnome

---


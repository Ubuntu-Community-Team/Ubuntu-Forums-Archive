---
title: "Ubuntu icon replaced by gnome icon"
date: 2010-08-30
forum: General Help
---

### Post by PuddingKnife on 2010-08-30
So, I have been trying to customize my desktop a bit, and I have run into a bit of a snag. 

I successfully installed the new Plymouth screen detailed here:

[http://www.omgubuntu.co.uk/2010/08/stunning-user-created-plymouth-boot.html](http://www.omgubuntu.co.uk/2010/08/stunning-user-created-plymouth-boot.html)

However, as a result of changing my boot splash (I think?) I have lost my Ubuntu icon. Its been replaced by the Gnome foot, which I am not a fan of. Here is a screen shot to give a better idea of what I mean:

[ATTACH]167973[/ATTACH]

I am currently using the Faenza icon set, and on either menu I'm using, I can't select the Ubuntu icon. 

I'm guessing the fix for this is fairly simple, but I am at a loss. Please help!

---

### Post by PuddingKnife on 2010-08-30
Hmm. Maybe this should have gone in the beginners forum. Any mods wanna help me out?

---

### Post by marshmallow1304 on 2010-08-30
I believe the Gnome menu uses an image in /usr/share/icons/<theme>/places/<dimensions> (or .../<dimensions>/places) called start-here.* or a symlink thereof.  Do a search in that directory and backup and replace that file.  I had to do that when I installed the Humanity Dark theme on Gentoo and ended up with the Ubuntu logo on my menu.

Edit: It seems that the panel itself uses 22x22 and the Add to Panel dialog uses 48x48.

---

### Post by PuddingKnife on 2010-08-30
Thanks, but do you have any idea why it would switch like that? I just wanted the default white Ubuntu icon as it appears in 10.04. 

This will help tho.

---


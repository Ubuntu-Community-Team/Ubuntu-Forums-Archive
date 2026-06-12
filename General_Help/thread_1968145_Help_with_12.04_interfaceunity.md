---
title: "Help with 12.04 interface/unity"
date: 2012-04-28
forum: General Help
---

### Post by flyingsliverfin on 2012-04-28
I'm testing 12.04 from a live CD to see how I like it (coming from 10.04). 

I have a couple questions though:
1. Is there a way to browse say, all the games installed on the system?
2. Why is there no clickable scrollbar in the dash home? every time I click on the tiny vertical line that tells how far down I am, the dash goes away.
3. If unity is based off compiz, how come when i search for compiz there's nothing that comes up? Shouldn't CCSM be installed by default?
4. Is there a way to put the old 'show desktop' button somewhere out of the way?
5. Change amount of visual effects? Like in the old 'Appearance' menu in 10.04 I can choose if i want 'none', 'normal', 'extra', or 'custom'.
6. Can i add another smaller panel on the right? I have miscellaneous scripts that do various small things like run the latest podcast I downloaded from a folder etc. but I don't use them often enough to pin them to the main dock thing.
7. A way to see all the open windows like mac's tiling thing?

I can see how nice this might be for all these annoying widescreen laptops and saving pixels. And speeding up work. I sorta miss the old minimize where it goes to the bottom panel (gnome 2); I feel like its a bit faster than alt-tabbing around or clicking on the launcher -> choose.

---

### Post by kolinab on 2012-04-29
> **flyingsliverfin said:**
> I'm testing 12.04 from a live CD to see how I like it (coming from 10.04). 

I have a couple questions though:
1. Is there a way to browse say, all the games installed on the system?

Yes. Open the dash by clicking the ubuntu icon. Then click the second icon at the bottom - the one that looks like a little ruler/pencil/pen. Then select 'installed,' Finally, on the top right, select 'filter results,' and in the column on the right, click 'games.'

> 
2. Why is there no clickable scrollbar in the dash home? every time I click on the tiny vertical line that tells how far down I am, the dash goes away.

I don't know either, but I've just tested on my system and experienced the same thing. Instead of using a clickable scroller, I scroll with a) my mouse roller b) my trackpoint and middle mouse button or c) the 'edge' of my touchpad. You might need to enable either edge scrolling or two finger scrolling in your system settings to make this work.

> 
3. If unity is based off compiz, how come when i search for compiz there's nothing that comes up? Shouldn't CCSM be installed by default?

I'm not sure, but I guess maybe compiz is working in the background without giving you a settings interface. CCSM is an advanced tool - many people don't miss it or wouldn't use it. You can install it on the command line with:

```

sudo apt-get install compizconfig-settings-manager

```

> 
4. Is there a way to put the old 'show desktop' button somewhere out of the way?

I don't know.

> 
5. Change amount of visual effects? Like in the old 'Appearance' menu in 10.04 I can choose if i want 'none', 'normal', 'extra', or 'custom'.

I'm not sure, but if you want a desktop without all the effects, you can select 'unity2d' on your login screen and try that.

> 
6. Can i add another smaller panel on the right? I have miscellaneous scripts that do various small things like run the latest podcast I downloaded from a folder etc. but I don't use them often enough to pin them to the main dock thing.

I don't think so, at least, not with unity. There are other desktop environments you can use that might give you this level of customization. You might look into one called 'Cinnamon' which you might find more configurable.

> 
7. A way to see all the open windows like mac's tiling thing?


Yes. Try Super+s (Your windows key). You can configure this on the 'desktop' section of ccsm. It is called the 'expo' feature.

Good luck!

K

---


---
title: "My wireless icon, sound icon, and others are missing!"
date: 2009-12-13
forum: General Help
---

### Post by Masterj15 on 2009-12-13
By accident I deleted it. So I checked out how to get it back and I found out that I deleted the notification area. I went into the add to panel and added it back but the wireless icon and my sound icon are still missing!

And I can't connect to the internet without it!

Also, Ubuntu wont allow me to access my secondary internal hard drive anymore. When I upgraded to Karmic, it usually asks for a password. Now, it wont even ask me and I need that because I trying to delete a virus on the xp side.

If anyone has any ideas, that would be greatly appreciated.

---

### Post by Masterj15 on 2009-12-13
bump lolz

---

### Post by TheOnlyMrK on 2009-12-13
Is "network-manager-gnome" installed in Synaptic? The sound controller I can't remember it's name right now... Am still looking.

"gnome-media" seems to be the volume adjuster, I had to do some searching to figure that out. Lol. Is it installed too? Other then that I'm not real sure what to recommend, hopefully someone with more knowledge on this subject will reply.

---

### Post by Masterj15 on 2009-12-15
> **TheOnlyMrK said:**
> Is "network-manager-gnome" installed in Synaptic? The sound controller I can't remember it's name right now... Am still looking.

"gnome-media" seems to be the volume adjuster, I had to do some searching to figure that out. Lol. Is it installed too? Other then that I'm not real sure what to recommend, hopefully someone with more knowledge on this subject will reply.

I know I have both, I just checked. I just deleted the icons by accident and they wont come back up.

I would just reinstall them but I can't because I didn't connect the internet yet and I need the icon.

---

### Post by ean5533 on 2009-12-15
> **Masterj15 said:**
> I know I have both, I just checked. I just deleted the icons by accident and they wont come back up.

I would just reinstall them but I can't because I didn't connect the internet yet and I need the icon.
I think I know what you're getting at -- I think you just removed the widget from the toolbar that displays those icons. It's pretty easy to add back, though:

I'm doing this from memory without an Ubuntu computer nearby to check against, so the details might be fuzzy. Right click on the toolbar, click "Add to Panel", scroll through the list and find... crap, I can't remember what the widget is called. I think it's something like Applet Area... something along those lines. I can find out the real name when I head home in an hour (unless someone else can check now?)

Let me know if this is completely the wrong advice :)

---

### Post by Masterj15 on 2009-12-15
> **ean5533 said:**
> I think I know what you're getting at -- I think you just removed the widget from the toolbar that displays those icons. It's pretty easy to add back, though:

I'm doing this from memory without an Ubuntu computer nearby to check against, so the details might be fuzzy. Right click on the toolbar, click "Add to Panel", scroll through the list and find... crap, I can't remember what the widget is called. I think it's something like Applet Area... something along those lines. I can find out the real name when I head home in an hour (unless someone else can check now?)

Let me know if this is completely the wrong advice :)

I do know what your talking about. You mean the notification area. I saw that in another thread and tried that but only the display screen icon came up. The rest are totally gone, which is odd.

Thanks though, I feel like I am closer to finding out the problem to this delma. :D

---

### Post by Masterj15 on 2009-12-15
bump lolz

---

### Post by Masterj15 on 2009-12-16
bump

---

### Post by Masterj15 on 2009-12-18
bump

---

### Post by Masterj15 on 2009-12-19
bump

---

### Post by spiderbatdad on 2009-12-19
yes you have to have "notification area" for the nm-applet. If you have notification area and don't see a network icon, try starting it manually. Press alt+F2 and run ```
nm-applet --sm-disable
``` If the problem still exists. Look at /etc/network/interfaces

---

### Post by Masterj15 on 2009-12-19
> **spiderbatdad said:**
> yes you have to have "notification area" for the nm-applet. If you have notification area and don't see a network icon, try starting it manually. Press alt+F2 and run ```
nm-applet --sm-disable
``` If the problem still exists. Look at /etc/network/interfaces


awesome, I will give this a check after work. This made my day! This totally makes sense too!

<3

Thanks again you guys :)

---

### Post by Quarkrad on 2009-12-19
I have just sorted my problem with missing wireless icon.  I downloaded and installed package from here: [http://packages.ubuntu.com/karmic/i386/network-manager-gnome/download](http://packages.ubuntu.com/karmic/i386/network-manager-gnome/download)

---

### Post by southernman on 2010-06-18
Although this is an old thread, I made a mistake today when shutting down transmission.

To fix, what you need to do is: right click on the panel > select "add to panel" > scroll through the list and select "indicator applet"

Credit to 23meg where I found the suggestion.

---


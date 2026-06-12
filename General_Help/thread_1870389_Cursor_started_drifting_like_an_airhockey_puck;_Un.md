---
title: "Cursor started drifting like an airhockey puck; Unity 3d problem, too"
date: 2011-10-27
forum: General Help
---

### Post by mittenchops on 2011-10-27
I upgraded to 11.10 over the weekend from 11.04.  It seemed basically OK, but then I got adventurous.  Some googling led me to conclude that I could add multitouch gestures easily, so I apt-got the xserver-xorg-input-multitouch and xserver-xorg-input-mutouch packages.  I think the latter required some strange ppa be added (xorg-edgers or something).

I installed it, but didn't get multitouch working---but everything else kept working, so I didn't want to press my luck.  I ignored it.

After over a day passed, Tuesday, on start, update center told me I should do a distribution upgrade.  Apparently, I needed a partial upgrade.  I saw that 173 packages would be installed, and one xserver package would be removed but not replaced, so I hesitated.  I posted a message over at ubuntu.stackexchange about whether it would be wise to upgrade or not given that everything seemed to be working, but didn't see a reply.  Also, it kept bugging me every day, so I assumed it was important.  So I upgraded. ([http://askubuntu.com/questions/72332/multitouch-mess-up-now-partial-upgrade](http://askubuntu.com/questions/72332/multitouch-mess-up-now-partial-upgrade))

That caused a problem.  No icons on the desktop, no menu, no sidebar.  And my cursor couldn't "curse" (though I did).  For precise movements, it floated and made it hard to select anything, such as links.

I rebooted into Unity 2d, and I seem to have menus and icons back.  But 3d still doesn't work (various compiz irregularities), and the cursor still floats.  The float begins to happen even at the login screen, as soon as a cursor is available.  

Booting back into Unity 3d, the menu and titlebars came back, but all shift/fade, etc. 3d effects are too slow to be usable.  As one example, I still have a cairo-dock on my system from before using unity, and the enlarge/shrink effects freeze the system.

I assume all of this is related, somehow, to xserver stuff and this recent upgrade---which makes me feel like this:
[https://www.xkcd.com/963/](https://www.xkcd.com/963/)

(Also, the float behavior has a weird characteristic that may be helpful in diagnosis---it's as if the touchpad input is being duplicated, once with a lag, to position the cursor.  Mostly don't notice it except for small movements.)

I'm wondering if anyone can help me begin my diagnosis. I am hesitant to reinstall completely, but it looks like it will be very precise surgery to figure out the couple of lines in piles of settings that are contributing to all these symptoms...

UPDATE 1:
Another component:
Screenshots apparently stopped working, too? I know these were working before the upgrade, but now, it takes a picture of a black screen with only the cursor visible. 
Weird combination of problems!

UPDATE 2: 
The cursor moves in the direction it was last moving in so long as my finger is on the touchpad.  With no movement, it will continue to drift in the same direction forever so long as the finger remains in contact with the touchpad.

UPDATE 3:
In addition to being unable to TAKE screenshots, I am also unable to view PNG files.  Maybe a file association problem?  I don't know.  Please help me restore to a functional configuration like I had just days ago!!

---

### Post by mittenchops on 2011-10-27
I posted a reply that I consolidated into the above.

(I hovered over "edit/delete" but apparently I can only edit this reply, not delete.)

Anyway, all problems above still exist.

---


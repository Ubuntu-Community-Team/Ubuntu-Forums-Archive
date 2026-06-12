---
title: "mouse clicks don't work anymore"
date: 2010-09-02
forum: General Help
---

### Post by jcphil on 2010-09-02
Yesterday, without any warning, mouse clicks stopped having any effect. I can move the cursor without a problem. No apps are frozen and I can type at the command line. But mouse clicks have no effect. The same mouse was working fine before and it works fine in Windows. When I look in /var/log/messages, I see:

ondemand governor failed, too long transition latency of HW, fallback to performance governor [OK]

I don't know if this is significant or not. The mouse is connected via USB. I'm running Lucid Lynx with all of the latest updates. Any ideas out there?

---

### Post by anirudhtomer on 2010-09-03
Same happened with me too. I am using 9.10 karmic koala.
I went to the tty1 terminal & typed "ps -axj" to list down the processes & then killed some of the programs which were running on the gnome & my system started working normal again.

---

### Post by jcphil on 2010-09-04
I decided I would upgrade to Maverick, but the problem is back in that version too. I'm finding the mouse clicks are selectively unresponsive. Jut now, open applications wouldn't respond to left-clicks, but items in the Gnome panel would. Then I did a right-click in the panel and selected "About". Now the panel doesn't respond to left-clicks, but open applications do. I'm not finding anything in Xorg logs or messages that would help in understanding this. I can now switch back and forth by fiddling with the panel. Very weird.

---

### Post by iggywig on 2010-09-06
Yes I'm seeing the same problem in Maverick too. Mouse works fine for a bit then all of a sudden the left click stops working all together. It's like it's stuck down or something..

---

### Post by jcphil on 2010-09-06
I found what may be the solution. Under System-->Preferences-->Input Method Switcher, the option selected (not by me) was:

Do not use input method.

I changed this to the default and now I seem to have full mouse functionality in all areas of the screen. I'll post more if the problem resurfaces.

---

### Post by gldearman on 2010-09-06
> **jcphil said:**
> I decided I would upgrade to Maverick, but the problem is back in that version too. I'm finding the mouse clicks are selectively unresponsive. Jut now, open applications wouldn't respond to left-clicks, but items in the Gnome panel would. 

This sounds exactly like the problem I am having: the panel will respond to left-clicks, but open apps will not.  Only, for me, it is only on one mouse with one user; a different user or a different mouse, no problem.  My thread is [thread=1569457]here[/thread].

I'm on Lucid, and there is not "Input Method Switcher" in my System > Preferences menu.  Is that new for Maverick?  Is there a way in Lucid to change the same setting?

---

### Post by jcphil on 2010-09-06
That dialog is new in Maverick. I don't know how you would change the same setting in earlier versions.

---

### Post by jcphil on 2010-09-06
No joy yet. The next time I logged in, mouse clicks stopped working on buttons and would no longer scroll the browser. This is making Linux virtually unusable for me. Are there any Ubuntu gurus out there who have more insight into mouse issues? This is clearly a software thing, but I've run out of things to try or logs to review.

---

### Post by gldearman on 2010-09-06
> **jcphil said:**
> That dialog is new in Maverick. I don't know how you would change the same setting in earlier versions.

Thanks, but never mind.  My mouse problem was related to the Sugar environment not playing well with Gnome, so is unlikely to be the same as yours, despite the same symptoms.

EDIT: Though, I guess it could be related to the same key in gconf, even with a different cause.  Check your setting for /apps/metacity/general/mouse_button_modifier.  Mine was set to "disabled."  Changed it to <Super>, no more problem.

---

### Post by iggywig on 2010-09-07
I've found what my problem is.. It seems to be when I use the media buttons on my keyboard the mouse gets stuck.. I tried changing the input method but this made no difference.

---

### Post by gldearman on 2010-09-07
> **iggywig said:**
> I've found what my problem is.. It seems to be when I use the media buttons on my keyboard the mouse gets stuck.. I tried changing the input method but this made no difference.

What model is your keyboard?

---

### Post by jcphil on 2010-09-08
> **gldearman said:**
> Thanks, but never mind.  My mouse problem was related to the Sugar environment not playing well with Gnome, so is unlikely to be the same as yours, despite the same symptoms.

EDIT: Though, I guess it could be related to the same key in gconf, even with a different cause.  Check your setting for /apps/metacity/general/mouse_button_modifier.  Mine was set to "disabled."  Changed it to <Super>, no more problem.

I tried this and it had no effect on my problem. It goes below the layer of desktop environment, because I installed Kubuntu in my desperation and I have the exact same problem there. Something resets the mouse button. I can still toggle it between:

works in panel but not in apps

and:

works in apps, but not in panel

I do this, as mentioned above, by right-clicking on the panel and selecting "About". I don't know enough about how the mouse is configured in X-windows to see what may be wrong.

---

### Post by jcphil on 2010-09-08
I thought I would try changing the mouse button mappings using xinput. The suggested mapping for my mouse is:

xinput set-button-map "Logitech USB Trackball" 1 8 3 4 5 6 7 2 9

This is what others with the same device had recommended. But the net result is that it still fails.

---

### Post by jcphil on 2010-09-08
I found a note on configuring the Logitech USB Trackball here:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/567068/comments/7](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/567068/comments/7)

I made the recommended changes to xorg.conf and everything seems to be working now.

---

### Post by jcphil on 2010-09-09
Well, the problem reappeared after the next reboot. So, not solved.

---

### Post by CarlesOriol on 2010-10-15
I'm blocked at the same point.

When I start the computer it does not work. After writing the changes on xorg.conf, when I restart the gdm it works but after a reboot the mouse stills not working in the aplications (until i restart the gdm).

It worked fine on lucid with the lines at xorg.conf, but not without  them.

---


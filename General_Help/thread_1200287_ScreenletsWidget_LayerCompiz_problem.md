---
title: "Screenlets/Widget Layer/Compiz problem"
date: 2009-06-29
forum: General Help
---

### Post by McCat on 2009-06-29
So, I've recently installed CompizConfig and Screenlets and so far I'm really impressed with what they're able to accomplish.

Only one hitch: my screenlets/widget layer or something isn't working properly. I press F9 and the layer pops up quite nicely (see attachment)-- but as soon as I click on ANYTHING, it disappears again. This happens if I click+hold to move a window (as soon as I let go, it fades to desktop), click ON a window, right click on a window, etc. All of it causes the widget layer to fade out back to the desktop.

I have tried going to CompizConfig and changing the widget layer to NOT close on click but that has not changed anything-- the problem still persists.

I have also tried uninstalling and reinstalling Screenlets but to no avail.

I have fairly normal hardware-- Nvidia card and such. I can list everything if it's really relevant. I am using Jaunty 64-bit though.

I would love to be able to take advantage of this nice feature, so any help anyone can provide would be MUCH appreciated.


Thanks in advance!

---

### Post by lovinglinux on 2009-06-29
Unticking the "End Widget Mode on Click" should be working. Nevertheless, you could try adding another window type to the widget layer and test if it also display the problem. Do you know you can run any application window on the widget layer right? For example, if you want to put gnome-terminal in the widget layer, click the "Behavior" tab of the widget layer plugin settings, then add *class=Gnome-terminal* to the "Widget Windows" option.

If the layer closes when displaying the terminal, then the problem is the plugin itself, not on the screenlets side.

BTW, this was happening to me also a couple of days ago, but I don't how it was fixed. You could try to reboot and see how it goes.

---

### Post by thrice_loved on 2009-07-20
I've been having the same problem. I have unclicked the 'end on click' option but it still persists.

The widget layer itself looks lovely and is great for checking the calendar etc. - Oddly I can use the calulator to type things in but I cannot click to get an answer. Also I cannot use the conversion widget becasue the moment I click the preferred conversion it disappears on me!

Btw - it's really unlikely to be a graphics or a 64-bit thing. I am running the 32-bit 9.04 with an ATI graphics card.

Hmm... I will keep playing around. Please post if you find a solution :-)

---

### Post by thrice_loved on 2009-07-20
It's a recognised bug:

Widget layer disappears when interacting with applications within the widget layer:
[https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-extra/+bug/356374](https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-extra/+bug/356374)


That at least makes me feel better! One man released a fix (Taylor "Ripps" L-Wren  on 2009-05-29 - towards the bottom of the page) - which seems to be doing the trick. I hope this helps :-)

---

### Post by rygar on 2009-09-23
i am having trouble installing this fix by Taylor...

when i attempt to add the keyserver, it times out.  and what do i do once it adds to install the package?

---


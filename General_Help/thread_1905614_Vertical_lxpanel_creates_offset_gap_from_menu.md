---
title: "Vertical lxpanel creates offset gap from menu"
date: 2012-01-07
forum: General Help
---

### Post by henriquemaia on 2012-01-07
I'm using lxpanel placed vertically on the left side of the screen and whenever I press the menu icon, the subsequent menu is placed with a gap from the panel.

You can check the effect here:
[IMG]http://i.imgur.com/3Y3hc.png[/IMG]

Is it a problem of lxpanel, pcmanfm or openbox? Where can I correct this?

Thanks in advance.

---

### Post by Rex Bouwense on 2012-01-07
When you changed the panel's position from the bottom to the left side, did you also change the size of the panel?  That might yield the desired result that you are looking for.

I just checked the LXDE forum and there doesn't seem to be any information there.  Sorry.

---

### Post by henriquemaia on 2012-01-07
> **Rex Bouwense said:**
> When you changed the panel's position from the bottom to the left side, did you also change the size of the panel?  That might yield the desired result that you are looking for.

I just checked the LXDE forum and there doesn't seem to be any information there.  Sorry.

Yes, I had to. When changing position, the panel assumed a huge width. I'm using it at 24pix width, but the gap is at 45 pix (measured it by enhancing the size of the panel).

Another thing that happens is that, when using guake, guake assumes the panel to be on the right and not on the left. When I change the size of the panel, guake behaves accordingly not covering the portion of the screen corresponding to the new size of the panel. Weird. 

You can see it happening here:
[IMG]http://i.imgur.com/pqRwn.png[/IMG]

---

### Post by henriquemaia on 2012-01-07
If I use lxpanel on the right, everything is good. Weird. 
Too bad I want it on the left. 

[IMG]http://i.imgur.com/WM2k2.png[/IMG]

---

### Post by Rex Bouwense on 2012-01-07
Just got back to the RV and I thought someone would have come up with a suggestion.  Anyway, I tried to duplicate the problem and sure enough if I move my panel to the left and decrease the width to what you have done (24 pixels) the gap exists on my system as well.  I am using Lubuntu 11.10.  It's not a big thing but if it can be moved I'm sure that someone will come up with a solution.

---

### Post by henriquemaia on 2012-01-08
I've found a solution for the menu gap problem. It's simple, though it takes a bit of work.

If you have the panel on the left, put it somewhere else. Then add a new panel, put it on the left and replicate the first one so you have all the features you want. In the end, delete the first panel and remain with the new one. 

The new panel doesn't have the gap problem. 

I still can't eliminate the shadow panel on the right when using guake. Maybe someone can come up with something in the meanwhile.

---

### Post by mðwsmith on 2013-02-17
I've fixed this on lubuntu Ubuntu 12.10 by editing the size of the icon for the start menu to less than the width of the vertical bar - I edited down to 24x24 pixels - see attachment.

If the graphic is too big it will displace the menu.

Path on my system for the files;

/usr/share/lubuntu/images, you will need root to place files here.

Right click on the start button for the menu setting to change the icon used.

Now only the wifi sysmbol is off set but that's quite minor - its still readable.

Hope this helps

---

### Post by Bucky Ball on 2013-02-17
[B][I]Thread Closed
[/I][/B]

Thanks for sharing but old thread put to bed. A lot changes in a year and though your solution is good for current users quite possibly not related to the original problem on whatever was being used by the OP a year ago.

Please post new threads rather than resurrecting ones that have been inactive for a year or more. Cheers.

---


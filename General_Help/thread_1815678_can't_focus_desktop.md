---
title: "can't focus desktop"
date: 2011-07-31
forum: General Help
---

### Post by mixmastamyk on 2011-07-31
Hi,

Upgraded to Natty a week ago from Maverick and still using the Classic desktop.  There were lots of minor issues but turned off a few things like wobbly windows and am mostly back to normal.

One problem left is that I can no longer focus on desktop icons unless I minimize all my windows.  This makes it difficult to rename files there, something I do every day.  I can right click on them and select rename from the menu (or F2) and the name is highlighted, but I can't get it selected nor will it take keyboard input to complete the operation.

I like to work on a few desktop files before moving them to their long-term locations.  Can anyone help?  Looks like a bug in compiz, but I'm not sure.

---

### Post by cybergalvez on 2011-07-31
I would post your hardware configuration because I'm using natty without issues.

---

### Post by mixmastamyk on 2011-08-01
Ok,

```

> lspci | grep VGA
21:02:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]

> grep -i driver /etc/X11/xorg.conf | uniq
	Option	    "VendorName" "ATI Proprietary Driver"
	Driver      "fglrx"

> dpkg -l compiz | grep ii
6:ii  compiz     1:0.9.4+bzr20110606-0ubuntu1~natty2

```

---

### Post by mixmastamyk on 2011-08-18
Ok, I gave up and downgraded to compiz .8x via the instructions here:  [http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)

Nice to have proper resize and zoom back.  Things are back to normal now, but how do I get compiz to be the default window manager?  Every time I boot it goes back to metacity.

I could put a --replace command in a startup file somewhere, but I'd prefer to run the correct WM first.

---


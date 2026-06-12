---
title: "Ubuntu refuses to print greyscale"
date: 2010-04-18
forum: General Help
---

### Post by WA1DH on 2010-04-18
I have a Brother Intellifax 1860C with the Brother-Fax-1860C CUPS v1.1 driver installed. I can't seem to make it print in greyscale only. When I print from Firefox, I clicked Advanced->Color/Greyscale and set it to greyscale in the printer options, but it still prints color. When I change the settings in System->Administration->Printers to greyscale, it still prints color. I went into CUPS and it listed greyscale, which I had set it to, but still color.

It's important I DON'T print color because I only buy black ink in bulk. My color cartridges are low and the printer won't print anything at all if they run out.

Please help..

Thanks.

---

### Post by quixote on 2010-04-19
If you set it in CUPS *and* in FF, it has zero excuse not to be printing greyscale.  Very strange.  You accessed cups by going to [http://localhost:631/](http://localhost:631/), selecting the right printer, and selecting "Administration", and then "color model"?

There's also a setting under System > Administration > Printers.  Right-click on the printer icon you want, select Properties > Printer Options, and see what's under Color Model.  It should be getting that from CUPS, but who knows, maybe it has old settings in its cache?

Or maybe somehow the settings were set for another printer with a similar model name or something??

---

### Post by WA1DH on 2010-05-14
Thanks for the reply. Sorry I did not get back on here sooner, but I've been busy with other things.

I just tried what you said. In CUPS, I click 'Manage Printers', and click the printer name. Under this, I see 'Driver:Brother FAX-1860C CUPS  v1.1 (color)'.  I click 'Modify Printer' and this brings me through a few pages until I finally get to a driver list. There is only 1 driver listed for this printer (the current one), and I don't see anything about color or greyscale near it (it says Current Driver - Brother FAX-1860C CUPS v1.1). There are no other options I can find regarding the color.

So, now I go to System->Administration->Printing and look under Properties->Printer Options as you said. I see 'Color/Greyscale' with a dropdown box, and select Greyscale. I click apply, close the window and re-open to confirm the change saved (it did). I then go to print a document, and when the print box pops up, I once again check and it does say greyscale. I print, and get a color printout.

Any other suggestions? My printer is worthless at this point as I'm not buying color ink for it (way too expensive). If it matters, I've upgraded to Lucid Lynx and the problem still persists.

Thanks for the help.

---

### Post by quixote on 2010-05-14
I wonder, could this be something the printer is doing, rather than Ubuntu?  It has some sort of onboard menu or something, right?  See if there are any settings under Ink or Color or Graphics or Print Quality or something.  Also, what would happen if you simply removed all the color print cartridges?  Maybe it would default to grayscale??  (Not very likely, I know.)

---

### Post by hesth on 2010-08-15
Hi, I have the same problem here. I have tried editing the cups at Localhost as suggested - I pointed it to the ppd file in case it was not going to the right place. No luck. Any suggestions? 

Thanks

---

### Post by kellymartinv on 2010-08-30
Same exact problem for me too. I have a Brother MFC 440CN that refuses to print grayscale, despite my programs and the control panel/etc, everything is set to B&W. It's a new thing since around 9.10 to 10.04, because i never had this problem back when i was using 6 and 7.

---

### Post by copycat on 2011-04-08
same here no grayscale possible on MFC 440CN.  I think it started on Karmic... not sure anymore.

---


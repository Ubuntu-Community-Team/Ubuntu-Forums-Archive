---
title: "Resolution Problem - displays OK in Lucid but not in Meerkat not"
date: 2010-10-29
forum: General Help
---

### Post by Scunnered on 2010-10-29
I am experiencing difficulty with the screen resolution on my Asus X51L laptop. Currently I am using Lucid and everything works perfectly but when I attempted to dual boot Meerkat the screen went out of sync.

I have tried Meerkat both as a live CD and a full install and in both instances the display does not fill the screen. I attach a photo of the display in the hope that it will assist.  

When I use the laptop at home I attach it to a 21 inch screen and everything works a treat and strangely enough when working with Meerkat and displaying it on the large screen it will properly display. This only confuses me further.

I am due shortly to go for a trip and as the display is not correct am not prepared to show Ubuntu as being improperly displayed to others. 

I wish to take the benefits of the latest version and would appreciate your kind assistance in the matter.

---

### Post by bobcollard on 2010-10-29
> **Scunnered said:**
> I am experiencing difficulty with the screen resolution on my Asus X51L laptop. Currently I am using Lucid and everything works perfectly but when I attempted to dual boot Meerkat the screen went out of sync.

I have tried Meerkat both as a live CD and a full install and in both instances the display does not fill the screen. I attach a photo of the display in the hope that it will assist.  

When I use the laptop at home I attach it to a 21 inch screen and everything works a treat and strangely enough when working with Meerkat and displaying it on the large screen it will properly display. This only confuses me further.

I am due shortly to go for a trip and as the display is not correct am not prepared to show Ubuntu as being improperly displayed to others. 

I wish to take the benefits of the latest version and would appreciate your kind assistance in the matter.
The problem is with the display manager.  You have to uncheck Mirror, click find displays, click on the laptop display and turn it off, then move the display resolution to the size of the external monitor.  I have the same problem, but, the Power manager will not let me close my laptop without killing whatever display is showing.  To get past this I use Xubuntu instead of Ubuntu.  XFCE4 Power manager has the option of Do Nothing when laptop is closed while Gnome Power Manager does not.

---

### Post by Scunnered on 2010-10-30
Many thanks Robert for your reply.

It is not a problem of using a mirror image on the large screen but the reverse.  Using 10.04 it will properly display using the native resolution of 1024 x 768 but will not do so in 10.10.  I have no problem if I close the lid on my laptop and only use the large screen.

I posted the photo showing both screens side by side to explain the problem better but it appears to have had the opposite effect.

When I use the laptop in a stand alone situation there is no problem with 10.04 but with 10.10 it displays as shown.  This is the effect that I seek to have resolved.

I keep singing the praised of Linux and Ubuntu in particular but I don't want to show it off in a bad light which would happen if I were to use 10.10 when it will not properly display on screen.

I hope this assists in clarifying matters.

Again my thanks for your input to my problem

---

### Post by Scunnered on 2010-11-01
Anyone able to offer a solution ??

---

### Post by bobcollard on 2010-11-01
> **Scunnered said:**
> Anyone able to offer a solution ??
Try setting a different resolution for the laptop?

---

### Post by Scunnered on 2010-11-01
Many thanks Robert.

I have had a look at your suggestion and find that other than the native resolution I am offered 800 x 600 or 640 x 480.  In each instance neither setting improved the view.  The screen still displayed as shown.

What should be an extremely simple matter to get right seems to beyond the developers of 10.10.  How can we expect to convert others to use Ubuntu when such a simple presentational matter can't be properly addressed.

It looks very much like I shall have to seek another OS if something is not done PDQ.

Again my thanks for your assistance

---

### Post by bobcollard on 2010-11-01
To get a higher resolution you have to drop the refresh rate, sorry, should have mentioned that.

---

### Post by Scunnered on 2010-11-01
Thanks again Robert

I have the options of 60, 70 & 75 Hz with the rotation set as normal.  No matter which I pick there is no change in the resolutions offered.

I have added this problem to launchpad in the hope that something positive will result.

Lets hope this works.

---

### Post by Scunnered on 2010-11-03
I spotted that the latest Ubuntu User magazine had a dual sided DVD with both Ubuntu & Kubuntu 10.10 so bought it.  I had hoped that perhaps that Kubuntu might work but everything appeared as before.

Looks very much like my lucky white heather is having a holiday.

Still no further forward and can only hope that this assists in finding a solution to this problem.

---

### Post by bobcollard on 2010-11-03
Try this.
[http://ubuntuforums.org/showthread.php?t=155746](http://ubuntuforums.org/showthread.php?t=155746)

---

### Post by Scunnered on 2010-11-04
Many thanks Robert

I am not worried about dual monitors. My concern is that the laptop will not properly display.

I added the additional information as I had directed others to the post and wished to show that with Kubuntu it did not work.

---

### Post by Alan F on 2010-11-04
The 2nd post in this thread ...

[http://ubuntuforums.org/showthread.php?t=1600512](http://ubuntuforums.org/showthread.php?t=1600512)

may provide the answer?

---

### Post by Scunnered on 2010-11-04
Alan F

Thanks very much for your advice.  

Could I refer you to my first post in which I was attempting to highlight that the display on my laptop did not fully populate the screen.  If I attach it to a large monitor it properly displays.

So far I am still using 10.04 as it properly displays. What I am seeking is to have the latest offering 10.10 display as it should and not as shown in my first port.

Any further assistance you can offer will be appreciated.

---

### Post by Alan F on 2010-11-04
From the pictures posted you need a different resolution on the laptop from that used on the external monitor.

To allow this you must have 'same image in all monitors' unchecked. This was the point of the referenced link above.

---

### Post by Scunnered on 2010-11-04
Alan  F

I am only concerned with the fact that the laptop will not correctly display when using 10.10.  Using 10.04 the screen displays side to side on the laptop as shown on the larger monitor but 10.10 does not do so.

I take the laptop away from home with 10.10 in its present form it does not in any way show how good Ubuntu is.  

How may I get 10.10 to properly display on the laptop

---


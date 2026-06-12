---
title: "how do you stop the panel &quot;doubleing&quot; when you increase it in size"
date: 2011-02-25
forum: General Help
---

### Post by Spyderkid on 2011-02-25
how do you stop the panel "doubleing" when you increase it in size
(attachment below of what i mean)

*thanks!*

---

### Post by Spyderkid on 2011-02-26
Anyone?

---

### Post by Spyderkid on 2011-02-26
any ideas at all?

---

### Post by flipper T on 2011-02-26
cannot replicate your problem

i assume that you are just right clicking on it to inc size & not something more esoteric ?

---

### Post by llawwehttam on 2011-02-26
Its down to the theme you're using. People used to have this problem all the time. Use a more up-to-date theme.

---

### Post by flipper T on 2011-02-26
a pic of my panel looking v big :)

---

### Post by hyperdude111 on 2011-02-26
It's because of the theme your using,if you want you can "hack" the panel out of the theme.

Follow this guide "http://www.omgubuntu.co.uk/2011/02/gnome-panel-transparency-fix-ubuntu/" 

however that will leave you without the nice panel (only white background) so you'll have to apply your own custom background to the panel.

---

### Post by Spyderkid on 2011-02-27
I'm using ambience its my fav theme

---

### Post by WorMzy on 2011-02-27
[http://www.webupd8.org/2010/05/fix-transparent-vertical-and-large.html]("http://www.webupd8.org/2010/05/fix-transparent-vertical-and-large.html")

---

### Post by Spyderkid on 2011-02-27
I did what it said on the link 
[http://www.omgubuntu.co.uk/2011/02/gnome-panel-transparency-fix-ubuntu/](http://www.omgubuntu.co.uk/2011/02/gnome-panel-transparency-fix-ubuntu/)


but i don't understand what it means by:
"Note that in order for the panel background to adhere to the &#8216;system theme&#8217; you will need to remove the &#8216;#&#8217; from the beginning of the same line in the same file."

---

### Post by Spyderkid on 2011-02-27
A log in and out mostly fixed it, however the greyish background still remains behind the indicator applet (messages and sound app) only when you have the use system theme box ticked and the clock has gone a tad weird aswell but appart from that its fine

---

### Post by Spyderkid on 2011-02-27
still dont understand the
"Note that in order for the panel background to adhere to the &#8216;system theme&#8217; you will need to remove the &#8216;#&#8217; from the beginning of the same line in the same file."
thing I posted about before.

---

### Post by wiggly81 on 2011-02-27
its because the panel.png image is the exact size of the original panel if you make this image bigger then u wont get the double problem, it can stretch left to right but not top to bottom

for Ambiance go to 
/usr/share/themes/Ambiance/gtk-2.0/apps/img/panel.png

you will need to change the height of the other panel-*.png files aswell

Hope this helps

---

### Post by Spyderkid on 2011-02-27
I did what you said before this thread, it didn't work.

---


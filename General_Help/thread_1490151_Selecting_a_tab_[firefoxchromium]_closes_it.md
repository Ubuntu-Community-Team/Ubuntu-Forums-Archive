---
title: "Selecting a tab [firefox/chromium] closes it"
date: 2010-05-21
forum: General Help
---

### Post by perlsys on 2010-05-21
Sometimes when I select a different tab in Chromium or Firefox the tab gets closed or killed

Did anyone observed or had the same problem. 
Can this be fixed?

---

### Post by cosmicbuff on 2010-05-22
not in ubuntu , but experiencing in my mandriva system (2.6.33.4) . I have no clue why its hapening.

---

### Post by perlsys on 2010-05-22
I do get a lot of errors related to gtk when i open chromium from the command line

I thinking its probably a gtk bug. 
Also note that i installed from ubuntu 10.04 beta and later upgraded, it is possible i did not upgrade correctly

---

### Post by lovinglinux on 2010-05-23
Firefox doesn't have a different process for each tab, so if the tab content crashes, the entire browser crashes. Is this what is happening with Firefox or the tab is just closing?

What Firefox version you are using? Does it happens on any pages or just on pages with flash content?

---

### Post by perlsys on 2010-05-23
the tab just closes in firefox.
the behavior is identical to what i get from chromium

---

### Post by perlsys on 2010-05-23
this could be useful
here is the error output i get from firefox and chromium

firefox
> (firefox-bin:2417): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2417): Gdk-WARNING **: XID collision, trouble ahead

(firefox-bin:2417): Gdk-WARNING **: XID collision, trouble ahead

chromium
> (exe:2739): Gdk-WARNING **: XID collision, trouble ahead

(exe:2739): Gdk-WARNING **: XID collision, trouble ahead

(exe:2739): Gdk-WARNING **: XID collision, trouble ahead

---

### Post by lovinglinux on 2010-05-23
> **perlsys said:**
> the tab just closes in firefox.
the behavior is identical to what i get from chromium

Check if you have a problem with your mouse or if you are not clicking the tab with the middle-mouse-button by accident. Left-mouse-button selects the tab, middle-mouse-button closes it.

> **perlsys said:**
> this could be useful
here is the error output i get from firefox and chromium

firefox


chromium


Those are just common warnings and most likely nit related to your problem.

---

### Post by perlsys on 2010-05-23
> **lovinglinux said:**
> Check if you have a problem with your mouse or if you are not clicking the tab with the middle-mouse-button by accident. Left-mouse-button selects the tab, middle-mouse-button closes it.


It a laptop Asus A52F. I am using the touch pad, it could be that the touch pad is messing up. 
I have also been facing several issues typing, the cursor would suddenly jump to another point in the screen and doing all sorts of crazy stuff!!!

i should probably find a way to disable the touchpad for a while and see what happens

---

### Post by lovinglinux on 2010-05-23
> **perlsys said:**
> It a laptop Asus A52F. I am using the touch pad, it could be that the touch pad is messing up. 

Most likely, because if it was a crash problem, Firefox would crash entirely, not a just a tab. The same doesn't happen with Chrome, which has separate process for each tab, so a crash would also just close the tab. Anyway, Firefox's behavior is what makes me conclude that is a touch pad issue.

> **perlsys said:**
> I have also been facing several issues typing, the cursor would suddenly jump to another point in the screen and doing all sorts of crazy stuff!!!

i should probably find a way to disable the touchpad for a while and see what happens

Yes, that will probably stop these issues.

---

### Post by cosmicbuff on 2010-05-24
happens only with my touchpad, not with mouse. 

In a completely distro with 2.6.34.8 ,have the same issues.tabs closing suddenly when u select them. And sometime left will paste cli[board contents.

I think all the distros with latest kernel will have this issue. need to look up for bug reports.

---


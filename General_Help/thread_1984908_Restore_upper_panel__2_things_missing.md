---
title: "Restore upper panel / 2 things missing"
date: 2012-05-22
forum: General Help
---

### Post by Myname22 on 2012-05-22
Hello,

I'm using Xubuntu 12.04. In my upper panel next to the weather applet, date and time etc. I'm missing 2 pictogramms:  sound + the e-mail enveloppe.

It has to be like this: [http://linux.softpedia.com/progScreenshots/Xubuntu-Precise-Pangolin-Screenshot-77002.html](http://linux.softpedia.com/progScreenshots/Xubuntu-Precise-Pangolin-Screenshot-77002.html)

How can I get them back? Or how can I restore my complete upper panel (like it is after a new install)?

Hope someone can help. Thanx!

(Edit: I tried to install another (than standard) weather applet today,  including a pictogramm on the upper panel. I removed it after a while  and probably I/it also corrupted/removed (?) the other 2 pg's.)

---

### Post by cortman on 2012-05-22
Right click the panel, hover over "Panel", select "Add New Items".

---

### Post by Myname22 on 2012-05-22
Thanks for your quick reply cortman!

I've tried what you suggested (tried it before already). 

But in the "add new items" list, I don't find the 2 correct pictograms (no sound or the (correct) e-mail enveloppe). 

What's it called in your list?

---

### Post by cortman on 2012-05-22
The sound applet is called "mixer", and the mail indicator is probably called something similar. If it isn't on your list you can install it with

```
sudo apt-get install indicator-messages
```

---

### Post by Myname22 on 2012-05-22
My system is in another language, so it's useless to know what it's called at your computer. Smart... sorry, my fault :).

Anyway, I'm sure those 2 pictogramms are dissapeared from my add new items list. And I don't see something similair either.

If I insert your command in the terminal, it says something like:  indicator messages are up to date and already installed.

I tried to install another (than standard) weather applet today, including a pictogramm on the upper panel. I removed it after a while and probably I/it also corrupted/removed (?) the other 2 pg's.

Now what? Is there another way to restore the upper pannel to default? or to get those pg/s back? or maby reset the panel? or to reset the add new items list?

Complicated. After 1,5 day I was almost ready with installing a new xubuntu 12.04. Hope I don't have to start all over again, because of this. Any help welcome...

---

### Post by Rodney9 on 2012-05-22
I had these disappear after yesterdays update, after 2 reboots all was back to normal.

Rodney

---

### Post by rai4shu2 on 2012-05-22
Right-click panel, select Panel/Add New Items, then select Indicator Plugin. That should give you the missing applets.

---

### Post by Myname22 on 2012-05-22
@Rodney9: tried several reboots. Nothing changed. 


@rai4shu2: Love you :p ... this worked and saved me a lot of time reinstalling etc. They were  still in my add new items list, but I didn't new the correct name.  They are also 2 in 1 and not seperate. So "Indicator Plugin" brings back both of them.

They (mixer + mail indicator) are both back on my upper panel now! Oef, happy again :D

**_SOLUTION_** in my case: see @rai4shu2.

Thanx for your help everyone!!

---


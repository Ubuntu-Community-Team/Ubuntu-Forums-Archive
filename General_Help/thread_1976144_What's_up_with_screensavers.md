---
title: "What's up with screensavers?"
date: 2012-05-08
forum: General Help
---

### Post by geovino on 2012-05-08
It seems that Ubuntu doesn't want to be bothered with screensavers anymore. I know they are not important, but they are nice. Now after installing 12.04 you find there is no screensavers, but you have to uninstall gnome-screensaver, and then install xscreensaver. Why? 

Then everytime I go to screensaver I get this:

Warning:
The XScreenSaver daemon doesn't seem to be running
on display ":0".  Launch it now?

What causes this? How to solve this error? 

I've turned off screensavers for now until I can fix this problem. 

Thanks.

---

### Post by Enigmapond on 2012-05-08
If you are going to use xscreensaver, purge the other, the daemons conflict. Then just add a startup command for xscreensaver to start at login. The command would be xscreensaver -nosplash

---

### Post by geovino on 2012-05-08
> **Enigmapond said:**
> If you are going to use xscreensaver, purge the other, the daemons conflict. Then just add a startup command for xscreensaver to start at login. The command would be xscreensaver -nosplash

I did that, as per: [http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/)

but I still get that error.

---

### Post by rickaron on 2012-05-24
I followed the same instructions and have the same problem. Strange!

---

### Post by zombifier25 on 2012-05-24
Instead of following the above tutorial, I simply added xscreensaver -no-splash to Startup Applications. Done.

---

### Post by peterx14 on 2012-07-01
> **rickaron said:**
> I followed the same instructions and have the same problem. Strange!

And me too. However (queue drum-roll), I know why!

Despite there being quite a lot of articles/forums posts about how to install screensavers for Ubuntu 12.04, a [surprisingly high]("http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/") [number of them]("http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-desktop-essentials/") [all contain]("http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html") [the same mistake]("http://www.thelinuxgeeks.info/how-to-install-xscreensaver-in-ubuntu-12-04/"); where they say to paste into the /etc/xdg/autostart/screensaver.desktop file, they spell the word "Application" wrongly as "Applicaton" which seems to prevent it from auto-starting!

There's clearly a conspiracy going on!!! Or a lot of people copy content from other sites without testing it first.

---

### Post by Orvis4wt on 2012-07-02
I'm a Newbie and having the same trouble. I installed the xscreensaver and then I was getting the error below. 

The XScreenSaver daemon doesn't seem to be running
on display ":0".  Launch it now?

I added the startup to applications and the error went away but now when I open the screensaver it just freezes.. any help to even get it to function at all would help.. thaks

---

### Post by Jan Greeff on 2012-07-10
Where do I find this misspelt file to correct, please? 


> **peterx14 said:**
> And me too. However (queue drum-roll), I know why!

Despite there being quite a lot of articles/forums posts about how to install screensavers for Ubuntu 12.04, a [surprisingly high]("http://www.liberiangeek.net/2012/04/add-enable-screensavers-in-ubuntu-12-04-precise-pangolin/") [number of them]("http://www.sitepoint.com/ubuntu-12-04-lts-precise-pangolin-desktop-essentials/") [all contain]("http://www.noobslab.com/2012/04/important-things-to-do-after-install_26.html") [the same mistake]("http://www.thelinuxgeeks.info/how-to-install-xscreensaver-in-ubuntu-12-04/"); where they say to paste into the /etc/xdg/autostart/screensaver.desktop file, they spell the word "Application" wrongly as "Applicaton" which seems to prevent it from auto-starting!

There's clearly a conspiracy going on!!! Or a lot of people copy content from other sites without testing it first.

---

### Post by peterx14 on 2012-07-10
> **Jan Greeff said:**
> Where do I find this misspelt file to correct, please?
/etc/xdg/autostart/screensaver.desktop

---

### Post by Jan Greeff on 2012-07-10
Many thanks peterx14. Must say I was quite chaffed, found this command before you replied, ran it, corrected the spelling error and presto! Problem solved!

---


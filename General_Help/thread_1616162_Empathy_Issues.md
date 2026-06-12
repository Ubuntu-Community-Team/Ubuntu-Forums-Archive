---
title: "Empathy Issues"
date: 2010-11-07
forum: General Help
---

### Post by miststlkr on 2010-11-07
I haven't been able to get sounds out of Empathy since I installed [running 10.04] and decided today was the day to fix this.   I looked on google and found some older threads, one suggested that I add a package and did, with no visible [nor audible] effect.  Another suggested adding the PPA and update from there, which sounded like a good idea and it came up with several updates so I installed them.  Now not only do I not have sound, but I have the Empathy green speech bubble in the notification area and Empathy has stopped using the messaging part of the indicator applet.  How might I go about, at the very least, fixing Empathy to use the messaging indicator, the way it did "out of the box"?

I'd like to get the sounds working too, if anyone has a suggestion there as well.

Ubuntu 10.04, all other sound-producing apps work fine as far as I can tell but Empathy hasn't from day 0.

---

### Post by cipherboy_loc on 2010-11-07
> **miststlkr said:**
> I haven't been able to get sounds out of Empathy since I installed [running 10.04] and decided today was the day to fix this.   I looked on google and found some older threads, one suggested that I add a package and did, with no visible [nor audible] effect.  Another suggested adding the PPA and update from there, which sounded like a good idea and it came up with several updates so I installed them.  Now not only do I not have sound, but I have the Empathy green speech bubble in the notification area and Empathy has stopped using the messaging part of the indicator applet.  How might I go about, at the very least, fixing Empathy to use the messaging indicator, the way it did "out of the box"?

I'd like to get the sounds working too, if anyone has a suggestion there as well.

Ubuntu 10.04, all other sound-producing apps work fine as far as I can tell but Empathy hasn't from day 0.

I cannot post any screenshots now, but if you go under edit, there should be a menu option called "preferences" make sure sound is turned on there. The bubble notifications should be in the same place as the sound stuff. 

Also make sure that under sound preferences, the sound themes are turned on. Please post the repo's info so I can try it.




Cipherboy from a jailbroken iPod touch, 3rd gen.

---

### Post by miststlkr on 2010-11-07
Yes,  the sounds are turned on in Empathy's settings.

The package that I saw kicking around was called sound-theme-freedesktop and for the PPA I used ```
sudo add-apt-repository ppa:telepathy/ppa && sudo aptitude update
```


[EDIT]

In fact, I just rebooted and now the option to chat is not even displayed in the messaging center, I only have "set up mail" and "broadcast" displayed now.

[/EDIT]

---

### Post by cipherboy_loc on 2010-11-07
Here is what I did to fix this issue:


Open up gnome-control-center (Enter that into the run dialogue (found at alt+f4) or into a terminal). Scroll down until you find a button called sound and click it. Make sure the window looks like the one attached.




Cipherboy

---

### Post by miststlkr on 2010-11-07
other than the fact that I don't have an "unamplified" mark on my volume bar, my settings are the same.

---

### Post by cipherboy_loc on 2010-11-08
What version of empathy are you using? After updating, I have:

[SIZE=6]Empathy 2.32.0.1[/SIZE]

I cannot think of anything else that might help, other than re-installing (after purging) Empathy.


Cipherboy

---

### Post by miststlkr on 2010-11-08
Odd, I have 2.30.2 and Synaptic says I don't have anything to update.   Equally odd is that, while working on my xorg.conf I had to reboot a few times and noticed today that my sounds in Empathy started working somewhere along the way.  Equally odd, though possibly related to the X changes I had made last night, is that the icons on the panel are displaying oddly now, as shown below, but weren't previously.  The new icon oddities aside, do you happen to know how I can get Empathy back into the messaging indicator as it comes default in ubuntu, rather than have the green speech bubble?

[IMG]http://img.photobucket.com/albums/v205/miststlkr/screenshot.png[/IMG]

---

### Post by miststlkr on 2010-11-08
Working on the answer to my question about the indicator, I was able to stuff Empathy back in its box by following [this post]("http://ubuntuforums.org/showpost.php?p=8646821&postcount=1%22"), but as soon as I get a message, it pops back out and the message indicator stops turning green for it.[URL="http://ubuntuforums.org/showpost.php?p=8646821&postcount=1%22"]
[/URL]

---


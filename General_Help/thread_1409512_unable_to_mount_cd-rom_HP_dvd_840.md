---
title: "unable to mount cd-rom HP dvd 840"
date: 2010-02-17
forum: General Help
---

### Post by smvarner on 2010-02-17
i'm new to ubuntu and can't get the cd-rom to work. all it  is gives is an error. it says 
    unable to mount cdrom0     mount: special device /dev/scd0 does not exist.
  please help me if more info is needed let me know 
the cd-rom is a HP dvd 840 on a compaq presario sr1800nx

---

### Post by jamesisin on 2010-02-17
What is the output of this command?

```
ls /dev | grep cd
```

---

### Post by smvarner on 2010-02-17
> **jamesisin said:**
> What is the output of this command?

```
ls /dev | grep cd
```
 
what do you mean??

---

### Post by jamesisin on 2010-02-17
Open a terminal, enter that command, and paste the response [NOPARSE]```
between code brackets such as these
```[/NOPARSE] in a reply.

Applications &#8212;> Accessories &#8212;> Terminal

---

### Post by smvarner on 2010-02-18
> **jamesisin said:**
> Open a terminal, enter that command, and paste the response [NOPARSE]```
between code brackets such as these
```[/NOPARSE] in a reply.

Applications ?> Accessories ?> Terminal


I didn't know you could do that. I got it to work lastnight wheni noticed that on the back of the cd-rom it has a selecter. That says cable select, slave, and master. it was on slave i moved the little green thing to master and now it works. 
 But when the music player is open when i try to click on something like play the window jumps up and down and won't let me click on what i want just whatever is there when it moves. not everything douse this is there a setting i need to change? thanks for you help.

---

### Post by jamesisin on 2010-02-18
The terminal (shell) is your friend.  You can fix a lot of problems and discover a lot of information through it.

So you have an IDE connected CD drive (wide ribbon cable).  If you attach a hard drive to the same IDE channel (same ribbon cable, they typically have two places to attach devices) you will run into a problem because usually the hard drive wants to be Master.  If you use Cable Select, the device at the end of the cable (furthest from the mother board) is the Master and that is where you should attach the hard drive (both would need to be set to Cable Select).  For now though you should be fine.  Here is a post about adding additional hard drives:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

As to your other issue, I don't have a clear picture what is happening yet.  Nautilus is the name of the file browser (those windows which show folder contents, for example).  Are you saying that with certain views in Nautilus when you double-click on something you encounter a problem?

It seems that you could also be seeing an issue because Compiz (which runs the more interesting visual effects for Gnome) is trying to snap a window into a particular location on the screen but is having difficulty doing so.  Does this happen when the window is snapped to the bottom of the screen?

---

### Post by smvarner on 2010-02-19
[SIZE=2]This sounds like my problem. But i don't have to double-click for it to happen. It snaps to the bottom and then back to the top when i try to click again. It started this when i trying to use the music player. Also my cd-rom is on another cord from the hard-drive. The hard drive is by it's self. The cd-rom was the second one in another tower i reused it. [/SIZE]
 
 
 
 
 
[SIZE=2]It seems that you could also be seeing an issue because Compiz (which runs the more interesting visual effects for Gnome) is trying to snap a window into a particular location on the screen but is having difficulty doing so. Does this happen when the window is snapped to the bottom of the screen?[/SIZE]

---

### Post by jamesisin on 2010-02-19
Of course you can turn off Compiz and this should stop that behavior, but that's not a very fun solution.

When I have a window which does this spaz-attack, I roll it up and back down.  This forces the window into a specific location and it stops bouncing about.  You can try this to see if it settles matters for you.

To turn on roll-up (double-click on title-bar and window rolls up like a shade), go into System &#8212;> Preferences &#8212;> Window and select "Roll up" from the Titlebar Action drop-down (Double-click titlebar to perform this action:\).

Let me know how this tests out.

---

### Post by smvarner on 2010-02-19
[SIZE=2]Thanks for you're help. I now got the problem solved. everything is working good now. [/SIZE]:popcorn:

---

### Post by jamesisin on 2010-02-19
Oh?  What was the solution?

---

### Post by smvarner on 2010-02-20
I'm not sure what i did. But when i turned it back on to try what you said it work fine.   

Do you know what this means? 

974.234784] end_request: I/0 error, dev sr0 , sector 1288092

976.776574 restarting system. 

That's what it said after install of ubuntu 9.04. It did start when i pushed the power button and turned it back on. It is on another compaq presario sr1303wm. If it works i was thinking about useing it has a second hard-drive on my other computer. It's a 40gb not sure what brand.

---

### Post by jamesisin on 2010-02-20
I/O errors can often be indicative of hard ware issues.  This drive may be moaning in a hospital bed waiting to die.  Or it could have been an anomaly.  But hard drives are cheap and a 40 GB hdd is really small.  If you want a second drive buy a new one.  But rip the old hdd apart and use its magnets as refrigerator magnets.

---

### Post by smvarner on 2010-03-02
[SIZE=2]Sorry i took so long to get back with you. I'm giving that other computer to my mom the small hard-drive won't matter. Would have written back sooner but my dog got sick. thanks for you're help  [/SIZE]

---

### Post by jamesisin on 2010-03-03
Good enough then.  Glad to have been of service.  Sorry about your dog.

---


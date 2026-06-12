---
title: "please help a newb! : )"
date: 2009-12-02
forum: General Help
---

### Post by black28 on 2009-12-02
hey guys, I was wondering how to change the display settings. i've searched and youtubed it and its all on (displayconfig-gtk) but it can't be found. is there any way I can go higher than the 800x600 I have right now? please help out.

---

### Post by fcuk112 on 2009-12-02
are you using nvidia?  in that case you can use the nvidia X server settings from your system > administration menu.

---

### Post by oldsoundguy on 2009-12-02
first off "please help" won't get you much help.  You have to put your problem in the title to get best results.

Second .. you should list your video display set up .. are you using a card?  or on board chip?  What is the chip being used (intel, nvidia, ati, ????

You may have to install restricted drivers from the restricted drivers repository.

---

### Post by jbrown96 on 2009-12-02
Most likely you need to install a graphics driver. 
1) Add the restricted repositories in Synaptic. System-->Admin-->Synpatic, then Settings-->Repositories. Make sure that all the repositories (like universe, multiverse, etc.) are enabled. Click ok, then click the reload button in Synaptic. Close Synaptic when this is done.
2) Install your graphics driver. System-->Admin-->Hardware drivers. Install the graphics driver and reboot.

If there are no drivers available, then we need to know your graphics card. Open a terminal (apps-->accessories-->terminal) and post the output of ```
lspci | grep VGA
```

---

### Post by spiderbatdad on 2009-12-02
ditto

---

### Post by black28 on 2009-12-02
thanks guys, well im not quit sure about the card. its a HP 521C I got from a friend that was crashed. it supported the 1024x600 when I used Puppy Linux. I tried administration and display settings but the highest I got was 800x600. im using a 19'' flat screen samsung monitor. just looking for some walkthroughs because im still fairly a newbie to linux and don't want to mess up and crash.

---

### Post by black28 on 2009-12-02
this is the output of code 
lspci | grep VGA01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i1 (rev 6a) where do i go from here?

---

### Post by oldsoundguy on 2009-12-02
the first thing I learned on a NEW install box is do NOT put anything critical on it until you get it set up and tweaked exactly the way you like it.  BECAUSE, if you upscrew something that crashes it or of you really do not LIKE what you have done, cleaning it up or even going back to point A and re-installing is NO BIG DEAL.  
You will not destroy your hardware, so flog away!!

(and the more you do so, the more you learn!)

---

### Post by black28 on 2009-12-02
true, i havent done much really accept make some desktop icons and a new desktop background. any tips on where to go from that code output?

---

### Post by black28 on 2009-12-02
anybody?

---

### Post by jbrown96 on 2009-12-03
I have never heard of a trident graphics card. I searched google, and there seem to be many others that have similar problems. I didn't stumble across anything solutions right away.

---

### Post by oldsoundguy on 2009-12-03
Doubt that you will find drivers for a card made by a company that is no longer in business

[http://www.google.com/search?q=trident+graphics&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=trident+graphics&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Best to replace the card with a known manufacturer.

Even WINDOWS will dump that card if it has not done so already!

Trident used to make a lot of things for HP including dial-up WinModems and some really FUNKY sound cards. 
I have pulled Trident crap out of many an HP and replaced it with stuff that works.

---


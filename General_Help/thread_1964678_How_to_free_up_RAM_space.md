---
title: "How to free up RAM space?"
date: 2012-04-24
forum: General Help
---

### Post by onebonetune on 2012-04-24
The normal thing is... when you close the aplications they must immediately free space on the ram. Isn't that true? But it seems it is not happening in my computer...
> gilmar@gilmar-desktop:~$ free -tom
             total       used       free     shared    buffers     cached
Mem:          3962       3869         93          0         53        375
Swap:         5884         24       5860
Total:        9847       3893       5953
[IMG]http://www.flickr.com/photos/79416317@N03/6963303946/[/IMG]

[System Monitor ]("http://www.flickr.com/photos/79416317@N03/6963303946/")

[IMG]http://www.flickr.com/photos/79416317@N03/6963303946/[/IMG]

---

### Post by GreatDanton on 2012-04-24
Some applications like Open office, or Libre office has the function to enable that the application immediately free the ram space. In Open office that option is under : Tools/Options/Memory. Then look for the option: **remove from memory after**. 
However this is not the solution of your problem, but it can save you little ram especially if you are working on old computer.

Cheers

Edit: I didn't see the picture you provided. As far as i can see you didn't close the programs (they are still running in the background). Right click on the the little icons on the top of the screen and chose exit from the menu.

---

### Post by onebonetune on 2012-04-24
I have 4gb Ram and after a little in the startup the amount of used memory reachs 90%...
Help please!

---

### Post by Cheesemill on 2012-04-24
What is the output of:
```
free -m
```

You may be getting confused between used RAM and cached RAM.
Unused RAM is wasted RAM!!

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by onebonetune on 2012-04-24
Code:
> gilmar@gilmar-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       3684        277          0         54        337
-/+ buffers/cache:       3292        669
Swap:         5884        197       5687
gilmar@gilmar-desktop:~$ 

It says I have a total of 3962, 3684 being used and just 277 are free...

---

### Post by JC Cheloven on 2012-04-24
Hi, 

From your former picture, it's evident, at least in my opinion, that you have a problem. Gnome panel using about 1Gb ram is crazy. Nautilus and firefox also use much more ram than expected (well for normal usage). And it's not about using as cache, which would be fine.

And that wnck-applet ... it has a known memory leak bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/576751](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/576751)

It probably has the culprit. You may try to turn it off. Or at least take that as a starting point for further investigation.

Hope this helps
JC

---

### Post by MonkeyPaw on 2012-04-24
It does appear you have an issue with something leaking memory. Especially if a reboot doesn't cure you.

As others have said, Ubuntu (and other distros) caches previous data in RAM for later (re)use. This is why Firefox takes a few seconds to open after a reboot, but only 1/2 second the next time you open it. In the event a new application needs the RAM, the cached data is dumped as needed. It's totally a good thing, or otherwise you'd never see the advantages of more RAM unless you dealt with really really large files or had 20 things open at once.

---

### Post by onebonetune on 2012-04-25
I have just turned on the computer, closed the applications that started with the system and see how it appears:
```
gilmar@gilmar-desktop:~$ free -tom
             total       used       free     shared    buffers     cached
Mem:          3962       1959       2003          0        348        730
Swap:         5884          0       5884
Total:        9847       1959       7888
gilmar@gilmar-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       1955       2006          0        348        730
-/+ buffers/cache:        877       3085
Swap:         5884          0       5884
gilmar@gilmar-desktop:~$ 

```

---

### Post by JC Cheloven on 2012-04-25
That's much closer to normal, 877Mb of true 'use'.

Is it wnck-applet among those apps 'that started with the system', which you closed?

Does that figure (877Mb, which is that matter, in red below) evolve significantly after opening and then closing applications?

```

             total       used       free     shared    buffers     cached
Mem:          3962       1955       2006          0        348        730
-/+ buffers/cache:        [COLOR="Red"]877[/COLOR]       3085
Swap:         5884          0       5884

```

---

### Post by onebonetune on 2012-04-25
I disabled transparency on the gnome panel... I am using system color now... 
```
gilmar@gilmar-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       3876         85          0        299       1344
-/+ buffers/cache:       2232       1729
Swap:         5884          0       5884
gilmar@gilmar-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       3867         94          0        210       1246
-/+ buffers/cache:       2411       1551
Swap:         5884          0       5884
gilmar@gilmar-desktop:~$ 

```
It seems things are better now:
[http://www.flickr.com/photos/79416317@N03/6966701154/]("http://www.flickr.com/photos/79416317@N03/6966701154/")

---

### Post by JC Cheloven on 2012-04-25
I see. Somehow better, but still not fine.

As you may have seen in the link I suggested, people reports different degrees of success with different actions: 
- One is to not use transparency in the panel, as you already did. 
- Another one is to not use the autohide feature (are you using it?)
- Another one is to not use the Windows List applet. Unfortunately this is something the user usually wants.
- Another one is to use a different theme, NOT Ambience or Radiance. 
- Yet another one is reprofiling at boot. You could try that. Instructions [here]("http://ubuntuforums.org/showthread.php?t=254263") (if you're impatient, just scroll to the "how do I do it" section). Quite easy.

Hope some of the above helps. 
BTW, AFAIU this whole thing is about gnome 2. What ubuntu version are you using, 10.04? Perhaps you'll be using gnome3 soon (Ub 12.04) and the issue will be solved automagically ;)

Cheers
JC

---

### Post by onebonetune on 2012-04-26
The memory usage increased again:
```
gilmar@gilmar-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       3927         34          0         16        206
-/+ buffers/cache:       3704        257
Swap:         5884        154       5730
gilmar@gilmar-desktop:~$ 

```
[Print Screen of the System Monitor]("http://www.flickr.com/photos/79416317@N03/7116592427/")
What is that wnck-applet for? Can I disable it?

---

### Post by JC Cheloven on 2012-04-26
> 
What is that wnck-applet for? Can I disable it?
I'm afraid you don't want to do that. It controls your panel (or at least a good deal of things you use the panel for). You'll see that if you kill the associated process wnck-applet (you can do that from the 'system monitor'), some things get unusable in the panel, and if you restore them, the wnck-applet process will start again. 

Your best bet (as for my knowledge so far) is to see if some of the tricks mentioned in my previous post fix your problem. 

Not a 'fix', but if you don't get it fixed, and you're still interested in running an older version of ubuntu (again what is it?), you can use a different desktop environment. I use mainly lxde (LUbuntu), and xfce (XUbuntu) is also nice...

JC

---


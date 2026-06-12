---
title: "Scary crashing........"
date: 2011-11-30
forum: General Help
---

### Post by darkvoid86 on 2011-11-30
[ATTACH]208289[/ATTACH]

If I have done this properly you should see a picture of the problem I have just been experiencing.  I have never had this before and it is very disconcerting because I don't want to go and wipe my computer and start all over again.

Basically everything freezes and you see what appears at the top but much less of "the white pixels" until you try and press any key on your keyboard.  Then more rows appear and the shapes visible begin to fill out.

I was forced to restart the computer via the button of the front of the tower and within a couple of minutes it did it again.  Currently I am operating Ubuntu by booting off the usb stick I used to install 11.10.

Any help would be extremely appreciated, this is incredibly annoying if you take into context the sheer amount of things that have been breaking.  Widescreen TV, guitar amp, 8 light bulbs, main guitar needs a re-fret, power supply on guitar effects processor died, external hard drive(s)/enclosure no longer working, laptop hard drive died, printer doesn't recognise ink cartridges any more, wok started flaking off all it's non stick coating........ the list actually goes on...........

So seriously (super cereal) if anyone could help me with my pc, you would really be a life saver!

(just as a note, I am currently virus scanning and I had a fresh re-format/start only a couple of weeks ago)

---

### Post by darkvoid86 on 2011-11-30
A little update, 0 threats found..... a dodgy update or a hardware fault?

---

### Post by darkvoid86 on 2011-12-01
Bump

---

### Post by jocheem67 on 2011-12-01
You should state your OS at least and also you graphic adapter

One tip would be to boot from a livecd > to rule out a hardware problem..

---

### Post by darkvoid86 on 2011-12-01
Thanks for the reply!  I might not have explicitly stated my OS but I did say that I am currently using Ubuntu by booting off the USB with version 11.10 that I installed it with.

When I type in "lspci" into the terminal I get "VGA compatible controller: nVidia Corporation G98 [GeForce 8400GS] (rev a1)"

When you say "boot from a livecd >", does that mean booting from usb isn't good enough and it makes a big difference to burn Ubuntu 11.10 onto a cd or dvd?  If so, how come?

Apologies if I haven't written as coherently as I should have or are as Ubuntu savvy as I need to be.  But I am learning!

---

### Post by darkvoid86 on 2011-12-02
Right, I decided to be "adventurous" and see if the pc would start crashing again............ nothing at all so far.  There was an update as soon as I logged in, should I still look for information or just write it up as a couple of flukes?

---

### Post by darkvoid86 on 2011-12-04
More problems....... I forgot to take screen shots but basically the volume went mute and the screen turned black.  Nothing I did brought the picture back so I restarted the computer which then froze on one of the loading screens (really should have taken a picture).  I restarted again with the button on the front and this time during load up it froze on the purple screen with the ubuntu logo.  Upon my third start up the computer managed to arrive at the login screen............ 3 hours in and no problems so far......

Is this not worrying and very weird?

---

### Post by oldtimer7777 on 2011-12-04
Sounds like a hardware issue to me, so I would probably want to check out that system first.. and keep an eye on it booting from the USB overnight.. Check the logs in the morning.. etc etc..  Otherwise, if you can't figure it out I would try using a fresh install and definitely use a walk-through, and see if it isn't some kind of configuration error. 

[https://debianhelp.wordpress.com/201...neiric-ocelot/]("https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/")


> **darkvoid86 said:**
> [ATTACH]208289[/ATTACH]

If I have done this properly you should see a picture of the problem I have just been experiencing.  I have never had this before and it is very disconcerting because I don't want to go and wipe my computer and start all over again.

Basically everything freezes and you see what appears at the top but much less of "the white pixels" until you try and press any key on your keyboard.  Then more rows appear and the shapes visible begin to fill out.

I was forced to restart the computer via the button of the front of the tower and within a couple of minutes it did it again.  Currently I am operating Ubuntu by booting off the usb stick I used to install 11.10.

Any help would be extremely appreciated, this is incredibly annoying if you take into context the sheer amount of things that have been breaking.  Widescreen TV, guitar amp, 8 light bulbs, main guitar needs a re-fret, power supply on guitar effects processor died, external hard drive(s)/enclosure no longer working, laptop hard drive died, printer doesn't recognise ink cartridges any more, wok started flaking off all it's non stick coating........ the list actually goes on...........

So seriously (super cereal) if anyone could help me with my pc, you would really be a life saver!

(just as a note, I am currently virus scanning and I had a fresh re-format/start only a couple of weeks ago)

---

### Post by darkvoid86 on 2011-12-05
Okay, you will have to be a little slower with me.  

"Checking out that system first", do you mean run a hardware diagnostics tool on ubuntu run from USB?  If so, which one do I need to use or download from the software centre?

"Keep an eye on it booting from USB overnight", basically don't leave it on like this overnight? (a lot of wear and tear on the ol'usb I am guessing?)

"Check the logs in the morning", I am such a noob that what this exactly means goes over my head.

I get the fresh install part, but what do you mean exactly by a "walkthrough"?  (something to show you how to set up ubuntu properly with the terminal?)

Oh and the latest news, it is freezing more and more frequently........ I think I am going to have to stick to booting off the usb for now.........................:cry:

> **oldtimer7777 said:**
> Sounds like a hardware issue to me, so I would probably want to check out that system first.. and keep an eye on it booting from the USB overnight.. Check the logs in the morning.. etc etc..  Otherwise, if you can't figure it out I would try using a fresh install and definitely use a walk-through, and see if it isn't some kind of configuration error. 

[https://debianhelp.wordpress.com/201...neiric-ocelot/]("https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/")

---

### Post by darkvoid86 on 2011-12-06
Also, if I spend hours and hours on Ubuntu via booting from the USB, shouldn't that mean that there isn't a hardware issue?  Everything is used apart from the main hard drive when I use Ubuntu this way?

---

### Post by darkvoid86 on 2011-12-07
bump

---

### Post by darkvoid86 on 2011-12-21
More experimentation going on.  I re-installed Ubuntu but where I left all my data and most of the programs intact.  All was well for 3-4 days and then I experienced the initial problem again with the black bar across the top with white pixels.

I tested the RAM when booting Ubuntu from a USB stick, no problems.  I have run the System Testing application both booted from the Ubuntu USB and logged in normally and I perceive that no problems arose.  However, where do I go to find the report it created on my computer to glance down everything?

I am currently writing this logged into Ubuntu normally, however after logging in there was a grey box.  The old fashioned sort which would remind you of something like windows NT or 98.  However the text was far too small to read, along with any text I try to read inside regular windows.  Below is a screen shot of this brand new problem:

[ATTACH]209511[/ATTACH]

I really don't know what to do guys, I really would appreciate some help.  I do not have much money and am currently looking for a new job.  So if I can diagnose and fix this myself then I will save myself going to a repairman who might try to rip me off and force Windows on me.

Last notes:  I have gone for a couple of weeks with the computer booting from the USB with absolutely no problems regarding crashing (just the limitations from booting from a USB stick).  Surely this must mean something?

---


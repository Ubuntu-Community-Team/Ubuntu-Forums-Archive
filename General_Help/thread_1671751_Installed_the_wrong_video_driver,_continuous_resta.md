---
title: "Installed the wrong video driver, continuous restarts"
date: 2011-01-20
forum: General Help
---

### Post by 133N355 on 2011-01-20
Last night I installed the video drivers for my ATi 3870 and I found out the hard way it was the wrong driver, so now upon booting I can only get as far as an Ubuntu screen with some text and then my computer will restart once it reaches that point. It'll keep doing this until I turn it off, and I can't seem to get to a point in which I can get any control over it. I made a live CD but it has the same effect, so I'm pretty lost here. Any help would be GREATLY appreciated :(

---

### Post by cgroza on 2011-01-20
How did you installed it? Via Additional Drivers, a deb or compiled from source?. You can try to boot into recovery mode and there should be an option to fix video or X.

The quick and easy way is to do a fresh install.

---

### Post by WorMzy on 2011-01-20
Boot into single mode.

> [COLOR="DarkBlue"][SIZE="3"]**How to Boot to the Recovery Mode w/o a Menu Option**[/SIZE][/COLOR]

[LIST=1]
[*]If you have Grub 2 set to boot without displaying the menu at all, hold the SHIFT key down until the menu displays. (In Grub it was the ESC key.)
[*]Press any key once the menu is displayed to 'freeze' it. Then arrow to the kernel you want to boot.
[*]Press "e"
[*]Scroll to the end of the "linux /boot/vmlinuz...." line. If displayed, remove "quiet" and/or "splash". Add the word "single" to the end of the line.
[*]Press CTRL-X to boot to the Recovery menu.
[/LIST]
(From #11 in [this topic]("http://ubuntuforums.org/showthread.php?t=1195275"))

remove the wrong driver with apt-get. e.g.
```
sudo apt-get remove xserver-xorg-video-ati
```

and install the correct driver. e.g.
```
sudo apt-get install xserver-xorg-video-radeon
```

---

### Post by 133N355 on 2011-01-20
[QUOTE=cgroza;10379449 
The quick and easy way is to do a fresh install.[/QUOTE]
 
I made a CD to do this initially but it'll just bring up a pink Ubuntu screen with some text for a few seconds, then restart and repeat infinitely. Can't seem to gain any control at all!

---

### Post by 133N355 on 2011-01-20
UPDATE: Now I'm not getting any video output at all! My machine went from the ASUS M4A77D screen to a pink Ubuntu splash with running text and THEN rebooting, to now having zero video output whatsoever. When I turn my computer on, my monitor doesn't even come on. Have I unintentionally ruined my video card?

---

### Post by 133N355 on 2011-01-20
> **WorMzy said:**
> Boot into single mode.
 
 
(From #11 in [this topic]("http://ubuntuforums.org/showthread.php?t=1195275"))
 
remove the wrong driver with apt-get. e.g.
```
sudo apt-get remove xserver-xorg-video-ati
```
 
and install the correct driver. e.g.
```
sudo apt-get install xserver-xorg-video-radeon
```
 
 
Now I'm not getting any video output at all! My machine went from the ASUS M4A77D screen to a pink Ubuntu splash with running text and THEN rebooting, to now having zero video output whatsoever. When I turn my computer on, my monitor doesn't even come on. Have I unintentionally ruined my video card?

---

### Post by WorMzy on 2011-01-20
Okay, it sounds like you have a hardware problem, not a software one. Do you even see the BIOS splash screen/POST results screen when you turn on your PC?

---

### Post by 133N355 on 2011-01-20
> **WorMzy said:**
> Okay, it sounds like you have a hardware problem, not a software one. Do you even see the BIOS splash screen/POST results screen when you turn on your PC?
 
Nothing, my monitor won't even turn on. I got this card not too long ago and it's worked totally fine up until now, I can't imagine that's the work of mere coincidence.

---

### Post by WorMzy on 2011-01-20
I suppose it's possible that the incorrect driver caused your card to stop working, but I think it's highly unlikely. It's certainly something that I've never seen, although I've always used nVidia cards.

Still, if you're not even seeing the BIOS screen, then there's definitely something wrong somewhere. Do you hear any BIOS error beeps? I think a long beep followed by two short beeps is the sign for faulty display hardware, but I'm not sure about that, it probably differs from motherboard to motherboard anyway.

You could try taking the card out, giving it a quick clean (with compressed air, for preference), then putting it back in; that may help. If not, check it in another machine, or try a different card in yours, just to make sure that it's the graphics card at fault, and not the motherboard. If you confirm that the problem is the graphics card, see if you can return it to whoever you bought it from, and ask for a replacement.

---

### Post by WorMzy on 2011-01-20
I suppose it's possible that the incorrect driver caused your card to stop working, but I think it's highly unlikely. It's certainly something that I've never seen, although I've always used nVidia cards.

Still, if you're not even seeing the BIOS screen, then there's definitely something wrong somewhere. Do you hear any BIOS error beeps? I think a long beep followed by two short beeps is the sign for faulty display hardware, but I'm not sure about that, it probably differs from motherboard to motherboard anyway.

You could try taking the card out, giving it a quick clean (with compressed air, for preference), then putting it back in; that may help. If not, check it in another machine, or try a different card in yours, just to make sure that it's the graphics card at fault, and not the motherboard. If you confirm that the problem is the graphics card, see if you can return it to whoever you bought it from, and ask for a replacement.

---

### Post by WorMzy on 2011-01-20
I suppose it's possible that the incorrect driver caused your card to stop working, but I think it's highly unlikely. It's certainly something that I've never seen, although I've always used nVidia cards.

Still, if you're not even seeing the BIOS screen, then there's definitely something wrong somewhere. Do you hear any BIOS error beeps? I think a long beep followed by two short beeps is the sign for faulty display hardware, but I'm not sure about that, it probably differs from motherboard to motherboard anyway.

You could try taking the card out, giving it a quick clean (with compressed air, for preference), then putting it back in; that may help. If not, check it in another machine, or try a different card in yours, just to make sure that it's the graphics card at fault, and not the motherboard. If you confirm that the problem is the graphics card, see if you can return it to whoever you bought it from, and ask for a replacement.

---

### Post by WorMzy on 2011-01-20
I suppose it's possible that the incorrect driver caused your card to stop working, but I think it's highly unlikely. It's certainly something that I've never seen, although I've always used nVidia cards.

Still, if you're not even seeing the BIOS screen, then there's definitely something wrong somewhere. Do you hear any BIOS error beeps? I think a long beep followed by two short beeps is the sign for faulty display hardware, but I'm not sure about that, it probably differs from motherboard to motherboard anyway.

You could try taking the card out, giving it a quick clean (with compressed air, for preference), then putting it back in; that may help. If not, check it in another machine, or try a different card in yours, just to make sure that it's the graphics card at fault, and not the motherboard. If you confirm that the problem is the graphics card, see if you can return it to whoever you bought it from, and ask for a replacement.


[SIZE="1"](If this posts three times, I'm going to scream.)[/SIZE]

---

### Post by WorMzy on 2011-01-20
I suppose it's possible that the incorrect driver caused your card to stop working, but I think it's highly unlikely. It's certainly something that I've never seen, although I've always used nVidia cards.

Still, if you're not even seeing the BIOS screen, then there's definitely something wrong somewhere. Do you hear any BIOS error beeps? I think a long beep followed by two short beeps is the sign for faulty display hardware, but I'm not sure about that, it probably differs from motherboard to motherboard anyway.

You could try taking the card out, giving it a quick clean (with compressed air, for preference), then putting it back in; that may help. If not, check it in another machine, or try a different card in yours, just to make sure that it's the graphics card at fault, and not the motherboard. If you confirm that the problem is the graphics card, see if you can return it to whoever you bought it from, and ask for a replacement.

---

### Post by 133N355 on 2011-01-21
> **WorMzy said:**
> I suppose it's possible that the incorrect driver caused your card to stop working, but I think it's highly unlikely. It's certainly something that I've never seen, although I've always used nVidia cards.
 
Still, if you're not even seeing the BIOS screen, then there's definitely something wrong somewhere. Do you hear any BIOS error beeps? I think a long beep followed by two short beeps is the sign for faulty display hardware, but I'm not sure about that, it probably differs from motherboard to motherboard anyway.
 
You could try taking the card out, giving it a quick clean (with compressed air, for preference), then putting it back in; that may help. If not, check it in another machine, or try a different card in yours, just to make sure that it's the graphics card at fault, and not the motherboard. If you confirm that the problem is the graphics card, see if you can return it to whoever you bought it from, and ask for a replacement.
 
This same exact thing has happened before; my old video card (7800 GTX) was the first video card I had working with Ubuntu when I first installed it, and after a couple days I tried installing a video driver and the monitor stopped coming on after booting (minus the short period in which musical notes and omega symbols started flashing in jagged patterns in neon colors).
 
I got rid of it and went out and bought a GTX 465, unaware of its lack of compatability so I traded it for this 3870, and it worked fine up until now, in which the same chain of events took place. I do not have another video card to troubleshoot with, but I do hear all the normal sounds I'm used to hearing for a regular bootup, just no actual display. At this point I'm convinced that Ubuntu has been the cause of my video cards breaking, though it still may be a WILD coincidence that it's not the culprit but I'm skeptical. Not sure how a driver could be malicious to the hardware it's designed for, but that's the conclusion I've come to after all this has taken place.

---

### Post by piquat on 2011-01-21
Are you plugging in the the power supply connection that is supposed to go directly to the card?
 
I've seen people ONLY plug the card into the MB and think "that's it, it should work now".  They just ignore the big power connector hanging off the card.  It can cause all types of wierd problems.
 
Probably not it, but I thought I'd throw it out there....

---

### Post by 133N355 on 2011-01-21
> **piquat said:**
> Are you plugging in the the power supply connection that is supposed to go directly to the card?
 
I've seen people ONLY plug the card into the MB and think "that's it, it should work now". They just ignore the big power connector hanging off the card. It can cause all types of wierd problems.
 
Probably not it, but I thought I'd throw it out there....
 
Yes, I always make sure everything is plugged in before I press the power button. I appreciate the concern though :)

---


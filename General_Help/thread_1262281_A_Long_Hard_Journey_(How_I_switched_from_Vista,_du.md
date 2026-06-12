---
title: "A Long Hard Journey (How I switched from Vista, dual boot, Vista, and Ubuntu)"
date: 2009-09-09
forum: General Help
---

### Post by schmazz on 2009-09-09
A long story with only a moderately happy ending. I've done a lot of searching of the forums, and they are how I have gotten this far, but I'm afraid nothing completely solves my problems. I've just shifted from one acceptable situation to another. I've made many mistakes along the way, but be gentle, that's apparently how I learn.

I have a Lenovo Ideapad Y710. It came with Vista on it, which I hated. I immediately switched to a full Ubuntu (Hardy) install which was lovely and treated me well for a long time. 

I soon became in posession of an iPhone 3G with OS 3.0 on it, which I enjoyed syncing very much, and so I switched back to a full Vista install since installing Windows as a dual boot when you've already got Ubuntu on there looked kind of daunting. I put up with this for a long time.

 Eventually my usual internet frolicking I became very tired of Vista (as one does) and decided to do a dual boot. I downloaded Hardy, did it up, and life was good. Except my cd/DVD drive disappeared from both OS's. After much frustration and no idea how to fix it, I switched back to a full vista install. Vista still had no idea where the cd/dvd drive was. I said, forget syncing, I want my CD drive back, went back to Ubuntu. Ubuntu didn't know where my CD/DVD drive was anymore either. 

Well, I figured if I was going to work at it, I was going to work at making Ubuntu happen and would worry about the iPhone later. I finally found that switching from Grub to LILO meant the CD/DVD drive was back. Hooray. I upgraded to Jaunty, and used Envy NG to find the right video driver, life is good.

So -- Now we're back to the issue of the iPhone. I really don't want to jailbreak it. I'm not that confident in my skills (for perhaps obvious reasons) and I can't afford to brick it. and it looks like no one's come up with a great solution for the 3.0 OS anyway. I think a dual boot would be the easiest way to address this, but all of the how-to's talk about Ubuntu to dual boot with grub, and not lilo. I'm concerned if I switch back to grub, my cd/dvd drives are going to disappear again, and I'm a little confused by the how-to's themselves. (I was going to just start syncing at work, but the itunes store is blocked by our firewall and i can't download album art etc, and that's just annoying.)

I've left a LOT out, but I wanted to write a forum post and not a novel. Thoughts?

Much appreciated,
Schmazz

---

### Post by nothingspecial on 2009-09-10
Have you thought about running some sort of windows in a virtual machine?

---

### Post by schmazz on 2009-09-10
I've read some things about XP in Virtualbox, but I have a copy of Vista. Have people had great luck with Vista in virtualbox? It seemed like a lot of steps for something that should be pretty simple, enabling network and USB access...

---

### Post by schmazz on 2009-09-12
Ok, so I've taken the plunge and vista is installing in virtualbox right now. I'm amazed at how well it seems to be going. I could very well be all set. We'll see.

---

### Post by synapsys on 2009-09-12
I have run vista in a virtual box, it works great. I could never get my iphone to attach to usb for some reason. I didn't play around with it all that much because I have a dual boot with vista. 

Dual boot configurations are actually quite simple if you don't mind getting your hands dirty. I have a hard time believing that your boot loader (grub vs lilo) has anything at all to do with your cd drive working.... I'll be it has more to do with the physical characteristics of the drive. Maybe you have a loose connection or a failing drive. Usually when a drive is not detected in 2 different os's this is the case. 

That being said, if you install vista first, then ubuntu, there is absolutely no configuration necessary. Ubuntu detects your vista partition (and of course itself) and practically dual boots for you.

(Unless you have 8 gigs of ram and a quad core processor, running virtual os's will be kinda slow)

***Scratch that: ***I just updated to the latest version (3.0.6) and now my iphone is working beautifully with my vista virtual machine.

---


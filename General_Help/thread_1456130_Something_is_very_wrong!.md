---
title: "Something is very wrong!"
date: 2010-04-16
forum: General Help
---

### Post by Lime Roberts on 2010-04-16
Hey all, I really need some help with this. I just reformatted a hard drive and installed ubuntu 9.10 on it. It was running fine but when i installed the driver update for my video card, Nvidia GeForce 9800 GT, when i rebooted the BIOS screen flashed but then the screen went dormant. When I rebooted again to try and just clean install from the CD, the BIOS screen didn't even come up. I have no idea what to do, i really don't want to lose my computer, I've only had it 4 months =(

---

### Post by jbrown96 on 2010-04-16
Ubuntu didn't break your computer. It probably didn't actually reboot or something. Try unplugging (and if a laptop, remove the battery), then try booting again. Sometimes if you have a CD or flash drive installed, the BIOS will try to scan it before displaying anything, so you may have to wait a minute.

---

### Post by Native Dialect on 2010-04-16
> **Lime Roberts said:**
> It was running fine but when i installed the driver update for my video card, Nvidia GeForce 9800 GT, when i rebooted the BIOS screen flashed but then the screen went dormant. When I rebooted again to try and just clean install from the CD, the BIOS screen didn't even come up. I have no idea what to do, i really don't want to lose my computer, I've only had it 4 months =(

First things, I hope that this experience does not sour you on using Ubuntu or any other *nix distro out there. Secondly, I believe I know what your problem is. 

You will have to plug your computer monitor into your iGP (integrated graphics card a.k.a on-board graphics card). Ubuntu, by default, will output through the iGP first, until you have installed and configured the drivers for your alternate GPU, in this case, your GeForce 9800GT. 

Of course, the supposition to my claim, is that your mother board has an iGP in the first place. It is not often the case, but there are some motherboards that are lacking an iGP. I doubt that such a matter will be applicable to your situation, but it is a note worthy consideration. 

So, just unplug your monitor from your graphics card, and plug it into the other port, for your on-board card. You should see that everything loads up just fine.

---

### Post by Lime Roberts on 2010-04-16
Already tried both of those with no success. And I don't blame Linux at all.

---

### Post by Native Dialect on 2010-04-16
Then there is something very wrong with this situation. I had a similar occurrence, but simply changing to my iGP, remedied the matter. I am not sure what to suggest at this point.

---

### Post by Lime Roberts on 2010-04-16
Yea, no idea what's wrong. The BIOS don't even beep anymore.

---

### Post by shaka_zulu on 2010-04-16
Do you have laptop or desktop?

---

### Post by Lime Roberts on 2010-04-16
Desktop

---

### Post by Colo2 on 2010-04-16
Reset the CMOS

---

### Post by Lime Roberts on 2010-04-16
How?

---

### Post by Native Dialect on 2010-04-16
[http://www.wikihow.com/Reset-Your-BIOS](http://www.wikihow.com/Reset-Your-BIOS)

If that works, then I am glad for you ma'am or sir.

---

### Post by Lime Roberts on 2010-04-16
Is it the same as clearing the RTC RAM?

---

### Post by christguard on 2010-04-16
> Yea, no idea what's wrong. The BIOS don't even beep anymore.

If you are not hearing a post-beep or a beep code, you are in trouble. Generally that is as bad as things get! If you have a friend who knows alot about computers, i would ask him for help, as things can get sticky from here on out.

As suggested before, first try reseting the cmos. To do this your motherboard will have a "jumper" on it. a jumper is basically a type of switch. In a well lit room open up your computer and look for the cmos jumper on the mother board (Make sure your computer is UNPLUGGED when you do this)... here is an image of what they look like: [http://www.nordichardware.se/skrivelser_img/220/cmos.jpg]("http://www.nordichardware.se/skrivelser_img/220/cmos.jpg") (I am not sure if outside links are allowed, if not, just google image "CMOS jumper" and see the firs result. Jumpers come in all colors but are normally black or red.

When you find the cmos jumper, remove the little cap (It will be on two of three little metal prongs) then, with it off, plug your computer in, and try to turn it on a few times (It should not turn on at this point). unplug your computer and replace the jumper on the prongs, but this time put it on the middle prong and the one prong it was not on before. Plug your computer back in and try to turn on again a few times. It still should not turn on. Unplug and put the jumper back in the original position. Plug back in, and see if your computer works. If this does not work please let me know, and we will move on to step two.

---

### Post by Lime Roberts on 2010-04-16
Ok, i think it reset. The screen it's now showing is asking if i want to run startup or load default values. Which should i choose?

---

### Post by 3rdalbum on 2010-04-16
> **Lime Roberts said:**
> Ok, i think it reset. The screen it's now showing is asking if i want to run startup or load default values. Which should i choose?

Loading the defaults should work, but at some point in time you will want to go back into the BIOS setup screen and set its clock.

---

### Post by Lime Roberts on 2010-04-16
Thanks everyone for the help, my computer is up and running again. Any idea as to why my BIOS gave out?

---

### Post by christguard on 2010-04-16
It happens when vital drivers are installed and interupted...sometimes for no reason. Knowing how to reset cmos is a great skill to have! That is the first thing to try if you don't hear a POST beep.

-posted from my motorola droid

---

### Post by 3rdalbum on 2010-04-16
> **Lime Roberts said:**
> Thanks everyone for the help, my computer is up and running again. Any idea as to why my BIOS gave out?

As far as I know, it "just happens" sometimes.

---

### Post by Linuxforall on 2010-04-16
Flash to latest BIOS and check for CMOS battery.

---

### Post by Native Dialect on 2010-04-16
Glad everything worked out for you, Lime.

---

### Post by lisati on 2010-04-16
> **Native Dialect said:**
> Glad everything worked out for you, Lime.

Ditto. My first impression was that something horrible had happened, thankfully it was fixable.

---

### Post by Native Dialect on 2010-04-17
I am even more pleased that it did not sour them on Ubuntu. I had an issue when I first started out, and I almost swore GNU/Linux off, because of it. It is a bit of a learning curve, and it can be a little scary, but once you understand it, it is a beautiful OS. Also, this moment is a testament to the community, coming together to solve a problem. Hopefully, it can stay that way (as in, no more posting commands that harm the user's system).

---


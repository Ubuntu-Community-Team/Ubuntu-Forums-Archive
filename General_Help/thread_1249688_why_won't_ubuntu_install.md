---
title: "why won't ubuntu install?"
date: 2009-08-25
forum: General Help
---

### Post by lordyosch on 2009-08-25
This isn't really a plea for help more a quest for info.

I've tried to install a variety of Linux flavours on my laptop but nothing installs except puppy, which I don't like.

It's something to do with the SIS board I believe, but what?
Drivers? Chips? 

I wish it did work.

---

### Post by tgeer43 on 2009-08-25
'nothing installs" is really not enough to go on. What exactly happens when you try? The more info we have, the more we'll be able to help.

tgeer

p.s. I run Puppy Linux from a USB thumb drive loaded totally into RAM and it still only takes less than 64MB. I love it - just not as my main OS.

---

### Post by lordyosch on 2009-08-26
It won't install period. Insert disc, make initial choices then it all hangs.

Ubuntu (32+64) version 8+9
Mint
OpenSuse
Fedora
Madriva

Nothing. Not a sausage.

All hang during install.

Like I said, i'm pretty much abandoned to the laptop being my (wife's) WXP machine.

I'm happy with my desktop!


Just curious.

Jay

---

### Post by P4man on 2009-08-26
> Insert disc, make initial choices then it all hangs.

Can you be a tad more specific ? What "initial choices" ? does it boot into a live session or not? Do you mean you get the screen where you can chose language and keyboard and verify cd, when you select "try out ubuntu without changes", then it hangs? No messages on screen?

can you give some specs of the laptop?

---

### Post by Genesis3 on 2009-08-26
Try burning the .iso file again to a new blank CD. When 9.04 came out I switched from Windows XP to Ubuntu. The first CD I tried would simply have the Ubuntu logo and the loading bar,all the loading bar would do is move a little line back and forth and eventually I would be taken to the command line and get stuck as no commands would work. I burned another CD using the text based installer .iso file and then success! Ubuntu installed without any problems. What .iso burning program are you using by the way? I used a free program called CDBurnerXP.

Try my solution above then give us some feedback on how it went:KS

---

### Post by rikiriki on 2009-08-26
> **lordyosch said:**
> This isn't really a plea for help more a quest for info.

I've tried to install a variety of Linux flavours on my laptop but nothing installs except puppy, which I don't like.

It's something to do with the SIS board I believe, but what?
Drivers? Chips? 

I wish it did work.

Haven't I read somewhere that AMD is not supported by Ubuntu?

---

### Post by nikhilk on 2009-08-26
> **rikiriki said:**
> Haven't I read somewhere that AMD is not supported by Ubuntu?

That is untrue. Check the "What do I need to create and use my Ubuntu CD?" section on [this]("http://www.ubuntu.com/GetUbuntu/download") page.

---

### Post by Primefalcon on 2009-08-26
not true AMD released their older cards to open source and their newer cards run the catelyst driver..

I'm running an older AMD/ATI card myself a radeon 1300xt pro, runs beautiful on the open source driver

---

### Post by P4man on 2009-08-26
> **rikiriki said:**
> Haven't I read somewhere that AMD is not supported by Ubuntu?

I guess thats why the 64 bit ubuntu version (even for intel) is called AMD64 :)

Nonsense. AMD cpu's and chipsets are equally well supported as Intel or any other. 

What you might have read is that ATI (now AMD) halted linux support for older videocards, so their binary drivers no longer work on ubuntu 9.04 and newer for cards older than ~5 years. For those cards you need the opensource drivers. That likely has nothing to do with what the OP is experiencing though.

---

### Post by rikiriki on 2009-08-26
> **P4man said:**
> I guess thats why the 64 bit ubuntu version (even for intel) is called AMD64 :)

Nonsense. AMD cpu's and chipsets are equally well supported as Intel or any other. 

What you might have read is that ATI (now AMD) halted linux support for older videocards, so their binary drivers no longer work on ubuntu 9.04 and newer for cards older than ~5 years. For those cards you need the opensource drivers. That likely has nothing to do with what the OP is experiencing though.

If the OP downloaded the wrong iso (not AMD) he may not be able to use it with an AMD machine. I just downloaded an iso on a Samsung Tablet PC but couldn't burn on an AMD desktop. Apologies for not expressing myself correctly. Perhaps I'm wrong, I'm new to Ubuntu...

---

### Post by novafluxx on 2009-08-26
> **rikiriki said:**
> If the OP downloaded the wrong iso (not AMD) he may not be able to use it with an AMD machine. I just downloaded an iso on a Samsung Tablet PC but couldn't burn on an AMD desktop. Apologies for not expressing myself correctly. Perhaps I'm wrong, I'm new to Ubuntu...

Nonsense. The AMD64 build will work on Intel and AMD 64-bit CPU's. Its just called AMD64 for some reason unknown to me.

---

### Post by P4man on 2009-08-26
> **rikiriki said:**
> If the OP downloaded the wrong iso (not AMD) he may not be able to use it with an AMD machine. I just downloaded an iso on a Samsung Tablet PC but couldn't burn on an AMD desktop. Apologies for not expressing myself correctly. Perhaps I'm wrong, I'm new to Ubuntu...

No you are mistaken. AMD and Intel chips are quite compatible (100% compatible from a user point of view, 99.9% from a developer point of view).  they run the same software and the same kernels. Both have 64 bit chips and used to have 32 bit chips. 

The 32 bit architecture is called i386 named after the intel i386 chip, the first chip  to implement the 32 bit x86 instruction set. 

The 64 bit architecture is called AMD64, after the AMD Athlon 64 and Opterons  chips, which where the first chips to implement a 64 bit x86 instruction set. Intel later copied this architecture and introduced it in late Pentium 4s, and  it called it EM64T or something. No one uses that name anymore. x86-64 is also frequently used, its the same thing as AMD64.

[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

Now here is the thing: you cant run 64 bit software (ubuntu or anything else) on a 32 bit cpu. Whether that is an intel or AMD cpu is irrelevant. The opposite is possible, every AMD64 bit cpu (intel or AMD) can also run i386 .. 32 bit software.

Hope that clears up some confusion.

---

### Post by rikiriki on 2009-08-26
Thanks for your input guys.

---

### Post by FeTTo on 2009-08-26
try a cooling pad under your laptop...i was fixing a laptop for a friend, and 7 times, the install would get to the 70's% and just hang and freeze. i finally put my cooling pad under the laptop so it wouldnt get hot, and it installed in less time then any of the previous 7 took to get into the 70's. i was installing jaunty 64bit on an amd64. try keeping the PC cool while installing ubuntu

---

### Post by rikiriki on 2009-08-26
> **FeTTo said:**
> try a cooling pad under your laptop...i was fixing a laptop for a friend, and 7 times, the install would get to the 70's% and just hang and freeze. i finally put my cooling pad under the laptop so it wouldnt get hot, and it installed in less time then any of the previous 7 took to get into the 70's. i was installing jaunty 64bit on an amd64. try keeping the PC cool while installing ubuntu

Valid point. I've tried the ub livecd on a laptop and the temperature has gone up making the cooling fan work like mad. I also felt abnormal vibrations whilst touching the pad. Never happened before...:confused:

---

### Post by lordyosch on 2009-08-29
Ive tried again with jaunty 64 bit. The errors are always the same with every version I try.

Choose language, select install. Then black screen with blinking cursor. Hdd spins a while then stops. Hard reset needed.

Try the different options... acpi=off and nolapic produce scrolling mess on screen and nothing else.

Install without GUI fails too.

I know the discs are sound cos they work on my other pc.


Cheers
Jay

---


---
title: "dell inspiron 1526 w/ ubuntu goes to white screen at boot and asks for password"
date: 2009-08-15
forum: General Help
---

### Post by xpinsx on 2009-08-15
hello all. i am working on my friends dell inspiron laptop. it currently has ubuntu 8.10 installed. when i turn the computer on, it goes to a white screen and says something regarding "an administrative password is required to access this computer." when i type, no characters appear on the screen and the only button that seems to get a response is the enter button. i tried booting from a live cd, and the same thing happens. i tried getting into the BIOS, and the same white screen still comes up. i really have no idea what to do with it. i've taken it apart, taken the hard drive out just to see if anything was loose, and everything appears to be fine. i'm thinking that he may just need to buy a replacement hard drive, but i'm hopeful that there is a solution other than spending money

---

### Post by jocko on 2009-08-15
That sounds like a bios password. You probably need to contact dell to get the password, or try to find out how to reset the bios. On most computers it's as easy as removing the cmos battery and leaving it off for a while, but on some laptops this method may not work.

---

### Post by sideaway on 2009-08-15
Sounds to me like someones entered a BIOS password either deliberately (mean joke on a laptop) or accidently.

If you've taken it apart before, then you may have to do so again. If this prompt comes up before the bios screen, chances are I'm right.

What you have to do is unplug the laptop from the mains, take out the primary battery, dismantle the laptop enough to get access to the motherboard and then remove the bios battery (little circular watch battery on the motherboard) hold the power button for five seconds (this will discharge the motherboard) and then leave it for 5 (maybe 10) minutes. This will ensure all settings are reset.

Put the battery back in, rebuild, replace main battery plug in mains and reboot.

EDIT: This method works with a Dell E1505, so I assume you're not-to-far-removed model should yeild the same results.

---

### Post by xpinsx on 2009-08-15
how would i remove the cmos battery?

ok. i'm going to try that

---

### Post by sideaway on 2009-08-15
Good luck, there should be a guid on google how dismantle your model. And kep tracvk of your SCREWS!

---

### Post by xpinsx on 2009-08-15
hmmmm. i mostly took it apart, but i couldn't locate the cmos battery. i really don't want to risk breaking anything, so i think it would be best if he took it in somewhere

---

### Post by jocko on 2009-08-15
> **xpinsx said:**
> hmmmm. i mostly took it apart, but i couldn't locate the cmos battery. i really don't want to risk breaking anything, so i think it would be best if he took it in somewhere
Have a look in [dell's serv]("http://support.dell.com/support/edocs/systems/ins1525/en/SM/index.htm")[ice manual]("http://support.dell.com/support/edocs/systems/ins1525/en/SM/index.htm"). It looks like you [have to remove everything from the motherboard]("http://support.dell.com/support/edocs/systems/ins1525/en/SM/coinbatt.htm#wp1179839") and even take the motherboard out before you can access it. So I guess the battery is hidden on the other side of the moterboard... I would try to contact dell first to see if there is any easier (and safer) way.

---

### Post by sideaway on 2009-08-15
It should be somewhere under your keyboard. If it's anything like the e1505. have you removed that?

---

### Post by P4man on 2009-08-15
Here is a possible solution:
[http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=209701&messageID=2321941](http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=209701&messageID=2321941)

not for the fait hearted!

---


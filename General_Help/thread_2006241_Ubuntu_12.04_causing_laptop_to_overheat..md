---
title: "Ubuntu 12.04 causing laptop to overheat."
date: 2012-06-18
forum: General Help
---

### Post by Pockett on 2012-06-18
I came across an interesting scenario two days ago when I tried to  install 12.04x86 on my laptop and subsequently had major overheating  issues. 

The laptop in question is a L550 Toshiba(2009ish I think) and is a near  identical twin to my wife's L500 Toshiba. Two days prior I had installed  the 12.04x86 system on her laptop and I was so impressed with the distro  that I decided to do the same to my own.

Oh the tribulations.:sad:

I could not make it through the install without the system crashing due to overheating.

On the fourth install, I set the laptop on my patio at around midnight  and successfully managed to install the system due to near freezing  temperatures of winter nights on the east coast of Australia.

So began my journey into finding the cause of the overheating and  rectifying it.....I had no choice as the entire drive was scrubbed and  pride would not allow me to bow to M$ and reinstall Winblows.

I familiarised myself with cpufreqd and searched for solutions to the  overheating, checked the governor was set to ondemand and dropped the  cpu's down from 2.1GHz to 1.8GHz.

Nothing.....Still overheating as before, though it was lasting a little  longer before the almighty "Click" of the power relay opening.

This made me take a step back and rethink the issue.

My wife's laptop is nearly identical to my own. The only major differences are;

-- Wife's L500 Satellite Pro T6750 Core2duo 3Gb Ram 15.X" screen and no graphics accelerator.

-- My L550 Satellite              T6500 Core2duo 4Gb Ram 17" screen and a  Radeon Graphics accelerator (I think its a Mobility 4150).

Knowing full well that the graphics processor is a major heat source, I  went through the system settings to see if the driver had been installed  properly.

It wasn't.

I promptly installed fglrx (2:8.960-0ubuntu1 - I tried the newer version  first but the download kept failing so I went back to the original  driver) and bingo, overheating solved. 

Just to be sure, I loaded a few "resource intensive" apps as well as a  couple of online games and a 20 minute soak left me without a doubt that  the overheating issue is now fixed.

:guitar:

---

### Post by bryncoles on 2012-06-28
> **Pockett said:**
> Knowing full well that the graphics processor is a major heat source, I  went through the system settings to see if the driver had been installed  properly.

It wasn't.

Possibly a dumb question... but how did you do this?  I'm experiencing overheating like never before!

---

### Post by zombifier25 on 2012-06-28
Probaly 'Additional Drivers' is what he's referring to. Search for it in the System menu.

---

### Post by bryncoles on 2012-06-28
Ah, yes.  That does it!  Cheers zombifier25!

No proprietary drivers in use for me!

---

### Post by johnrobert on 2012-07-17
My Dell Studio was having similar problems, running hot (although not as hot as yours) and I was going nuts from the fan running full out, non-stop. But going to System Settings/Additional Drivers and installing the FGLRX driver solved the whole problem immediately. I couldn't load the post-release updates, but no matter.

---

### Post by Thulitharn on 2012-07-19
My ACER 5315 has the same problem.  The stated 'fixes' do not seem to work with this OS version.

---


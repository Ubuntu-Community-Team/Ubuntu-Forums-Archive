---
title: "URGENT 10.04 killed my computer!"
date: 2010-06-12
forum: General Help
---

### Post by Acegard on 2010-06-12
I decided to try Ubuntu 10.04 LTS today. I downloaded it and installed  it in Windows 7 with Wubi installer. I made it dual-boot with Windows 7.  It worked the first couple of times, I.E. it installed just fine and  booted into Ubuntu fine and showed both 7 and Ubuntu as boot options. I  booted into Ubuntu and it told me to install a bunch of updates, which I  did. It then prompted for a reboot, which I did successfully. I then  needed to boot into Windows, so I shut the computer down using the  buttons on the top bar. It shut down OK, but when I tried to reboot,  nothing happened. I pressed the power button, the power light came on,  but none of the HDD/activity lights did, the screen is blank, and the  manufacturer/boot screen never appears. I am using an Acer Aspire 5735  laptop.
Please help! To my knowledge I cannot even boot from a CD because it  doesn't pass on to the boot screen, nothing initializes in any way  whatsoever.
>:( Needless to say I am super pissed.
-Asa

---

### Post by goldshirt9 on 2010-06-12
you are sure your pc hasn't just died.:confused:
can you boot into your bios.

how old is your pc

---

### Post by Acegard on 2010-06-12
no. I press the power button and nothing happens, except it turns on but nothing happens on screen or with any activity lights.

---

### Post by cprofitt on 2010-06-12
Please remove the battery and power adapter.

Then press the power button ten times.

Then reinstall battery and attach the power adapter and try again.

If that does not work I would try hooking it up to an external monitor to see if it is just an issue with the LCD backlight or panel.

---

### Post by goldshirt9 on 2010-06-12
mmmmmmmmmmm if you cannot even go into your bios the error could be more than your o/system.

is it still under warranty by chance.:confused:

---

### Post by F1R3H4CK3R on 2010-06-12
I don't know what happened to you, however, it is a wierd issue, Ubuntu never fails.

Your PC is dead, burn it.

Ubuntu :guitar:

---

### Post by Acegard on 2010-06-12
ahhhh, thank you cprofitt. that worked. Out of curiosity, what was going on and why did that work?[[COLOR=#339900]****[/COLOR]]("http://ubuntuforums.org/member.php?u=257622")

---

### Post by learning_ on 2010-06-12
perhaps it is just your hdd. however if nothing is activating, your power supply my just be shot. try external power, if that doesnt work.... you're screwed. at that point, burn it.

---

### Post by cprofitt on 2010-06-12
> **Acegard said:**
> ahhhh, thank you cprofitt. that worked. Out of curiosity, what was going on and why did that work?

The removal of power and pressing the button, on most manufacturers, is a way to clear the cmos. This usually resolves odd problems like the one you described.

Feel free to mark the thread solved as well so people know that you are set.

Enjoy Ubuntu.

---

### Post by Acegard on 2010-06-12
yes, but what went wrong? (it is working now) This shakes my confidence... if it can happen again I will uninstall.

---

### Post by cprofitt on 2010-06-12
> **Acegard said:**
> yes, but what went wrong? (it is working now) This shakes my confidence... if it can happen again I will uninstall.

What went wrong likely had nothing to do with the install.

I have this issue about once a month with different laptops where I work. I support ~3000 machines of which ~1000 are laptops.

It has nothing to do with the OS installed though.

---

### Post by Acegard on 2010-06-12
so it can and most likely will happen again or no?

---

### Post by cprofitt on 2010-06-12
> **Acegard said:**
> so it can and most likely will happen again or no?

Well... it could happen again -- though I rarely see the same laptop back again in my experience.

If it does happen again you know the solution -- it is not related to the OS though.

I have only had this happen on Windows XP in the past.

---

### Post by Acegard on 2010-06-12
> **cprofitt said:**
> Well... it could happen again -- though I rarely see the same laptop back again in my experience.

If it does happen again you know the solution -- it is not related to the OS though.

I have only had this happen on Windows XP in the past.

Thank you! Solved. :KS

---

### Post by v1ad on 2010-06-12
basically what they are saying the issue lays in the bios.

some people do not recognize the term cmos.

---

### Post by Arand on 2010-06-12
Aceguard:

Did you shutdown the computer or did you hibernate it? If ubuntu hibernated and then got stuck whilst waking up (a bug I guess, hibernation issues are not uncommon), at this stage a hard shutdown (holding powerbutton ~5-10s), ctrl+alt+del or alt+sysreq+RESIUB might be the way to get it down.

If you find that it is hibernation that is causing the issue either:

A. Report a bug against the kernel and provide debugging info, which hopefully will lead to it being fixed in the future.
or
B. Avoid hibernating

###

If it isn't hibernation being the issue, well then my guessing fails as of now.

- arand

---

### Post by Golden.S on 2010-07-02
Hello, the same happened to me as well. I also facing that my computer can not boot some time, I have to take the battery out and plug the AC adaptor, and then switch on (many times now).

I also have the problem that the panel section,. for example my switch off button has bee replaced by my user account name (I have two Account name but no switch on/off button). I have to put another switch button to witch off my computer.

My computer screen blinks time to time. 

Is anyone has the same problem? and any solution for this? 

Thank you very much indeed.

(My computer is one years old, before I use Ubuntu 8.10, It was very good, all the above things never happened).

---


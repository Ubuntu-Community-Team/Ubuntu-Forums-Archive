---
title: "Ubuntu 11.04 Natty + XBMC kills Asrock"
date: 2011-05-17
forum: General Help
---

### Post by joalin on 2011-05-17
Hi,

I've got s serious problem after upgrading my Asrock 330 HT to Natty. I  basically run XBMC Dharma on it, but since it's now dead I can't check  exact releases. 

If I put it in suspend from XBMC, it does, and the blue led starts  flashing. However it's impossible to wake it up, also to reboot it by  holding the power button. When unplugging the power,and back in, then it  won't start up, completely dead. This happened first sunday morning,  and the strange thing is it was back running magically this morning, 48  hours later. Since I must be crazy, I wanted to be sure to reproduce it,  I  once again checked if it would die, and it did.  Anyone has a clue  how it could start working after 2 days? Would it help to disconnect the  battery on the mobo or what might cause this/help me back? Putting it  in suspend in Ubuntu 11.04 natty worked fine, so it seems like XBMC  Dharma causes it to crash really hard...

If anyone is interested, I've got it on video from my iphone... 

Cheers //Joacim

---

### Post by Joe of loath on 2011-05-17
Unplug it completely, take the battery out, and leave it a few days. Should come back.

---

### Post by sisyphus1978 on 2011-05-17
I don't know if I could `leave it a few days'. I have an asrock 330 with xbmc (though I am still on 9.04 because I'm sure later versions aren't really supported yet). Anyway, why don't you email asrock technical support. They are very helpful and should be able to give you an idea of what the problem is (possibly hardware related). Otherwise go and investigate at the xbmc forums and see if anyone has a similar problem.

Good luck.

On re-reading the OP, perhaps it's just a problem with suspend. I never use suspend and have xbmc running all day everyday. I just switch it off at night and back on in the morning (thanks WOL and android handset).

---

### Post by joalin on 2011-05-17
Thanks for your advise. I've opened a ticket at the Asrock support. I will let you know. I'll also try exit next time :-) (if it gets back on)

---

### Post by joalin on 2011-05-17
A quick update. I managed to get the pc back and running by removing the CMOS battery and back in. I unchecked the option to let the user rights to  put the pc in suspend, if it's still risky. I haven't heard from Asrock yet. I guess Asrock has some special implementations of suspension in Bios...

---

### Post by joalin on 2011-05-19
I've now received an answer from Asrock support. 

They recommend to update bios and vga driver. I'm however not very keen on doing this since it's a risk, and i can live with not suspending from xbmc. Maybe a challenge on  a boring day?

---

### Post by YfoMp5QBh2 on 2011-05-19
> **joalin said:**
> I've now received an answer from Asrock support. 

They recommend to update bios and vga driver. I'm however not very keen on doing this since it's a risk, and i can live with not suspending from xbmc. Maybe a challenge on  a boring day?

I downgraded back to Ubuntu 10.10 until most of the bugs have been fixed (only minor irritations) but 10.10 still works better for me and I can't live without XBMC or LIRC.

The downgrade fixed my problems.

---

### Post by sisyphus1978 on 2011-05-24
Good to hear you got it sorted. I'm on 9.04 and xbmc works great. :)

---


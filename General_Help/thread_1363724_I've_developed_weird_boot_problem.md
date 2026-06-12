---
title: "I've developed weird boot problem"
date: 2009-12-24
forum: General Help
---

### Post by Andy11 on 2009-12-24
Hi, I'm working with 9.10 on an old dell desktop and have run into a problem that's over my head. 

Everything worked well until earlier today when I went to boot up (as usual) and instead of my desktop I was brought to a black screen with nothing happening. The computer was still semi-responsive, as i could tell it to power down by hitting the power button on the desktop and it would shut down within a few seconds after letting go, but it had stopped loading anything else.

This is the weird part -- I'm able to get to my desktop and everything's normal when i hit f12 and choose boot to hard drive.  The weird thing is that I've gone into my BIOS and disabled booting from any other devices. I've rebooted a number of times and the same thing has happened over and over again. 

So i'm wondering how to get my computer to fully boot again without having to goto the boot menu at startup each time.

Let me know if i need to clarify anything at all.
Thanks

---

### Post by Bosje on 2009-12-25
Hello Andy,

I have run into exact the same problem as you describe it.... I have not figured out yet what it is. If I find a solution I will let you know, but I've been working with Ubuntu (9.10) just for two days now, so I am no expert. Hopefully there are some experts around, who can help us out. My installation is also on a Dell system. 'Just wanted to let you know, you are not alone.

Greetings,
Rene.

---

### Post by Leppie on 2009-12-25
are you dual booting with windows and is the clock in ubuntu set to utc?
some systems seem to have issues with this combination, windows saves time as local time on a machine. changing that could upset the bios (possibly seen as tampering with it).

---

### Post by nastyboy on 2009-12-25
I'm having almost the same issue....This morning everything worked fine until my box received the updates...then I rebooted the box and now after I log in but before the main menu comes up I get the terminal windows.... This is where I'm having issues, because I'm not sure what to do.

Dual Boot with Vista and 9.10....not sure of the clock right now I can't get there...

HELP

---

### Post by Bosje on 2009-12-25
> **Leppie said:**
>  are you dual booting with windows and is the clock in ubuntu set to utc?
some systems seem to have issues with this combination, windows saves time as local time on a machine. changing that could upset the bios (possibly seen as tampering with it).


I am not dualbooting, I have run Ubuntu over Windows, for I needed to reinstall an OS anyway. I saw this as a good opportunity to try Linux... And so far I like it a lot, despite some small troubles as decribed.

Thanks for responding,
René.

---

### Post by Andy11 on 2009-12-25
> **Leppie said:**
> are you dual booting with windows and is the clock in ubuntu set to utc?
some systems seem to have issues with this combination, windows saves time as local time on a machine. changing that could upset the bios (possibly seen as tampering with it).

I'm not dual booting. I'm going to format and reinstall everything so i'll know in a bit whether anything changes. Any recommendations on top of that? 
Thanks.

---

### Post by Bosje on 2010-01-03
Hé Andy,
I´ve formatted my HD also, reinstalled everything and got the battery temperarily out of my BIOS, but no changes.... Still have the same boot problem. Any developments at your side?

René.

---

### Post by Leppie on 2010-01-03
you could try contacting dell support, i have not had this issue. also, maybe if you set ubuntu to use local time for the hardware clock it will work normal again?

---

### Post by Bosje on 2010-01-09
He Andy,

I fixed it! Thanks to someone on the forum. 
This is what I did:

in the terminal give the command: 	 	 	 	 	   sudo gedit /etc/default/grub
Change    	 	 	 	  sudo update-grub
and then reboot


Good luck! For me this worked. I found this solution at someone who had the same problem and worked with the same computer, a Dell Dimension 2400.


Rene.

---


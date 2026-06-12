---
title: "out of scan range"
date: 2006-06-26
forum: General Help
---

### Post by Hiroshima on 2006-06-26
I'm not sure if this is a graphics card question, a monitor question or a what.  This problem happens only every now an again, but I'm not sure what causes it.  All of a sudden, the screen goes rainbow, and a little error box says:

Out of scan range V:32.8/H31.5

Any ideas on how to fix this?

Secondly, when it happens, I try control alt backspace, but it doesn't seem to do anything, so I end up shutting of the power bar... which isn't supposed to be healthy for computers...  Can I restart X, logout or go to a non-x runlevel using shortcut keys?

Thanks in advance, 
Hiroshima

---

### Post by zxee on 2006-06-26
Alt+Ctrl+F1 is the way to get to a shell or try those 1st two keys with any function key up to F8. If Alt+Ctrl+Backspace isn't working though that keystroke combo may not either. Have you done a search on that out of scan message?

---

### Post by ajifans on 2006-06-26
Type the following into a terminal

sudo dpkg-reconfigure xserver-xorg

have your graphics card and monitor details to hand, and answer the questions.  If you come to a really difficult question, you can press Enter and accept the default, which unless your problem is with this default it will be okay.

Your xorg.conf settings (in particular the monitor settings) may be a bit off.

---

### Post by Hiroshima on 2006-06-26
Thank you for the advice!  How can I check my video card details (I have the book for the monitor)?  

(I'm on a computer at work right now, so I cannot check right away) 

Yes, I did a search for that error in google, on this forum, and on the wiki, but didn't come up with anything that looked the same.

Cheers, Hiroshima

Edit:  PCMCIA says "failed" at startup, I don't know if this is relavant or not.

---

### Post by ajifans on 2006-06-27
The PCMIA shouldn't be relevant if you have a desktop.  I think it's just checking if you have any thing plugged into a PCMIA slot (like on a laptop).

I wouldn't get too concerned about the graphics cards settings at the moment.  It's generally acceptable to select the defaults, so you can just press enter when asked questions about these and it shouldn't change your default setup.

When it gets to the monitor settings, select 'Advanced' and replace any settings that differ with the ones stated in your monitor book.  Pay particular attention to the scan range and the list of allowed resolutions (remove the asterix by any that your monitor can't handle).

---

### Post by Hiroshima on 2006-07-01
Ok, I've run sudo dpkg-reconfigure xserver-xorg with book in hand.  I will wait and see if it happens again.  

I've also noticed an "auto" button on the bottom of the monitor... If anything happens in the future, I'll pushing it to see if it refreshes as it is supposed to.

Cheers, and thanks Ajifans!

Hiroshima

---

### Post by Hiroshima on 2006-07-07
D'oh...
While I was still using ubuntu, it did happen again.  Even after I ran x-org...
Too bad.  Due to other problems (Grub) I reinstalled with Kubuntu (wow, I like KDE) and had one crash again, after a reinstall.  everything should be on default after the reinstall.  I don't know what is wrong.  The 'auto' button on my monitor didn't do anything either...  I think it jst reset the monitor settings, but didn't help the problem.  

Thanks for the advide though,

Hiroshima

---

### Post by jkwarras on 2006-07-08
Do you have a TV-out?

---

### Post by PriceChild on 2006-07-08
The "Auto" Button on your monitor automatically adjusts your monitors settings to make the display best. Sharpening, removing distortion etc.

---

### Post by Hiroshima on 2006-07-08
> **jkwarras said:**
> Do you have a TV-out?

No, I don't have a TV out.

and thanks for letting me know what the auto button is  for.

I think that it happens mostly when I'm opening applications, when other things are open.  Could be a connection to memory?  It hasn't happened lately, which could be because I'm being carefull not to open too many things at the same time.

Hiroshima

---


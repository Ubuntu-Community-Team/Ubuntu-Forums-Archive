---
title: "[URGENT] I can't Log In.....????"
date: 2010-04-15
forum: General Help
---

### Post by r352alit on 2010-04-15
Just finished Update Karmic koala, but after finished installing all the update and restart i can't log in....????? :confused: :confused:
On the screen its show tty1. And what is that mean...? frankly speaking THIS IS MY FIRST TIME having nightmare that i can't log in.... let alone the X11 desktop, there is no log in screen....???? :confused: :( :confused: :(
can anyone, anybody, someone, somebody help me..... because i don't know what to do.....????


(All my precious data for School Test Subject is on the Documents folder....)

---

### Post by nixclusive on 2010-04-15
You should be able to enter your username/password on that tty1 screen. I think the update broke your X configuration. Try the command *reboot* once you've logged in the text console and depress the SHIFT key as the system is powering on, you'll be shown the grub boot menu. Select recovery mode and you should be presented with the options to fix your X configuration.

---

### Post by akakingess on 2010-04-15
You could also try typing in "startx" (without the quotes) and just see if it is a boot config issue. Other than that suggestion, I agree with 'nixclusive' on his/her suggestion.

---

### Post by r352alit on 2010-04-15
> **nixclusive said:**
> You should be able to enter your username/password on that tty1 screen. I think the update broke your X configuration. Try the command *reboot* once you've logged in the text console and depress the SHIFT key as the system is powering on, you'll be shown the grub boot menu. Select recovery mode and you should be presented with the options to fix your X configuration.

already did that sir.... no offense meant, but the result is..... my system  totally freeze up... stack dumb!!! :confused::(:confused::(:confused:


> **akakingess said:**
> You could also try typing in "startx" (without the quotes) and just see if it is a boot config issue. Other than that suggestion, I agree with 'nixclusive' on his/her suggestion.

typing it on tty1 screen.... i'll try it...

thanks....

---

### Post by r352alit on 2010-04-15
yup.... it's the Xconfig problem, and it said that my NVIDIA graphic driver kernel has been broken. And that resulting that the system can not load the Xsession.

So.... how do i fix it...? can i download the kernel module for my NVIDIA driver on the tty1...? 

Oh.. i forgot. i'm not using dual OS... this is pure linux just for education..... (where do i have a mount of money to buy a license OS that cost me almost $150 minus software...?)

---

### Post by akakingess on 2010-04-15
So, did you have it running, but after that did you enable some hardware drivers (restricted, I mean) and then restarted and that is where the problem started? If so, why not try a new clean install and start over? Other than that, I don't have much experience swapping graphics drivers around via CLI/TTY1, so I won't be of much help there.

---

### Post by r352alit on 2010-04-15
> **akakingess said:**
> So, did you have it running, but after that did you enable some hardware drivers (restricted, I mean) and then restarted and that is where the problem started? If so, why not try a new clean install and start over? Other than that, I don't have much experience swapping graphics drivers around via CLI/TTY1, so I won't be of much help there.

Just solve the problem though..... :P (with trial and error :()

Thank god it's much easier if so many people help solving the problem.... thanks akakingness and nixclusive :P :KS for the input and enlightment.... you are rocking
Just a hint for anyone, someone, somebody or anybody... if you mess up the xconfig, just try to reinstall the graphic driver. don't worry about the desktop manager, because on that state you really don't need the "# sudo /etc/init.d/gdm stop"

99% you're already "kill" the Xserver. just install the driver... and let the magic begin (from my point of view). after finish installing the driver, start the Xserver.... Voila... it's in...

but the cost is great... you're back to the state like being fresh install. no data on the documents, downloads or any folder that stored in those folder....

So... pick a choice.... Fresh install or reinstall the driver if the Xserver is broke....


Thanks....

---

### Post by akakingess on 2010-04-15
Glad to hear you are back up and running, as always, 'we' are here for you and everyone else and each other. Just one final note, though. If you don't mind, if the problem is in fact resolved, please mark the thread SOLVED (it is located at the top of the thread under thread tools). Good Luck and Happy Learning ;)

---


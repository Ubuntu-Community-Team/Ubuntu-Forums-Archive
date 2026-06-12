---
title: "no input signal"
date: 2009-08-18
forum: General Help
---

### Post by gsbetini on 2009-08-18
Hi, all,


I have been using Ubuntu 9.04 and windows XP in my PC since June 09. They were working just fine until this morning. When I turned the computer on the screen turned black after the initial “Ubuntu” signal (could not login). If I turn the monitor off then on, I get "no input signal". I do not have the same problem with XP and I have tried two other monitors and got the same problem. 



As you can see, I am new in linux and would appreciate any help.

---

### Post by Vunutus on 2009-08-18
I had an odd problem a while back where I had two monitors plugged in, but kept one of them turned off. In windows, the one that was turned on was the primary. For some reason, Ubuntu thought the other one was the primary.

Every time I turned the computer on, it acted like you describe. It would boot up and my main monitor would just say "no signal". What was actually happening was that all the login display was moving over to the second and powered off monitor.

I don't know if that's the problem you're having but it's worth a try. Make sure all monitors are turned on or unplug all but the main one and see what happens.

---

### Post by gsbetini on 2009-08-18
hi, thanks for your help, but I have only one monitor.

---

### Post by Vunutus on 2009-08-18
> **gsbetini said:**
> hi, thanks for your help, but I have only one monitor.

Have you recently tried to install a video driver or something? My next suggestion would be to select "recovery mode" from the GRUB select screen and run xfix.

---

### Post by gsbetini on 2009-08-18
noop, I have not changed anything in my computer. 
I ran xfix but did not work. I got the following message:  
 

 xserver-xorg postinst warning     overwritting possibly-customised configuration
 file; backup in /etc/x11/xorg.conf.20090818125039

---

### Post by Vunutus on 2009-08-18
That sucks =/

I'm running out of ideas as to what it would be. The last thing I can think of to try is to hit "Ctrl+Alt+F2" (make sure F-lock is on if your keyboard is annoying like mine and has that) to try and bring up a console. If you get a login prompt then I'd be willing to bet it's an X issue.

Perhaps somebody else has real solutions?

---

### Post by ReyDavid5 on 2009-09-27
I have this same problem as well.  I tried pressing "Ctrl+Alt+F2" and it finally gets to where it says "myusername-linnux login:  *  fglrx (8.600)...."
and then just continues on and goes to the same problem i had before.
after it says that though it does say "Starting GNOME Display Manager..." so i don't know what to do and i can't log in right now.

---


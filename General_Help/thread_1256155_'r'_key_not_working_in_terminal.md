---
title: "'r' key not working in terminal"
date: 2009-09-02
forum: General Help
---

### Post by stoneg64 on 2009-09-02
Hey,

I've got what I think is a strange problem.  When using the gnome-terminal and any virtual consoles the 'r' key can not be typed in.  I'm using a laptop and have tried both the laptop keyboard and an external keyboard and neither work, so I'm pretty sure it is not a hardware issue.  Although the 'r' key does not work in the local terminal it does work on remote servers I've logged into from the same terminal.  The 'r' key also works fine from firefox.  I can also type 'R' with no problem, I simply can't type 'r'.   The only thing I can think of is that I somehow assigned a hot key to the 'r' key.  Does that make any sense?

Any help would be greatly appreciated,
Thanks,
Ted

---

### Post by wojox on 2009-09-02
Have you looked in System > Preferences > Keyboard Shortcuts and scrolled through there to check? 

That is strange.

---

### Post by stoneg64 on 2009-09-02
> **wojox said:**
> Have you looked in System > Preferences > Keyboard Shortcuts and scrolled through there to check? 

That is strange.

I checked there and didn't see anything.  I don't see anything strange in the syslog.  I'm checking things in the gconf-editor now as well.

---

### Post by stoneg64 on 2009-09-02
I tried installing Konsole and it has the same problem.  I might try rolling back the kernel to one that worked.

---

### Post by stoneg64 on 2009-09-02
> **stoneg64 said:**
> I tried installing Konsole and it has the same problem.  I might try rolling back the kernel to one that worked.

I tried loading an older kernel at startup and nothing changed.

---

### Post by stoneg64 on 2009-09-02
Seeing as this problem seems to occur on all terminals/consoles I've installed, can anybody suggest what package that the shells are running on top of so I could attempt reinstalling/rollingback them?

Thanks!

---

### Post by dearingj on 2009-09-02
> **stoneg64 said:**
> Seeing as this problem seems to occur on all terminals/consoles I've installed, can anybody suggest what package that the shells are running on top of so I could attempt reinstalling/rollingback them?

Thanks!

Ubuntu uses the 'bash' shell by default. Good luck.

---

### Post by Vishnu V on 2009-09-02
Check this
Do  you use compiz config setting manager or any application which you configured 'r' as shortcut
or
try it in a new user account

---

### Post by Lucky75 on 2009-09-02
before any of that, try typing "setxkbmap" into the console and see if that fixes anything?

---

### Post by stoneg64 on 2009-09-02
> **dearingj said:**
> Ubuntu uses the 'bash' shell by default. Good luck.

You nailed it, sort of!  As usual the answer is stupid user.  I tried tcsh and everything worked fine so I checked /etc/inputrc to see what I had recently changed.  I added the line "rmmod pcspkr" suggested elsewhere on the internets to attempt to shut off the system speaker.  Well it didn't do that and it somehow turned off my r key.  I'm pissed I didn't think of this earlier.  

thanks!

---

### Post by dearingj on 2009-09-02
> **stoneg64 said:**
> You nailed it, sort of!  As usual the answer is stupid user.  I tried tcsh and everything worked fine so I checked /etc/inputrc to see what I had recently changed.  I added the line "rmmod pcspkr" suggested elsewhere on the internets to attempt to shut off the system speaker.  Well it didn't do that and it somehow turned off my r key.  I'm pissed I didn't think of this earlier.  

thanks!

Glad you got it fixed, though I am puzzled as to why that line would affect your ability to use one (and only one) key on your keyboard.

---

### Post by vttay03 on 2009-09-02
Just as a side note - to turn off your pc speaker add the following line to /etc/modprobe.d/blacklist.conf

```

blacklist pcspkr

```

I promise it won't have unintended side effects on your 'r' key.

---

### Post by cariboo on 2009-09-02
I marked this thread as solved for you. Next time use Thread Tools at the top of the page to do it your self.

---


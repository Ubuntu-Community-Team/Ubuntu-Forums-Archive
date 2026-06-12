---
title: "General Troubleshooting Tips"
date: 2011-12-19
forum: General Help
---

### Post by randomname9438 on 2011-12-19
Hello Forum,

I had a simple question... A few times now I've been doing various things which has caused my system to either freeze or, the screen goes blank EXCEPT for the mouse and the wallpaper. I've tried different things to get a terminal going, or something like a "cntl-alt-del" but nothing works. I must kill the power and reboot. When I do this though, I ALWAYS have problems booting back up. Sometimes I can't get past the Ubuntu/Kubuntu splash screen with the dots moving, sometimes it freezes on the login screen before I can even type anything, or sometimes it'll freeze after I input my login info, but never makes it to the desktop. 

So, I'll restart until my heart is content. That doesn't seem to fix it until 2-3 restarts (sometimes). Sometimes I'll boot into Windows and work over there a while to ditch some frustration, then I'll try again and everything magically works.

So what I'm wondering is - in situations of freezes, lockups, etc. What kinds of general troubleshooting can we do? Are there terminal commands we should run? Things we should check for? A certain amount of time before we should try again? Etc. etc. 

I look forward to any guides, tips, answers, pointers, whatever...

Thanks!

---

### Post by Wayne_V on 2011-12-19
If the GUI freezes the first thing I try is "CTRL-ALT-F1" .  That should give you a text mode login on another virtual terminal.

(oh, and CTRL-ALT-F7 to go back to the GUI VT)

---

### Post by randomname9438 on 2011-12-19
So once I'm at the terminal - what should I do? Are their commands to reset the GUI, or should I just tell it to reboot? I'm not familiar but a few commands... so if I can make it to the terminal, OR, if I have to reboot - should I go to "recovery mode" and try anything?

---

### Post by Wayne_V on 2011-12-21
you can tail ~/.xsession-errors and see if there is anything there.

go to /var/log and tail any files there that have changed recently (cd /var/log ; ls -altr)

run top and see who's hogging memory or cpu

if you want to just kill X, I think you can just kill either lightdm or gdm, whichever you are using, and that should take care of everything.  init should kick it off again and take you back to the login screen on VT 7 (Ctrl-alt-F7)

That's a start anyway ....

---


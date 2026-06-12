---
title: "Regarding working webcam"
date: 2010-01-18
forum: General Help
---

### Post by llawwehttam on 2010-01-18
I have a webcam that works fine in ubuntu ..... when its turned on. There is a hotkey to turn it off which I do when on battery power but if I want to use it again after turning it back on I have to reboot. Is there a way to automatically detect it when I turn it on?

---

### Post by schmidtbag on 2010-01-18
is this a built-in webcam or a separate one?  also, what program are you using to try the webcam?  it just surprises me that you can only use the webcam once.  if you have a hotkey to enable it, there should be one to disable it.

theres a possibility that whatever the program(s) you are running continue to run even after you close them.  after you close the program and you can't get the webcam to start up again, check system monitor to see if there are any processes still running related to what you used before.  if you really aren't sure what some of the processes are, try logging out and logging back in instead of doing a full restart and see if that fixes anything.

---

### Post by llawwehttam on 2010-01-19
Sorry I wasn't very clear there. It is an internal webcam. The hotkey turns it off AND on but when I turn it back on in ubuntu it is not detected. It works if it was on when I booted up but if then I turn it off and on again I cannot use it till I next reboot.

I want to be able to turn it off when I'm on battery power then turn it back on and use it straight away. Once I have turned it off and on again without rebooting cheese cannot see it nor can programs such as Emesene.

Any help appreciated.

---

### Post by schmidtbag on 2010-01-19
try using it without the hotkey, i'm not really sure why you would need the hotkey in the first place.  also, check if cheese is still running in system monitor after you close it.

also like i said before, if all else fails, just try logging out and logging back in.  there isn't any reason i can think of why your webcam would only work once, so if you log out, that should force all processes you started to close.  its much faster than restarting

---

### Post by llawwehttam on 2010-01-19
> **schmidtbag said:**
> try using it without the hotkey, i'm not really sure why you would need the hotkey in the first place. 

Erm ... how else do I turn it off and on when I am on battery power?

---

### Post by llawwehttam on 2010-01-19
Woop Woop  got it working. Now I can turn it on when in ubuntu and it is working. Cheese now seems to be able to pick it up and activate it.

---

### Post by schmidtbag on 2010-01-19
you typically aren't supposed to turn it on manually, just let the programs handle it.  don't overcomplicate things.  its good that its working now

---


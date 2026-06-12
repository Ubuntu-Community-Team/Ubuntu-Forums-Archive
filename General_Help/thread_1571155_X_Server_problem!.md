---
title: "X Server problem!"
date: 2010-09-09
forum: General Help
---

### Post by raziology on 2010-09-09
Greetings,

I've been using Ubuntu 10.04 since the day it was released, and I never had a problem with any of the Nvidia drivers that were released. I have upgraded to Ubuntu 10.10 Beta, and had to install the newest Nvidia drive (256.53) for new ABI support (instead of ignoring the ABI from the xorg.conf). 

My problem is that right after the Ubuntu splash screen is displayed, and right after the Nvidia splash screen is displayed as well, I get a blank screen. What's more interesting is that when I switch to another tty using Alt+ctrl+F1 for example, and by using:
```
sudo service gdm stop
```

And then:
```
sudo service gdm start
```

Everything goes well for the actual session.

But when I try the same but this time with the following code:
```
sudo startx
```

I get the ubuntu splash screen, followed by the Nvidia splash screen, followed by the blank screen.
I don't know if this is related, but when I switch to another tty while the blank screen is still there, it gives me the following error:
Waiting for Xserver to begin accepting connections:
No protocol specified

And it keeps on displaying: No protocol specified.



Can anyone tell me what's happening?

I'm using Nvidia 8700m GT on an x200-15k Toshiba laptop.

---

### Post by realzippy on 2010-09-09
...might ask mods for moving thread to maverick testing...and welcome!

---

### Post by raziology on 2010-09-09
Thanks =)

Let's hope that someone sees this thread anytime soon, 'cause it's a very annoying problem.

---


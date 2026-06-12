---
title: "Ubuntu Boot Logo replaced by white screen w/ black lines"
date: 2012-04-11
forum: General Help
---

### Post by Eirreann on 2012-04-11
So I recently re-installed Ubuntu on my hard drive (it's the only OS on there) and after the reinstall when I start up the computer the usual Ubuntu boot screen (with the logo and five little dots under it) has been replaced with a white screen with black stripes down it.  
The white screen also occurs when I shut down the computer, when I suspend, and when I hibernate.... other than that I have no problems with the computer at the moment.
How can I get the Ubuntu boot logo back???  It's annoying the h*ll out of me!

---

### Post by Eirreann on 2012-04-11
Can no one help me out here?

---

### Post by PhantomTurtle on 2012-04-12
I had a similar problem. I think it was because of my graphics card, I had a really old one. Also I didn't happen on any of my computers with newer graphics cards. Can you post your Graphics Card. Additionally, you are only allowed to bump the threads only once every 24 hours.

---

### Post by Eirreann on 2012-04-12
> **PhantomTurtle said:**
> I had a similar problem. I think it was because of my graphics card, I had a really old one. Also I didn't happen on any of my computers with newer graphics cards. Can you post your Graphics Card. Additionally, you are only allowed to bump the threads only once every 24 hours.

Oops, sorry, I wasn't aware of that!

Anyway, I thought it was my video card as well, only this problem only occurred after I reinstalled Ubuntu; previously, when Ubuntu was installed as a dual-boot setup, the boot logo was normal; however after I installed Ubuntu over my entire hard drive I get the white screen instead of a boot logo...  I hope that whatever the problem is will be fixed in 12.04.

---

### Post by 2F4U on 2012-04-12
Do you experience any other graphical problems? Did you already try adding nomodeset to the grub kernel parameters?

---

### Post by roelforg on 2012-04-12
Let me guesss...
Intel brooklyn chipset?
 
Try editing /etc/defaults/grub
Uncomment the GFX_PAYLOAD line and change it's value to 
```

text

```
Remove splash and quiet from the LINUX_CMD_LINE
All should be well.
EDIT:
D'oh!
Forgot to tell to run:
```

sudo update-grub

```
and to tell you to back the file up before editing.

---

### Post by Eirreann on 2012-04-12
> **roelforg said:**
> Let me guesss...
Intel brooklyn chipset?


No, it's the Nvidia GeForce FX Go5200... but will that method work anyway?

> **2F4U said:**
> Do you experience any other graphical problems? Did you already try adding nomodeset to the grub kernel parameters?

I'm a complete noob to Ubuntu and have no idea what "nomodeset to othe grub kernel parameters" means.... sorry.  But no, beyond the white screen at start up, shut down, and whenever I suspend or hibernate, no other problems.

---

### Post by roelforg on 2012-04-12
> **Eirreann said:**
> No, it's the Nvidia GeForce FX Go5200... but will that method work anyway?
 
 
 
I'm a complete noob to Ubuntu and have no idea what "nomodeset to othe grub kernel parameters" means.... sorry. But no, beyond the white screen at start up, shut down, and whenever I suspend or hibernate, no other problems.
 
Just do both eirreann's and my suggestions,
can't hurt.
I mentioned the Brooklyn chipset because that problem is common to those (mine included).
At least you still have the desktop!
(Try having that problem on Server, only the tty and that one is mangled/garbled, what a pain to get running (openssh to the resque!), and i still don't know how my friend got all his typing right on a mangled console :P)

---

### Post by Eirreann on 2012-04-12
> **roelforg said:**
> Just do both eirreann's and my suggestions,
can't hurt.
I mentioned the Brooklyn chipset because that problem is common to those (mine included).
At least you still have the desktop!
(Try having that problem on Server, only the tty and that one is mangled/garbled, what a pain to get running (openssh to the resque!), and i still don't know how my friend got all his typing right on a mangled console :P)

Okay, I'll give it a go!  But could you please give me more detailed instructions?  I don't completely understand what it is that you're asking me to do...

---


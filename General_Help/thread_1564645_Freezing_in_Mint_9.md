---
title: "Freezing in Mint 9??"
date: 2010-08-30
forum: General Help
---

### Post by steve509 on 2010-08-30
Hello guys and gals, I have just a simple question, I've been using mint 9 now for a few months and love it (yes i'm a noobie, lol). Every now and then, maybe twice a month, everything freezes and the only thing I can do is to reboot. The question is, is this a somewhat normal thing to happen using Linux? I have used other distros as well and it seems to happen with them too. Thanks for any info, it is greatly appreciated.

steve509

---

### Post by *uu on 2010-08-30
What exactly do you mean by "freezing"?

Can you see (and hear) that the hard drive is doing something when you blindly press key shortcuts and maybe launch applications? Or when pressing <CTRL>+<ALT>+<F1>, does the terminal screen appear and ask for a login? If so, then possibly "only" some part of Compiz might be crashed, causing the display to fail to be refreshed. (At least that's what often happened to me on my previous Ubuntu installation: the display suddenly stopped with the last shown desktop and all my windows visible and didn't show any changes or new windows. I could move the mouse, though, and the cursor still changed when moving over a window border or text area etc.)

Given the terminal login screen appears, log in with your username and password and enter:

```
sudo /etc/init.d/gdm restart
```

This would only restart your Gnome session and with it the X server. In case you face the above symptoms, I never found a cure, unfortunately.

But if not even <CTRL>+<ALT>+<F1> would work, I'm out of ideas right now, sorry.

And to answer your question: no, this is not a normal thing to happen on Linux, at least it shouldn't be. But it's not too hard either to misconfigure something and have the system go south. Keeps ya busy. :D

Regards,
*uu

---

### Post by steve509 on 2010-08-30
*uu, everything freezes, mouse and all...ctrl + alt + f1 does nothing at all. When this does happen, like i said, maybe once or twice a month, it happens not just the once but 2 to 4 times in about 5 hours time then not again for at least a few weeks. Also when I reboot the bios info comes up like it usually does but then when it should be booting into linux I'll get a black screen with a blinking cursor in the upper left corner. I can't type anything and I have to hit the reboot button again. Tonight this has happened 3 times now. Any other ideas?? and thanks so much for your reply.

steve509

---

### Post by Chris1274 on 2010-08-31
There's a bug in Mint 9 with fsck causing hangups, I wonder this maybe your problem. Can you replace "quiet splash" with "text" in your kernel command line and see if any error messages come up when you try to reboot?

---

### Post by steve509 on 2010-09-01
Chris, I would love to tell you i'll try that but i have no idea how to go about it..I am still too new at this :)

steve509

---

### Post by wojox on 2010-09-01
This is how we do it in Lucid

```
gksudo gedit /etc/default/grub
```

Look for 

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
```

Replace *"splash quiet"* with *"text"*

Save and close. Run

```
sudo update-grub
```

Reboot. That's using Grub2. Not sure if that's what Mint uses.

---

### Post by steve509 on 2010-09-02
This is the output of:

grub-install -v

"grub-install (GNU GRUB 1.98-1ubuntu5-1mint2)"

Should I install the latest grub?

Thanks
steve509

---


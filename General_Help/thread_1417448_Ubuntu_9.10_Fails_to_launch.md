---
title: "Ubuntu 9.10 Fails to launch"
date: 2010-02-27
forum: General Help
---

### Post by sandfire on 2010-02-27
Hi folks,

I am completely new to Ubuntu. I installed it yesterday. It worked well. I was able to log into windows without any trouble and restart into Ubuntu without a hitch.

This morning I launched Ubuntu as usual vi GRUB. I was asked to install about 135 upgrade files, which went withou an apparent challenges. I then went through the restart and noticed that there was an extra two choices in GRUB, but I just left it to launch Ubuntu automatically. Which it did. 

I then messed about with the appearance settings. Noticed a some more updates were waiting which included 49 files. I went through the updating process and restart.
GRUB worked well, and I was soon loggin in with username and password.

The Ubuntu Screen became visible with the flashing horizontal line and about 3 seconds later everything froze. I waited for several minutes - I timed them - but still no progress - everything remained frozen.

I switched off the machine completely, as I knew of no other way to get out of this situation. I rebooted and when GrUB launched I booted into windows 7 with absolutely no problems.

I used restart in windows and then allowed GRUB to boot into Ubuntu. Once more I was able to log in but soon after the Ubuntu Screen appeared and the horizontal line flashed for a few seconds, everything froze. This time I waited five minutes before switching off the machine by disconnecting at the mains.

I am now using windwos 7 to make contact and ask for your help, please.

Not being in anyway computer smart, I will need a step by step approach with very clear instructions as to exactly what I need to do to sort this problem out.

Thank you in advance

Gordon

---

### Post by oldfred on 2010-02-27
It sounds like a video issue but could be something else. The two new lines in the grub menu were a new kernel download and we recommend keeping at least two kernels in case of issues (like this). First try booting with the old  kernel. If that does not work try booting the recovery mode line in the menu. If you end up at a command line startx should start the graphical system.

---

### Post by sandfire on 2010-02-27
> **oldfred said:**
> It sounds like a video issue but could be something else. The two new lines in the grub menu were a new kernel download and we recommend keeping at least two kernels in case of issues (like this). First try booting with the old  kernel. If that does not work try booting the recovery mode line in the menu. If you end up at a command line startx should start the graphical system.


Thanks Oldfred for your help.

I have tried booting with the old kernel. I have tried both the old and new recovery
modes and when booting from there I end up with a black screen with white bands
at top and bottom of the screen. 

Nothing moves from then on.

What's the next thing to do, please?


Again thanks in advance,

Gordon

---

### Post by oldfred on 2010-02-27
I have not had recent issues with video (since about 8.10) but had many before that. Others may be able to help better. 
Much depends on what video card you have. Do you know?
Can you run the liveCD and does it work ok, does it add any parameters to the boot?

To find video info this command may help. From terminal in liveCD run this; it will be long but look for graphics or video card info.

sudo lshw

---

### Post by _khAttAm_ on 2010-02-27
> **oldfred said:**
> I have not had recent issues with video (since about 8.10) but had many before that. Others may be able to help better. 
Much depends on what video card you have. Do you know?
Can you run the liveCD and does it work ok, does it add any parameters to the boot?

To find video info this command may help. From terminal in liveCD run this; it will be long but look for graphics or video card info.

sudo lshw

You can also try the recovery mode if you don't have Live CD.

---


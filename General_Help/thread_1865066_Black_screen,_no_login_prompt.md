---
title: "Black screen, no login prompt"
date: 2011-10-19
forum: General Help
---

### Post by megabuffen on 2011-10-19
Hi!

I'm having a problem with Ubuntu 11.04. When i start my computer, it displays the GRUB menu and I select Ubuntu. I get the loading screen with the Ubuntu logo and five dots, and then the screen is just black. There is no login screen and I can't use Ctrl+Alt+F(number) to switch to a bash shell. After some time it reboots.

Could anyone help me find the problem?

---

### Post by collisionystm on 2011-10-19
> **megabuffen said:**
> Hi!

I'm having a problem with Ubuntu 11.04. When i start my computer, it displays the GRUB menu and I select Ubuntu. I get the loading screen with the Ubuntu logo and five dots, and then the screen is just black. There is no login screen and I can't use Ctrl+Alt+F(number) to switch to a bash shell. After some time it reboots.

Could anyone help me find the problem?

Do you have an ATI Radeon Video Card?

---

### Post by megabuffen on 2011-10-19
Yes I do. It was working fine earlier today, though. It's an ATI Readeon HD4890 to be precise.

---

### Post by Green_Star on 2011-10-19
I have installed 11.04 three days ago, everything was working fine. Today morning I have installed bunch of updates then Iam stuck just like how this thread owner stuck before the login prompt. Recovery mode at grub didnt help, it does the same thing. I tried Alt+Ctrl+F to open any terminal session, but that one too not working. I think these updates broke my display drivers and now I have no way to install my drivers, I have integrated ATI 4200HD graphics card. This is really frustrating.

---

### Post by collisionystm on 2011-10-19
Probably updates killed it. Did you have the fglrx driver installed previously? If not...

reboot your computer

immediately after the bios screen hold the SHIFT key

you will be at grub

choose system rescue

at this menu, choose resume normal boot and hold the SHIFT key until you are at the text login

put in your username and password

sudo apt-get install fglrx

reboot like normal

---

### Post by megabuffen on 2011-10-20
I did what you suggested and it's working now. Thanks a lot!

I had previously installed the graphics driver using files from the AMD website. I remember updating yesterday before I shut down the computer, though I can't recall what updates I installed.

Anyway, it's OK now. And thanks again!

---

### Post by Green_Star on 2011-10-20
As explained at some forum(from google) I started computer with recovery option by adding 'i915.modeset=0' to grub, I was able to manage to go command prompt. From there I have installed proprietary drivers, that fixed everything.

Anyway I strongly believe, Ubuntu needs to fix this so that non-tech people dont have to go too technically to fix the problem, in my previous releases when ever kernel updates(sometimes for some other updates), I loose my drivers and it just hangs before login prompt. I was able to start in recovery option and reinstall display drivers. This is first time Ubuntu hangs even with recovery option.

---

### Post by megabuffen on 2011-10-20
I agree. The problem was very easy to fix when I got instructions and it worked within a few minutes, but if Ubuntu is to become more widespread, it has to be a lot easier to deal with these problems, and they shouldn't occur in the first place.

---


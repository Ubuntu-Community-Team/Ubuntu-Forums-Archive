---
title: "Boot Hangs Up On Splash Screen"
date: 2010-07-19
forum: General Help
---

### Post by teamcoltra on 2010-07-19
So I turned off my computer the other day (I leave my laptop on, pretty much 24/7 I only turn it off if I have to, or I forget to plug it in I turned it off this time just because it was feeling warm)... 

And when I went to turn it back on, the splash screen was big and ugly looking, then the orange ("loading") dots loaded to the end... but then it just stopped. 

My computer wouldn't boot up... so then I used one of the older versions (you know grub lets you select versions before upgrades or whatever)... and the boot splash was the nice small version... and it loaded just fine, but then after the splash screen went away... the monitor just stayed black... same thing with the version before that.


So then I tried recovery mode on the first one (the latest), and when I clicked "boot normally" it took me to shell. However, everything was working fine, I could load up my non-x dependent programs like IRSSI just fine. 

I think it has something to do with me installing the ATI proprietary driver (which was stupid of me, Ubuntu was handling my graphics card perfectly without it... and I hate using closed sourced software). 

Anyway... suggestions?

---

### Post by teamcoltra on 2010-07-19
Quick followup--
I purged FGLRX and that seemed to fix the ugly splash screen, and it allowed the computer to move past it... but only just.

Now after that it takes me to a backlit blank screen... and I can only get into Ubuntu if I use graphics failsafe mode, which I didn't need before FGLRX.

---

### Post by S.R on 2010-07-19
Sounds FGLRX is your man. An excellent how to could help you fix it or could whiyle the list of problems down. Try these things here at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by teamcoltra on 2010-07-19
Yeah that was great for installing, but I am trying to remove it. 

Now I have successfully purged all the fglrx files from my computer, but now I am getting the crappy non-accelerated graphics. Even though before I installed the proprietary drivers, Ubuntu was running just fine with all the compiz effects I could throw at it. 

I also had to remove "fglrx" from xorg (which I think was why I couldn't reboot properly). 

Suggestions on how to get back to whatever Ubuntu was doing to make my computer run nice and smooth?

---


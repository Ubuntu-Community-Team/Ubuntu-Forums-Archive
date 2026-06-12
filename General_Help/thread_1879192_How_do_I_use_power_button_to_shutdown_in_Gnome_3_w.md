---
title: "How do I use power button to shutdown in Gnome 3 without confirmation dialog?"
date: 2011-11-11
forum: General Help
---

### Post by netman74501 on 2011-11-11
How do I use the power button to shutdown my PC without the annoying confirmation dialog when in Gnome 3? I have been searching for the last two hours and am unable to find the answer.

Nearest I came was here:

[http://askubuntu.com/questions/66723/how-do-i-set-the-power-button-to-shutdown-instantly-instead-of-opening-a-dialog/66731#66731]("http://askubuntu.com/questions/66723/how-do-i-set-the-power-button-to-shutdown-instantly-instead-of-opening-a-dialog/66731#66731")

But, as stated there, it does not work for Gnome 3.

I had it working before I updated to Ubuntu 11.10 so I know that it should be possible.

---

### Post by netman74501 on 2011-11-11
Nevermind. I hate life sometimes.

The missing key from the other site was to use dconf editor to navigate to org->gnome->gnome-session and then uncheck logout-prompt.

---

### Post by GreenRaccoon on 2012-03-25
> **netman74501 said:**
> Nevermind. I hate life sometimes.

The missing key from the other site was to use dconf editor to navigate to org->gnome->gnome-session and then uncheck logout-prompt.

Thanks for posting this!  It helped me!

Just to clear up any confusion for anyone else who reads this, you press alt + f2 to open up the RUN dialog (or whatever it's called), and then type in "dconf-editor".  Instead of doing alt + f2, you can do it in Terminal too (ctrl + alt + t).

---


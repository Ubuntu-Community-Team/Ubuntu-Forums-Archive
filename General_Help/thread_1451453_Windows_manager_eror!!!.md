---
title: "Windows manager eror!!!"
date: 2010-04-10
forum: General Help
---

### Post by maadim on 2010-04-10
I have updated my ubuntu 10.04 and restarted my system.
when it came back, I had no windows maneger! "Your windows manager does not support the show desktop button,or you are not running a window manager" when I try to run it,it tells me  that I have an "unkown" windows manager!!!

I sort of a beginner in Linux and don't:confused: know what to do!

---

### Post by ubunterooster on 2010-04-10
alt-f2 to open run dialog. Type nautilus and press return

---

### Post by carlexpc on 2010-04-11
To fix this problem, install compiz:

apt-get install compiz compiz-gnome

Then, reboot your system.

---

### Post by mazin77 on 2010-04-12
I've had a similar problem after an update on 10/4 where windows don't have title bars, lower panel doesn't show open windows and pressing the show desktop button gives the same error message. also the alt-f2 didn't work.
This is how I fixed it:
open the terminal (Applications->Accessories->Terminal),
then type gnome-wm and press enter

---

### Post by ubunterooster on 2010-04-12
> **mazin77 said:**
> I've had a similar problem after an update on 10/4 where windows don't have title bars, lower panel doesn't show open windows and pressing the show desktop button gives the same error message. also the alt-f2 didn't work.
This is how I fixed it:
open the terminal (Applications->Accessories->Terminal),
then type gnome-wm and press enter
This should work. I was not really thinking before and confused the wm with the file manager

---

### Post by maadim on 2010-04-14
Neither of the solutions is working :confused: :(

---

### Post by ubunterooster on 2010-04-14
Ok, when this happens are you looking at a black screen with white text? Or are you logged in and looking at your background?

---

### Post by maadim on 2010-04-14
I cannot get the window Top borders to work. The top panel is gone.
Plus I can't use the multiple screens and the 'Show desktop' features.
When I am trying to run the Windows manager from the menu,an error pops up.
:confused:

---

### Post by ubunterooster on 2010-04-14
press alt+f2. In the run box check "run in terminal" type ```
sudo apt-get install kubuntu-desktop
``` or ```
sudo apt-get install xubuntu-desktop
``` Press "enter" [some say "return"], give password when prompted, press "enter" again, when asks you to press "y" or "n" press "y" and then "enter"

Log out. In the login screen, select your username but before entering your password look at the bottom of the screen for a drop-down menu titled "sessions". Select xcfe or kde and enter your password to log in.

---

### Post by maadim on 2010-04-14
Yeah, Kubuntu is running fine,though KDE is sooo odd!
I wish Gnome was fine...

Anyway you are great,thank you!!!!!!!

---

### Post by maadim on 2010-04-14
Yeah, Kubuntu is running fine,though KDE is sooo odd!
I wish Gnome was fine...

Anyway you are great,thank you!!!!!!!

---

### Post by ubunterooster on 2010-04-14
You could use Synaptic to remove the "ubuntu-desktop" package, reboot, and add the "ubuntu-desktop" package again. If this works, feel free to remove kubuntu-desktop [only if you want to, you can keep both], if not, that's as far as I know what to do.

---


---
title: "Added programs list"
date: 2010-08-24
forum: General Help
---

### Post by AmpersUK on 2010-08-24
If I want to make a clean re-install, is there anyway I can obtain a printed list of all the programs in the"Applications" pull-down menu.

I am sure there will be as this seems a necessary request when things go wrong and you want to re-install if you haven't the technical knowledge to put things right.

Until now, I have been going into every item in the Applications menu and taking a screen shot of all the program's names. but just feel their must be an esier and better way.

Ampers.

---

### Post by Vaphell on 2010-08-24
in synaptic you can generate a list of all packages installed and then use that list to automatically install everything you had.

[http://lifehacker.com/5146028/save-synaptic-markings-to-speed-up-ubuntu-reinstallation](http://lifehacker.com/5146028/save-synaptic-markings-to-speed-up-ubuntu-reinstallation)
don't forget to tick 'save full state'

open the file to see if it's full of package names to be sure you generated it correctly

---

### Post by inameiname on 2010-08-24
Actually that's sort of how I reinstall mine whenever a new version comes out. For me, I just 'sudo aptitude update && sudo aptitude install program1 program2 program3 program... && sudo aptitude remove programA programB programC program...' after putting together my sources.list and pubkeys and voila, it all installs just fine for me.

Here is a cool little script that I also use, which does give you a list of all packages you have on your system, so if you ever wanted to throw them back on there, are you have to do is use it:

[http://gnome-look.org/content/show.php/P-launcher?content=128561](http://gnome-look.org/content/show.php/P-launcher?content=128561)

The 'Installed-Apps' text file that can be saved with this little script is pretty much the exact same as if you go to Synaptic Package Manager and save the markings, which is what Vaphell is talking about.

---

### Post by AmpersUK on 2010-08-24
> **Vaphell said:**
> in synaptic you can generate a list of all packages installed and then use that list to automatically install everything you had.

[http://lifehacker.com/5146028/save-synaptic-markings-to-speed-up-ubuntu-reinstallation](http://lifehacker.com/5146028/save-synaptic-markings-to-speed-up-ubuntu-reinstallation)
don't forget to tick 'save full state'

open the file to see if it's full of package names to be sure you generated it correctly

Thanks for that. I did note: *"It's a nifty time saver, but it likely works best on re-installations  of the same OS version—package names can sometimes change across  upgrades, though the worst that would likely happen would be an error  message and some manual searching/downloading after that."* but am willing to chance that with a new installation.

Ampers

---

### Post by AmpersUK on 2010-08-24
> **inameiname said:**
> ... Here is a cool little script that I also use, which does give you a list of all packages you have on your system, so if you ever wanted to throw them back on there, are you have to do is use it:

[http://gnome-look.org/content/show.php/P-launcher?content=128561](http://gnome-look.org/content/show.php/P-launcher?content=128561)

...

That **is** cool! Thanks.

---

### Post by inameiname on 2010-08-24
No prob. It is a handy little script. Credit goes to the creator. Works great when all you need is something simple to see and use.

---


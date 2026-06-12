---
title: "logging in doesn't start KDE?"
date: 2006-05-12
forum: General Help
---

### Post by ren wins on 2006-05-12
when i tried to log into KDE this morning, instead of starting up my desktop, a konsol window appeared.  This is a step up from yesterday, when logging in would result in a loss of video connection (my monitor would say "check cable" and then turn off).  I can log into terminal just fine.  I'll probably just back up what i need and reinstall, but i figured i'd ask the forum first to see if anyone had any ideas about what's wrong.

Near as i can figure, my nvidia drivers finally did something to mess stuff up.  I've got an geforce fx 5700, and i installed the latest drivers, but they gave me issues when i'd log out/shutdown/restart.  They used to just freeze everything, but these days they just make the logging out text stuff unreadable.

---

### Post by aysiu on 2006-05-12
After you log into the terminal, type ```
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can. Then type ```
sudo /etc/init.d/kdm restart
```

---

### Post by Patrick-Ruff on 2006-05-12
if that doesn't work, you can always try 'startx'...I'm not entirely sure if this still apply's to kubuntu or not...but, idk. it worked with SUSE, so assuming its the same enviornment it should work...

peace

---

### Post by Harold P on 2006-05-12
[QUOTE=Patrick-Ruff]if that doesn't work, you can always try '**startx**'...I'm not entirely sure if this still apply's to kubuntu or not...but, idk. it worked with SUSE, so assuming its the same enviornment it should work...

peace[/QUOTE]

**startkde**

---

### Post by ren wins on 2006-05-14
[QUOTE=aysiu]After you log into the terminal, type ```
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can. Then type ```
sudo /etc/init.d/kdm restart
```[/QUOTE]


so i did this, answered all the questions as best as i could, did the restart thing, and my system did it's classic "let's just desplay random noise instead of what is actually on the screen!"  underneath the noise it is trying to display a kernel login (non graphical, straigh to the terminal sort of thing)

i'm going to try sudo shutdown now
and see if i all that work worked

---

### Post by ren wins on 2006-05-14
crap
now when i try to log in, the screen goes black for a second, with a little timer cursor in the middle, then it goes back into the log-in screen

this happens when i try to login to gnome, kde, and failsafe

---

### Post by aysiu on 2006-05-14
Maybe you can try ```
sudo dpkg-reconfigure xserver-xorg
``` and answering the questions as *conservatively* as possible--maybe opting for the highest resolution of 800x600...?

---

### Post by ren wins on 2006-05-14
[QUOTE=aysiu]Maybe you can try ```
sudo dpkg-reconfigure xserver-xorg
``` and answering the questions as *conservatively* as possible--maybe opting for the highest resolution of 800x600...?[/QUOTE]


if i have to use a computer at a max resolution of 800x600
i'd rather not use a computer

the only thing i was unconservative about was the refresh rate, i said the max was 70hz instead of 65 (which was the default)
which is accurate for my monitor (at least in windoze...?) and 1024x768 is my standard monitor resolution. pretty much everything else i left to the defaults.

this is what i've been running in linux since forever (6 months?), why would it suddenly blow up now? 

unless you want me to go through this reconfigure buisiness just so i can fix what needs to be fixed in wherever

---

### Post by aysiu on 2006-05-14
Yeah, I guess my hope was that in 800x600 you could get it functioning again and then worry about it moving it up to its optimal resolution.

---

### Post by ren wins on 2006-08-17
well i'm back with the same problem (that i never fixed and instead defaulted back to windoze :()

things that have happend since i last posted:
1) somehow GNOME fired up for a session, imediatly i apt-get updated and upgraded
then i restarted, and am back to where i started, trapped in the log-in
2) i tried apt-get remove kubuntu-desktop and ubuntu-desktop, and then reinstalling them, and that didn't help
3) i also tried apt-get install xubuntu-desktop, but that didn't change anything

my man pages seem to be broken. whenever i try to man something (even man man) i get a bizar error saying there isnt enough space or something...
i'll write down the exact error message if you need it. i have to walk accross the house to trouble shoot :(

oh, i tried going back through the dpkg-reconfigure, this time i left everything default, and *something* happend, but my monitor wont display it.
i'm going to try and go back through and leave most of the video card stuff blank.

here are some of my computer specs (i really should add this stuff into a signature)

AMD XP 2200+ processor (1.6 gHz)
512 MB RAM
nVidia FX 5700 graphic card

---

### Post by ren wins on 2006-08-17
oh wait
6.06 went live

maybe i should just scrap all this and get dapper

how do i do this from terminal?

---

### Post by aysiu on 2006-08-17
> **ren wins said:**
> oh wait
6.06 went live

maybe i should just scrap all this and get dapper

how do i do this from terminal?
[http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by ren wins on 2006-08-18
well, i upgraded to dapper according to that link
but i'm still stuck in the log-in screen

i'll enter my password, the screen will black, the little timer icon will pop up like it's loading, and then back to log-in

i suppose now i should take this to the dapper support forum

or just do a straight-up reinstall

---


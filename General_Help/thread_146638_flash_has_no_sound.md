---
title: "flash has no sound"
date: 2006-03-18
forum: General Help
---

### Post by aznmodder on 2006-03-18
flash animations have no sound but i can view the graphics fine...any idea?

edit: i should probably mention that sound works fine everywhere else (playing video files or listening to music) except on google videos the sound doesnt work but i think thats because the video player there is flash based

---

### Post by Sherlock Holmboy on 2006-03-18
i was having this problem too, so i installed epiphany with the extension package to test if it was localized to firefox. epiphany worked after the install and, to my suprise, so did firefox. so it had to be some library that was installed with the epiphany extensions

---

### Post by psychicdragon on 2006-03-19
I don't think the flash plugin plays nicely with esd (the Enlightenment Sound Daemon), which is used by default in Breezy.

Take a look at [this page]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Flash#head-c02d7ec888c401b9b82b98a7d7630cba5a21792b") from the wiki.

If that doesn't work you can turn off esd permanently by selecting on your panel: System > Preferences > Multimedia Systems Selector. Change the dfeault sink from ESD to ALSA. (This may not work with all sound cards)

---

### Post by aznmodder on 2006-03-24
sorry for the late response but none of those solutions seemed to work

im on ALSA right now

---

### Post by JayBachatero on 2006-03-24
I was searching the macromedia site and there is a post that says to start firefox with the followim parameters.  It worked for me.
aoss firefox &

---

### Post by aznmodder on 2006-03-24
how do u do that?

---

### Post by JayBachatero on 2006-03-24
Main Menu > System Tools > Applications Menu Editor > Internet form the left > Double click on firefox > where it says command you add that.  The same thing if you have the quick launch icon.  You right click it and click on properties.

---

### Post by Lod on 2006-03-25
> 4.&#8195; How to configure sound with Flash?
                  sudo ln -fs /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

This is from the Ubuntu startersguide (System->help) and it worked for me. :)

---

### Post by shahrc on 2006-04-08
[QUOTE=JayBachatero]I was searching the macromedia site and there is a post that says to start firefox with the followim parameters.  It worked for me.
aoss firefox &[/QUOTE]

Not working in my dapper..](*,)

---

### Post by nanotube on 2006-04-08
go to the link in my sig, and read the sound section (specifically, "sound, firefox, and flash" part)
that assumes you are using breezy with esd - so no guarantees for dapper, or for alsa. :)

---


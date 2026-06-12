---
title: "step by step starting GnomeDM/StumpWM from grub"
date: 2011-03-22
forum: General Help
---

### Post by Chepoll on 2011-03-22
Hello,
I have a question regarding some steps involving the booting.
Firstly, I want to learn about what happens in the background as the OS is starting. I stated those in the list with [COLOR="Red"]red[/COLOR] colour. I  wrote down my guesses there, please fill in the blanks there or correct me where I'm wrong. Add details as to what folder or file is addressed during these steps too, that would be very helpful.
[LIST=1]
[*]So, I turn on the computer, 
[*]The default option from GRUB is ran(I'll have to edit this so it starts in console) [COLOR="red"]Grub activates a portion of the disk as the OS of selection, and starts the kernel in it.[/COLOR] 
[*]It constantly checks for disk errors at start ( I'll google this) [COLOR="red"]I guess the kernel runs mountall to load. mountall prior to doing so checks for errors(?)[/COLOR]
[*]I then press Ctrl+Alt+F1, [COLOR="red"]next, a display manager is ran. because I don't have one, it goes idle, waiting for me to log-in.[/COLOR]
[*]Input my username,password
[*]It says "-bash: cmd: not found [COLOR="red"]some file that is involved in starting a cdm still points to CDM. What files do I need to search for such a thing?[/COLOR]
[*](I have a .xinitrc folder that points to stumpwm in my home folder)
[*]If I want to start gnome, I move .xinitrc file to some other location
[*]I type in **startx** and stumpWm or Gnome is started depending on whether the **.xinitrc** file is there [COLOR="red"]what folders or files does startx interact with? (same as my question below)[/COLOR]
[/LIST]

Now I will try to solve 2,3 on my own; although all help is appreciated. So here is my question.
**Question:**
I don't want to use a Display Manager, or a login manager, whichever it is called ( like slim, gdm ...)
  Regarding #6 : I had **ConsoleDisplayManager** installed at one point, but it didn't work so I uninstalled it. I believe #6 is a remainder of that. What do I need to do to solve it?
  Regarding $7-9 : What sort of a command do I need to run, without having to play with my **.xinitrc** file, to make **startx** start the specified window manager

---

### Post by Chepoll on 2011-03-22
I solved the problem with #7-9
I just read the **man xstart** and it was quite clear:
_If there is a home/.xinitrc, it starts that one
_If there is not, it starts the one at /etc/X11/xinit/xinitrc.

the second xinitrc said /etc/X11/Xsession, so, I use that to start gnome.
I use /usr/bin/stumpwm to start stumpy stumpy.
I am not sure as for where a third window manager would be, but so far so good.

Still waiting an answer to #6

---

### Post by Chepoll on 2011-03-22
removing "quiet splash" from the grub configuration did it.

Could you mark the thread as SOLVED please.

*edit*
oh, I do that myself.

---


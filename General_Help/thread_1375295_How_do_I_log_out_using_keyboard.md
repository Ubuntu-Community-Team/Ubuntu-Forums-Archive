---
title: "How do I log out using keyboard?"
date: 2010-01-07
forum: General Help
---

### Post by Redsandro on 2010-01-07
Either I am stupid, or the Ubuntu team is stupid for making me need to ask this question:

How do I log out from my ubuntu session without having a mouse? When I press Ctrl+Alt+Del I can only shutdown, reboot etc. but I cannot afford to reboot right now. I need to logout so I can startx as a different user. I started X from CLI.

---

### Post by happyhamster on 2010-01-07
- There are probably a few ways of doing this. For example, for Karmic or newer Ubuntu versions, in a terminal:

sudo service gdm stop

- Or (for older Ubuntu versions):

sudo /etc/init.d/gdm stop

- This will drop you into a console. Login and restart gdm:

sudo service gdm start

(or sudo /etc/init.d/gdm start)

- Or: directly drop into another console by pressing Ctrl-Alt-F3, and restart gdm:

sudo service gdm restart

---

### Post by Redsandro on 2010-01-07
Ah thanks!

I was thinking of something like alt+f2 for running, something for the logout menu, but this works!

I just hope that I remember it when I am somewhere without internet :P

---

### Post by lswb on 2010-01-07
You are not stupid. The older unified shutdown/logout dialog from 8.04 and earlier IMHO was much superior to the current disorganized collection of FUSA, logout and shutdown choices.

I use 9.04, not 9.10, so I don't know if this applies to you, but uninstalling FUSA and/or removing the FUSA applet from the panel will cause shutdown and logout items to me added to the Main Menu/System.

A more convenient method (for me) was to create a keyboard shortcut. Navigate to Main-Menu/System/Preferences/Keyboard Shortcut and select add. I used <Ctrl-Alt-Ins> for the hotkey but you can choose anything you like as long as it isn't already used. In the command field use "gnome-session-save --logout-dialog" to bring up the dialog, or "gnome-session-save --logout" to logout immediately.

Not as nice as the older system, in that 3 hotkeys are now required to do what a single hotkey did previously, but to some people that's progress.

---

### Post by Redsandro on 2010-01-07
Thanks for this advise.

I don't dare uninstalling anything in 9.10 because I've had some problems before when doing things that weren't a problem in 9.04, [SIZE="1"](like replacing GDM with the old one for custom loginscreens caused me not being able to login at all)[/SIZE], but the hotkey will do as I please! :)

I hope it will be neat in 10.04 because I'm going to stick to 10.04 (lts) for a few years.

---

### Post by junapp on 2010-01-07
interesting. I thought I used to be able to hit alt+f1 then use my tab key or some some key to get over to the other panel applications.

according to:
[http://library.gnome.org/devel/hig-book/stable/input-keyboard.html.en#keynav-applets](http://library.gnome.org/devel/hig-book/stable/input-keyboard.html.en#keynav-applets)

it should be possible, but I can't figure out how.

Great question. How does one use the keyboard to navigate the Ubuntu Gnome panels?

---

### Post by Redsandro on 2010-01-07
Haha yes kinda outdated. It also sais:

> Log out	**Ctrl+Alt+Del**	Open the session logout confirmation dialog

Nope. Shutdown/reboot dialog.

---

### Post by xykivo on 2010-05-08
Not sure if this is what you are looking for but u can use:
super + S (the windows key + 'S' key).

This will open the logout/switch-user menu.

---

### Post by Redsandro on 2010-05-08
Nope, not in my install of Ubuntu 10.04.
The best advice is still to add a custom keyboard shortcut to for example ctrl+alt+insert:
> gnome-session-save --logout-dialog

---

### Post by Ginsu543 on 2010-05-08
I personally get around this issue by installing Gnome-Do. You can call Gnome-Do from the keyboard, and then all you have to do is type in "log out" and the appropriate command comes up. Hit ENTER and it logs out! I prefer this to setting up custom keyboard shortcuts because Gnome-Do is so much more versatile and powerful.

---

### Post by Redsandro on 2010-05-08
Sounds potentially nice. What more can Gnome do?

[SIZE="1"]I know who my friends are, but [http://do.davebsd.com/preview.shtml](http://do.davebsd.com/preview.shtml) is timing out over here right now..[/SIZE]

---

### Post by Ginsu543 on 2010-05-08
Best thing is for you to try it out for yourself. You can find it in the Ubuntu repos, so just run Synaptic Package Manager and look for "gnome-do" in the Quick search field. Check on the gnome-do package and click Apply.

Having said that, Gnome-Do is basically a quick-launch utility. Whatever programs you have installed, Gnome-Do does a search as you type and comes up with matching programs. When the program you want comes up, you just hit ENTER and it will launch it for you. Shutdown and Log-out are both doable in Gnome-Do.

---

### Post by Redsandro on 2010-05-08
Ah, sort of enhanced alt+f2.
I'll check it out sometime, for now I only need to log out and the keyboard shortcut settles that. :)

Thanks for the tip.

---


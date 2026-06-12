---
title: "Infinite login problem"
date: 2010-05-13
forum: General Help
---

### Post by morbo1993 on 2010-05-13
Hi, i'm new to this forum, and new to Linux in general. I bought a very cheap computer (About $100) to use as a secondary computer with a Linux distro. 
So i've been using Xubuntu for about a week with only a few tiny problems. But yesterday i stumbled upon a setting called "Appearance" and thought i'd check it out. I tried out a few different, before i went to the bottom one, and chose that ( i think it was the bottom one at least) And then suddenly things started going haywire, with firefox leaving some "copies" of itself as i dragged it around (you know the one where you drag the window and the top bar repeats itself over the screen). I tried to restart and suddenly when i try to log in there is a flash of an error screen, and i return to the login screen again. I can still log in in a Xterm session, but that's obviously just a temporary sollution. 

I'm not 100% sure, but i think the error screen says: 

> Saved ALSA mixer setting detected; aumix will not touch mixer               [OK]
                           Starting common unix printing

på den andre, som lå under, sto det:                             

Pulseaudio configured for per-user sessions 
                                                        checking battery  state           [OK]I've tried deleting the .xsession-errors file to "provoke" the error, and then when i opened it this is what it said: 

> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to  /etc/X11/xinit/xinput.d/default.         And i tried typing: Xfwm4 --replace which only resulted in a logout

Finally i also tried opening the folder /home/dinbruker/.config/autostart/ to see what was in there (all of these things were recommended to try on Freakforum.nu)

which contained 

> .                 xfce4-clipman-plugin-autostart.desktop
..                xfce4-notes-autostart.desktop
dropbox.desktop   xfce4-settings-helper-autostart.desktop
Synergy.desktop   xfconf-migration-4.6.desktop
SynergyS.desktopDoes anyone have any idea?
I am also considering installing either AntiX or Peppermint OS instead, which may be a last solution if we can't find a fix

Thanks in advance :)

---


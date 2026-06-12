---
title: "Karmic GDM uses flat, gray, win2k theme"
date: 2009-12-02
forum: General Help
---

### Post by Levviathor on 2009-12-02
I upgraded to Karmic yesterday, and everything's working great, but the GDM theme is UGLY (see first attachment).  It's using the same ugly theme Ubuntu uses when you gksu an application while using a non-system wide theme in ~/.themes.

See the second attachment for what I was expecting.

So first, why didn't it look correct, and second, how can I fix it?

---

### Post by some-what-Gnu-2-networks on 2009-12-02
Try to right-cick your background select change background. Then click the theme button.
choose wanted theme.

---

### Post by Aflack on 2009-12-02
haha my name is alex too :P
maybe try 'sudo aptitude reinstall gdm'

---

### Post by raktarok on 2009-12-02
I don't exactly know why you are facing this problem, but here are a few things you can try.

First, try this, it will attempt to restore the gdm to the default one:
```
sudo -u gdm gconftool-2 --set --type string /desktop/gnome/interface/gtk_theme HumanLogin
```

If this does not work, try this command -it will bring up an appearaces preferences window. Note that changing theme, wallpaper,etc in this window changes the gdm theme, not the current desktop theme(that's because we lauched it as the user gdm. A very handy trick if you want to change gdm's theme)
```
gksu -u gdm dbus-launch gnome-appearance-properties

```
Or to change the gdm theme, you can also go to the gdm screen, switch to one of the virtual consoles(ctrl+alt+F1), and then from there, type these commands:
```
export DISPLAY=:0.0
sudo -u gdm gnome-appearance-properties
```
On siwitching to the graphical session, you will see the appearance preferences window. If you choose this path, then you can see immediate changes in gdm theme (useful if you are picky like me and want to choose the perfect theme for gdm)

Actually, all of these steps are pretty similar. I don't know if it will solve your problem, but there's no harm in trying. Goodluck!

---

### Post by Aflack on 2009-12-02
Did any of these suggestions work?[-o<

---

### Post by Levviathor on 2009-12-02
I had to leave home immediately after posting.  I'll try them once I get home in an hour or two.

Thanks for so many suggestions guys!  A couple look promising.



On an unrelated note, I need to set up SSH to my laptop.

---

### Post by wojox on 2009-12-02
Make sure ubuntu-artwork is installed.

---

### Post by NFblaze on 2009-12-03
I got this same issue by clicking the accessability issues in the right corner and messing around with them. I havent figured out how to go back, but it doesnt bother me.

---

### Post by Levviathor on 2009-12-03
I used the gconftool-2 trick and installed ubuntu-artwork, and that seemed to work.  I then used the "EXPORT display" trick to set the background to my own, as I like that better.

Unfortunately, all htese fixes only work when I log out.  If I switch users instead, gdm retains the ugly gray theme + orange background.

I can't remember if I've rebooted or not, so I'll try that and get back to you if it works.  If I don't, it obviously didn't work.

---

### Post by Levviathor on 2009-12-03
YES!

I ran 'sudo -u gdm ... ' in a virtual terminal at the 'switch users' screen, then rebooted.  I don't know if separately changing the 'logged out' and 'switch users' screens was necessary, or if it just needed a reboot.

I'm hoping that this whole process can be streamlined in Lucid...
>_>

Thanks to all of you for your help.  Now, if only I can figure out why editing posts doesn't work.  The throbber just sits there endlessly.

Sounds like a job for a new thread.  :D

---


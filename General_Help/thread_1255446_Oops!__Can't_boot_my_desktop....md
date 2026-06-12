---
title: "Oops!  Can't boot my desktop..."
date: 2009-09-01
forum: General Help
---

### Post by FokkerCharlie on 2009-09-01
Hello!

Well, something very strange has happened to my setup.  Today I have had my lappy on most of the day, but all of a sudden the desktop stopped working.  The mouse pointer was movable, but remained an 'I-bar' symbol, and nothing responded to any clicks.  The system monitor applet stopped working, so after a couple of minutes, I ctrl-alt-bkspc'd to restart X.  The GDM loaded fine, I entered my username/password, and was presented with a black screen, with the mouse cursor only (the 'please wait' type).

Further attempts at logging in give similar results.  Sometimes just the black screen, sometimes I see my wallpaper, sometimes a blank panel, but no more than that so far.  Another user on the same machine works fine.  Dmesg reports nothing obvious- segfaults from ekiga and syndaemon, both of which are in my sessions to load on login.

Before the problem started, I had installed gnome-do (since uninstalled from the failsafe terminal, which works fine, just in case), and was also trying out some programming- I had been playing with bonobo servers and trying (unsuccessfully) to make a panel applet in Python.  I suspect that this is where the root of the problem lies.

Starting a 'Failsafe Gnome' session also fails in a similar fashion...

please help... I await your wisdom!

Charlie

Specs:
Ubuntu 9.04 64, Acer 5920G, Intel Core2Duo, Nvidia proprietary drivers

---

### Post by P4man on 2009-09-01
a quick, but rather drastic way that will probably get you back in business is renaming your homefolder and making a new one. You will lose all your personal settings, but you can copy files over (including config files) from the renamed home folder.

In the grub menu, press esc, and select the recovery option. Then a root shell. Type:

```

mv /home/yourusername /home/yourusername.backup
mkdir /home/yourusername
chown yourusername:yourusername /home/yourusername
reboot
```

---

### Post by FokkerCharlie on 2009-09-01
Thanks, P4man

I have got myself up and running again (for the time being at least!) by doing:

gconftool-2 --recursive-unset /apps/panel

Which allowed me a usable desktop.  After logging in, I saw that the gnome-panel process was using 20-30% CPU, and shortly thereafter, it crashed.  I logged in again, deleted the extraneous bonobo server files that I had created earlier, and after yet another login, all seems to be OK.

I'll come back if the problem continues.  Serves me right for thinking I could do some clever coding....

Cheers!
Charlie

---

### Post by petrus4 on 2009-09-01
> **FokkerCharlie said:**
> 
please help... I await your wisdom!

If you can get to the failsafe terminal, do this:-

```
cd /boot/grub
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
sudo nano menu.lst
```

Now scroll down to where it says something like:-

```
title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
```

Delete the two words "quiet splash," save the file with nano, and reboot.  Go into the usual default boot type, and wait and see what happens.

That won't prevent the crash, but what it **will** do is allow you to actually watch the boot procedure so that you can figure out what is going on, rather than just stopping at a black screen.  You've probably got one of the daemons that load on startup crashing for some reason; that will let you figure out which one it is, so you can go back in with the failsafe terminal, and remove it.

Whoever had the brilliant idea of using the quiet splash options in Grub, for Ubuntu, needs to have some very painful and unpleasant things done to them.  Waterboarding would probably suffice. ;)

---

### Post by FokkerCharlie on 2009-09-02
Thanks for the response, Petrus.

My panel-related fix seems to have worked... but while we're on the subject, the removal of 'quiet splash' from Grub is an interesting one.  As my issue seemed to be happening AFTER login, would the problem have shown up here?  I will try next time if I see something similar!

Thanks again to both of you for your replies, they are much appreciated.

Charlie

---

### Post by P4man on 2009-09-02
you can type
```
dmesg
```
in a terminal to see the kernel boot log after logging in. If its too long to read,  you can write it to a file with "dmesg > file.txt", or look it up in the log viewer in system > administration.

---


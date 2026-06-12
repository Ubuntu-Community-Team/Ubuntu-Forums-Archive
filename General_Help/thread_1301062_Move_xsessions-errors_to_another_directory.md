---
title: "Move xsessions-errors to another directory"
date: 2009-10-25
forum: General Help
---

### Post by raptir on 2009-10-25
I'm using Xubuntu Karmic Koala on an Asus Eee 1000. I'd rather not have log files written to the SSD, so I moved /var/log, /var/tmp and /tmp to a tmpfs. That seems to take care of most of the log/temporary files, but I still have .xsessions-errors in my home directory. Is there a way to move it to /var/log? I tried the trick of denying write access to .xsession-errors, but now it's created .xsession-errors.XX0GEG2U and etc. Is there any way to change the directory it writes to?

---

### Post by raptir on 2009-10-25
What program even manages .xsession-errors? Is it GDM, or is it the X session itself?

---

### Post by P4man on 2009-10-25
I thought you can delete .xsessions without much side effects if you never tweaked it. Dont kill me if thats not true though (rename it is perhaps safer :) )

BTW, and for what its worth, those errors are most commonly the result of using sudo with graphical apps like nautilus, instead of using gksudo (or gksu).

---

### Post by raptir on 2009-10-25
Sorry, I guess I wasn't specific enough. I don't want to move the files that are currently there, I want to change it so that .xsession-errors will be created in /var/log instead of in my home directory, for the sake of saving wear on a localized part of my SSD. Especially since EXT4 doesn't support wear-levelling.

---

### Post by P4man on 2009-10-25
Sorry I misread.

I believe its /etc/X11/Xsession that writes it.

There is a variable ERRFILE=$HOME/.xsession-errors
You can probably change that

BTW, most SSDs do the "wear leveling" themselves.

---

### Post by raptir on 2009-10-25
I tried changing the ERRFILE variable to /var/log/.xsession-errors, but it's still creating it in $HOME directory. /var/log is a tmpfs with mode 1777, defaults and noatime. Any other suggestions?

---

### Post by P4man on 2009-10-26
Thats odd. I assume you did restart X?
Perhaps try if changing it to /dev/null makes it stop writing it at all?

---

### Post by raptir on 2009-10-28
I tried /dev/null, it still writes to my home folder.

---

### Post by raptir on 2009-10-28
In attempting to boot without a display manager, I addded this to my ~/.profile:

```
pgrep X &>/dev/null; [ $? = 1 ] && startx
```

And that seems to have stopped the xsession-errors from being written. I'd like to figure out auto-login without a display manager, though.

---

### Post by gmc on 2009-11-02
I'm in the same boat as you. I rgrep'ed the entire /etc directory and changed all references to $home/.xsession-error to /dev/null but still no joy.

This very frustrating.

G

---


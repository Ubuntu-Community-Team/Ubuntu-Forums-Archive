---
title: "All I did was log out!"
date: 2009-08-22
forum: General Help
---

### Post by n2stc on 2009-08-22
Then I selected GNOME for my session type.  I had never installed GNOME.  Some limited GNOME desktop comes up with no way to log out so I can pick my KDE session again.  No terminal either.  Just some desktop shortcuts, dolphin is among them.  How can I set the default session from ctrl-alt-F2?

---

### Post by blueshogun on 2009-08-22
ctrl + alt + backspace will "log you out" and allow you to choose your session and log in again.

---

### Post by n2stc on 2009-08-22
> **blueshogun said:**
> ctrl + alt + backspace will "log you out" and allow you to choose your session and log in again.

I wish it was so. ctrl + alt + backspace does nothing, & hasn't since I upgraded to jaunty.  Thanks for the reply though....

---

### Post by wojox on 2009-08-22
Ctrl+Alt+Delete. You have to wait about a half second in between each key press.

---

### Post by zkriesse on 2009-08-22
CTRL + ALT + DELETE...and you really should go with Ubuntu...I found that KDE is not as reliable as the Gnome desktop.

---

### Post by n2stc on 2009-08-22
> **Zachk18 said:**
> CTRL + ALT + DELETE...and you really should go with Ubuntu...I found that KDE is not as reliable as the Gnome desktop.

Thanks.  That gives 4 choices.  Sleep, Hibernate, shutdown & restart.  No log-out. I install gnome trying to cure this (about 1/2 hour) but can't select it as a session.

---

### Post by zkriesse on 2009-08-22
Hmm....do you have a live cd version of ubuntu jaunty? if so you could do a fresh install of that and then install KDE if you like it so much. or just a KDE disk by itself.

---

### Post by n2stc on 2009-08-22
> **Zachk18 said:**
> Hmm....do you have a live cd version of ubuntu jaunty? if so you could do a fresh install of that and then install KDE if you like it so much. or just a KDE disk by itself.

I do, but I was trying to avoid wiping everything out.

---

### Post by zkriesse on 2009-08-22
do you have a portable hard drive? to find out the usage of your hard drive type this command in the terminal then post the results. "df -h" WITHOUT QUOTES!!!!

---

### Post by Ms_Angel_D on 2009-08-22
try this Key combo I believe it does the same as what ctrl-alt-backspace used to do

alt-sysreq-k

---

### Post by n2stc on 2009-08-22
> **Ms_Angel_D said:**
> try this Key combo I believe it does the same as what ctrl-alt-backspace used to do

alt-sysreq-k

Thanks, but that doesn't work either.  I did solve it by editing my .dmrc file to say "Session=kde".

After fixing it I went back and selected gnome again (as I'd like to switch).  Same result.  I'll mark this as solved and work on that.  Thanks to all!

---

### Post by n2stc on 2009-08-22
> **Ms_Angel_D said:**
> try this Key combo I believe it does the same as what ctrl-alt-backspace used to do

alt-sysreq-k

That re-starts the KDE session.
:)

---


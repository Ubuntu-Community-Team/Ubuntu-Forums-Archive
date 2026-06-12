---
title: "How do I exit gksudo nautilus"
date: 2011-10-13
forum: General Help
---

### Post by 02darkRS on 2011-10-13
When I enter gksudo nautilus I lose my command line...... it just hangs out at:
darkrs@darkrs-A780L3G:~$ gksudo nautilus
Initializing nautilus-gdu extension

how do i get out of this? if i click X I recv:
Close this terminal? 
There is still a process running........

---

### Post by WorMzy on 2011-10-13
Press Ctrl+C to send a interrupt signal.

---

### Post by 02darkRS on 2011-10-13
:pthat's almost funny considering i've sent that signal 100 times in error attempting to copy......... thanks. 

does this hanging up relate to some sort of error or is this what you always have to do?

---

### Post by pretty_whistle on 2011-10-13
@02darkRS

If you're done with the work you had opened nautilus for, simply close the window and when it says there's something still running "close the terminal?"  just hit 'close terminal'.

It wont hurt anything.

---

### Post by pretty_whistle on 2011-10-13
> **02darkRS said:**
> :pthat's almost funny considering i've sent that signal 100 times in error attempting to copy......... thanks. 

does this hanging up relate to some sort of error or is this what you always have to do?

It's no error, it's being technical, that's all.

And yes, you always have to do it.

---

### Post by WorMzy on 2011-10-13
Ctrl+Shift+C should copy in gnome-terminal. (Ctrl+Shift+V for paste)


As for the hangup itself. I can't say for sure what's causing that. nautilus-gdu is part of the gnome-disk-utility package; and is presumably responsible for listing your disks' partitions.

You could try reinstalling gnome-disk-utility:
```
sudo apt-get install --reinstall gnome-disk-utility
```

I doubt it'll help though.

---

### Post by pretty_whistle on 2011-10-13
> **02darkRS said:**
> :pthat's almost funny considering i've sent that signal 100 times in error attempting to copy......... thanks. 

does this hanging up relate to some sort of error or is this what you always have to do?
That's just how it closes.  No biggie.

---

### Post by 02darkRS on 2011-10-13
thanks everyone..... this whole trial seems to be getting easier!

---


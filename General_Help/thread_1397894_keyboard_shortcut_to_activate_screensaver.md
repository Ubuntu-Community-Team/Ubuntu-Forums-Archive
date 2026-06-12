---
title: "keyboard shortcut to activate screensaver?"
date: 2010-02-03
forum: General Help
---

### Post by linuxgrrl on 2010-02-03
I have a HTPC and need to be able to activate screensaver using a hotkey.  (Screen lock won't work, don't want to enter a password).  Any ideas?

---

### Post by NT4usB on 2010-02-03
Ctrl+Alt+l (That's a lower case L, not a one(1))

---

### Post by linuxgrrl on 2010-02-25
OK, thanks, but that requires a password to unlock.  Is there any way to activate the screensaver WITHOUT locking the screen?

---

### Post by raktarok on 2010-02-25
This command does the trick:
```
 gnome-screensaver-command -a
```

Set it up as a launcher, or bind it to some key.

---

### Post by linuxgrrl on 2010-02-26
yay, perfect, thank you!  

Now one other thing .. is there a similar command to eject a CD?  I have been opening sound-juicer to eject, but that seems cumbersome.

---

### Post by raktarok on 2010-02-26
You are welcome, glad it worked for you.

For ejecting cd, you can try this - works in my laptop:

```
eject /dev/cdrom
```

---

### Post by stinkeye on 2010-02-26
For me simply 
```
eject
```
to open cd

and
```
eject -t
```
to close

or
```
eject -T
```
open/close toggle

---

### Post by linux.girl on 2011-10-25
Hello,

I tried to use the hotkey you gave, but it didn't work, it tells me that gnome screensaver is not installed. I have installed xscreensaver and during the installation process, I had to uninstall gnome-screensaver. Under those circumstances, what would be the screensaver hotkey to be used? I have ubuntu 11.10.

Thanks in advance,

linux.girl

---

### Post by linux.girl on 2011-10-28
Hello, I still haven'd found a solution for this...does anyone have more suggestions? 

Thanks in advance,

linux.girl

---


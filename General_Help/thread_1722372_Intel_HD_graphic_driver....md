---
title: "Intel HD graphic driver...???"
date: 2011-04-05
forum: General Help
---

### Post by robertcoulson on 2011-04-05
When I was doing some updates,i seem to have lost ( I guess) my Intel HD graphics driver...??...can't play any games at all...Even games like tux racer will download but not even come up to try to play it...Don't know what is happening...Should I download and reinstall the driver and where would I get it for Ubuntu...???
Thanks for any help, Robert

---

### Post by pqwoerituytrueiwoq on 2011-04-05
I have never seen a intel video card not work out of the box they usually work better than intels version for windows
what does this command give you
```
lspci | grep VGA
```

---

### Post by lithopsian on 2011-04-05
The key package would be xserver-xorg-video-intel.  You could try forcing a reinstall and see if that helps, but if you can cope, it might be best to do a bit of sleuthing before you do anything that could make things worse.

lspci as mentioned
Also glxinfo and look for errors in /var/log/xorg.0.log

Then hopefully we can tell you what is wrong and a likely way to fix it.

---

### Post by robertcoulson on 2011-04-05
Well, it did work but I can't get " extra visual effects " to work or play any games...It did play games up to about 5 or 6 updates ago...Maybe reinstalling 10.10 might help...???
ROBERT

---

### Post by robertcoulson on 2011-04-05
sorry here is attachment

---

### Post by robertcoulson on 2011-04-05
Here is the "glxinfo" attachment
Robert

---

### Post by lithopsian on 2011-04-05
Hah!  Good one.  Did you install the package so you could actually run glxinfo?

Also, try "lspci -l" which will tell us exactly which Intel chip you have.  Probably doesn't matter, but useful to know.  Oh and just grep for the VGA line because it will output a lot of stuff.

I wouldn't reinstall 10.10 unless you really want to go back to square one.  This shouldn't be hard to fix.  In fact the reinstall of the drivers would probably do it.  We are just being cautious.

---

### Post by robertcoulson on 2011-04-05
Here is "lspci -l" attachment
Robert

---

### Post by lithopsian on 2011-04-05
My mistake, that should be lspci -v :confused:  But really that glxinfo and /var/log/xorg.0.log output would be much more useful.  We know you have an Intel graphics chip, but we need to know what is wrong with it.

---

### Post by robertcoulson on 2011-04-05
lspci -v attachment...don't know how to capture the whole page though...???
Robert

---

### Post by lithopsian on 2011-04-05
Just copying the text would be sufficient.   Post it here inside code tags.  Luckily that page contained the interesting bits for lspci.  Now we need glxinfo and /var/log/xorg.0.log.  Use package manager to install mesa-utils.

---

### Post by robertcoulson on 2011-04-05
mesa-utils....Is already installed...See "glxinfo" attachment
Robert

---

### Post by lithopsian on 2011-04-05
Yikes!  No wonder your games don't work.  Package for that should be libgl1-mesa-glx.  Again, best to check /var/log/xorg.0.log before doing anything.  It might tell you why that driver isn't getting loaded.  Might just be something wrong with your configuration or it might be that the driver itself has gone walkabout.

---

### Post by robertcoulson on 2011-04-05
How do I find the "/var/log/xorg.0.log"..???
Robert

---

### Post by lithopsian on 2011-04-05
How do you find it?  It's a file.  Use your favourite file manager.  Nautilus?  I use Thunar but that isn't the default in Ubuntu.  Or use a terminal:
```
more /var/log/Xorg.0.log
```  Note the capital X:lolflag:

---

### Post by robertcoulson on 2011-04-05
more /var/log/Xorg.0.log....I don't know how to print ALL that info...???...Sorry...Maybe a reinstall would be easier...What do you think, or just live with what I got now...???
Robert

---

### Post by robertcoulson on 2011-04-05
lithopsian Thanks for all your patience and help.
Robert

---


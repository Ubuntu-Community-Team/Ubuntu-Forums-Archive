---
title: "Blender on 9.10"
date: 2009-12-29
forum: General Help
---

### Post by wolfenden on 2009-12-29
Can anyone please help me get Blender to work?!  I am losing the will to live going round in circles with posts about graphics drivers I don't understand.  I have removed compiz in favour of metacity (I don't care if my windows wibble or are appealingly translucent as long as I can run the programs I need ](*,))  I have every graphics driver I have seen mentioned marked in Synaptic package manager.  I have an aged Inspiron 5100 with an ATI Radeon Mobility 7500, I know both these products seem to have been wonky from the start, but they worked just fine with 9.04.
9.10 is otherwise an excellent step for my laptop, but Blender just starts to load, flashes up a grey screen then disappears.
Thanks in desperate hope 
W

---

### Post by taurus on 2009-12-29
Try running it from a terminal to see if there is any error message.

Applications -> Accessories -> Terminal
```
blender
```

---

### Post by wolfenden on 2010-01-05
Hi there
Here we go...

Compiled with Python version 2.6.4.
Checking for installed Python... got it!
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  29
  Current serial number in output stream:  29

Is it enlightening?
Best
R

---

### Post by wolfenden on 2010-01-07
I found this thread from searching the Terminal error messages
[http://ubuntuforums.org/archive/index.php/t-1054235.html](http://ubuntuforums.org/archive/index.php/t-1054235.html)
And thought it would solve it, but it just reduced the machine to low graphics mode until I tagged everything with ATI in the title in Synaptic, which drop me right back to where I started...
There must be a way, Blender not running on Ubuntu, ridiculous, my laptop isn't that old that it shold present a problem!

---

### Post by aklo on 2010-01-07
Blender can be open in 9.10 i downloaded and ran the full screen version. ....as for actually doing something on it i'm not sure...since i have not read my ebook blender tutorial :D

---

### Post by wolfenden on 2010-01-11
After trying all manner of routes I came to try turning off DRI in xorg.conf.  This provoked it to request a start into failsafe graphics...and blender worked.
Looking at the failsafe xorg.conf it uses VESA video driver, which I understand to be a minimal, last resort option (indeed failsafe), but everything seems to look normal and Blender is working. So I've copied the failsafe detials into xorg.conf and will proceed from there.  Resolution looks like it's dropped a slot, but not enough to be a problem, can you increase resolution in VESA?
Best
R

---

### Post by llawwehttam on 2010-01-11
try downgrading your version of DRI. I had to do this as the latest was causing me problems.

---


---
title: "System Testing (checkbox) not working"
date: 2012-09-02
forum: General Help
---

### Post by Paco62 on 2012-09-02
Using ubuntu 10.04   .  When using 'administration'-'system testing' none of the tests seem to work.  I click 'test' and the test button greys out but no test occurs.  I tried reinstalling checkbox and checkbox-gtk via synaptic but it didn't work.  If I uninstall checkbox etc that will also mean uninstalling ubuntu-desktop but the notes say this is not recommended.  What will happen if I uninstall ubuntu-desktop?   Is there another way of fixing system testing without uninstalling and then reinstalling?.  (This problem started after I had a lot of trouble installing drivers for new nvidia card)   TIA

---

### Post by pyro.xyz on 2012-09-02
Try running this program under the safe-mode option in grub. I find that sometimes if a program doesn't work the way it should in the normal environment, it might work in safe-mode.

---

### Post by Paco62 on 2012-09-02
> **pyro.xyz said:**
> Try running this program under the safe-mode option in grub. I find that sometimes if a program doesn't work the way it should in the normal environment, it might work in safe-mode.

Do you mean in full-screen command prompt mode or in low-graphics mode?  I specifically want to check my new nvidia card, so low-graphics won't do it.

---

### Post by opensshd on 2012-09-02
try 
```
sudo apt-get install --reinstall checkbox checkbox-gtk
```

You can reinstall software that ubuntu-desktop depends on without removing ubuntu-desktop in this manner. Does that help?

---

### Post by Paco62 on 2012-09-02
> **opensshd said:**
> try 
```
sudo apt-get install --reinstall checkbox checkbox-gtk
```You can reinstall software that ubuntu-desktop depends on without removing ubuntu-desktop in this manner. Does that help?

I tried that code using terminal but it didn't work.  It seems the only way is by uninstalling checkbox but that would mean uninstalling ubuntu-desktop.  Is there any other way?

---

### Post by Paco62 on 2012-09-03
I tried via synaptic completely removing checkbox, and checkbox-gtk and ubuntu desktop and then reinstalling, but system testing still does not work.  Any ideas?

---

### Post by Paco62 on 2012-09-03
I solved it by installing checkbox-cli (command line interface) and was able to successfully do the video tests.  The gui version of checkbox still does not work though, would like to get it back anyway.

---

### Post by opensshd on 2012-09-04
Hmm, good problem solving :) GUI < CLI!

To try and troubleshoot the gui's problem, try executing it from the command line - does it show any error messages in the output when you try and launch it?

---


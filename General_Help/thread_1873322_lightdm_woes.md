---
title: "lightdm woes?"
date: 2011-11-01
forum: General Help
---

### Post by Atamisk on 2011-11-01
Hello all, 

I'm experencing some issues with lightdm. I have Xubuntu 11.10 installed over a vanilla 11.10 install, which means i have both Unity and XFCE Sessions. When i try to log into XFCE from lightdm, i intermittantly get stuck somewhere in the middle of XFCE's initialization. I'm left with the log-in screen's background, usually conky, and nothing else. When i stop lightdm and start XFCE using startx, it pops right up with no issue. 

Any ideas on where to track this silliness down?
Thanks, 
Aaron

---

### Post by 2F4U on 2011-11-01
Did you look into .xsession-errors in your home folder?

---

### Post by Atamisk on 2011-11-02
I did look at the contents of .xsession-errors, but it didn't tell me a whole lot, except that it's compiz that's freaking out. i don't know if there's an error earlier in the setup or not. I'm assuming something happens in lightdm that breaks compiz's startup, because when i use a symlinked copy of the xinitrc that XFCE-session uses, i can use startx and fire right up with zero issue. Lightdm shows no obvious errors or warnings.  

[Here's the .xsession-errors file]("http://paste.ubuntu.com/726236/") if you want to see....

---


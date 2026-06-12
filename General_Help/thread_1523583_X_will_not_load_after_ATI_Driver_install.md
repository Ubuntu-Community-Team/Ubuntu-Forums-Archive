---
title: "X will not load after ATI Driver install"
date: 2010-07-03
forum: General Help
---

### Post by happysumo on 2010-07-03
Hi,  After installing the ATI drivers from ATI's website (which went fine, installation complete no worries) on ubuntu 9.10, I've rebooted only to find X-server won't load, the last few lines of the issue being  

  xinit: Connection refused (erno 111): unable to connect to X server  
xinit: No such process (erno 3): Server error.  

 I downloaded the file ati-driver-installer 10-6-x86.x86_64.run. Also, I have a HD4890 G.Card   

 Any clues where to go from here? I'm totally stumped.  Much appreciated.

---

### Post by happysumo on 2010-07-03
Might as well post the xorg.conf file 
 
 Section "Screen" 
Identifier           "Default Screen"
DefaultDepth 24
Endsection

Section "Module"
Load "glx"
Endsection

 Section "Device" 
Identifier "Default Device"
Driver "fglrx"
Endsection

---

### Post by happysumo on 2010-07-04
ended up just doing a re-install. Back in business!

Apparently this command should have fixed it:

aticonfig --initial -f

I didn't read that when I first installed the driver, the user is meant to put that command in if X doesn't load.

---


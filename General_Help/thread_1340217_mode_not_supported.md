---
title: "mode not supported"
date: 2009-11-28
forum: General Help
---

### Post by svetlinux on 2009-11-28
I installed Xubuntu a week ago and it worked fine, everything except the sound was ok …
  However, yesterday when I turned the system on, after grub, instead of loading OS the monitor showed the following message: 
  ‘mode not supported
H: 75.0 KHZ V: 60.0 HZ’
  Now I can enter only Recovery mode. A friend of mine, who is quite more acknowledged with Linux suggested to reset the X Window System, so I deleted  ~/.config and started X, but the same disgusting message appeared again…
  Any suggestions what might be the problem? Maybe something with VGA drivers… ?

---

### Post by cariboo on 2009-11-29
The message you are getting is cause by the horizontal sync and the vertical refresh rates are not set properly in /etc/X11/xorg.conf.

What type of graphics card do you have?

---

### Post by svetlinux on 2009-11-29
Ati hd 3600

---

### Post by svetlinux on 2009-12-03
OK, I have searched in the web and found this  command -
# sudo dpkg-reconfigure -phigh xserver-xorg 
  
Is  this the right tool in my case???

---


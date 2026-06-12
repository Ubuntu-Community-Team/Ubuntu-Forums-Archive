---
title: "change keyboard in ubuntu server"
date: 2011-08-04
forum: General Help
---

### Post by reza.adinata on 2011-08-04
Hi all,

I have a problem with keyboard in ubuntu server 11.04. My computer is using german keyboard, but the ubuntu server runs english. I need to adjust the keyboard to use german (currently it is US keyboard), but still runs english language. 

I tried using console-data, when I first installed, I can type QWERTZ on my ubuntu server. But when I restarted, it got back to QWERTY. I tried to rerun the console-data, but it does not work. 

How can I permanently change the keyboard in ubuntu server, so it runs german keyboard, but with english language?

Thank you

---

### Post by reza.adinata on 2011-08-04
Solved :
dpkg-reconfigure keyboard-configuration

instead of dpkg-reconfigure console-setup.

---

### Post by two00lbwaster on 2013-02-16
> **reza.adinata said:**
> Solved :
dpkg-reconfigure keyboard-configuration

Thanks for this.  I found it via Google when I was trying to work out how to do the same thing, but US > UK keyboard.  Piping to Grep is far easier now :)

---


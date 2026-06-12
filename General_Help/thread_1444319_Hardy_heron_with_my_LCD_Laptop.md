---
title: "Hardy heron with my LCD Laptop"
date: 2010-04-01
forum: General Help
---

### Post by Cyi3ian on 2010-04-01
Hi, Everyone
I'm Just a newbie here
my OS is ubuntu 8.04 LTS
I tried to install chrome9 driver
chrome9.83-242-u804 on my laptop
after i have installed that
my laptop is umm..
like this picture..
[IMG]http://img260.imageshack.us/img260/5818/01042010161.jpg[/IMG]

but when i use external monitor 
the external monitor is fine
but my laptop still no change :( 

what does i should do? 
can't anyone help

ps. sorry, my grammar was very bad

---

### Post by Bungler on 2010-04-01
Do you use the proprietary drivers of you video card, or what else do you use?
The first thing you can do is reset the X-server, you will need to reset you settings and re-install your original driver afterwards, but at least you can get your display back (well usually...):
- Press Esc during boot (or select boot in commandline only mode right away)
- Login in command line mode

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

restart:

```
sudo reboot
```

---

### Post by Cyi3ian on 2010-04-01
Thank you for help
but If i use original driver
3d accel doesn't working
I was download this driver from**  linux**.via.com.tw/

any the other way?

---

### Post by Bungler on 2010-04-07
Perhaps just start by reconfiguring them?

```
dpkg-reconfigure xserver-xorg
```

---


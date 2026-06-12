---
title: "Garbage on screen after boot up"
date: 2009-06-29
forum: General Help
---

### Post by Cuerzo on 2009-06-29
Hi!  I really need help with this, I'd really appreciate if you could give me a hand.  I've been working with Jaunty for a few months now, very happy with it.  Recently I tried installing the ATI drivers, since I read that it was the solution for slow fullscreen videos in Youtube and stuff. I have an ATI Radeon 7500.  Anyway, after installing both the ATI drivers and Catalyst from Add/Remove, I rebooted. Everything was normal: Grub loads normally, splash screen shows up, bar fills normally... and then, onscreen garbage.  A top portion of the screen is garbage, while the bottom part is my desktop (I have autologin set). After that, the screen flickers once or twice and garbage changes: The bottom part is now garbage, and the top part is various things that were on the screen recently: A row with the Ubuntu splash repeated, and another row with the BIOS splash (!)  This obviously happened right after I installed the ATI drivers: Everything was alright before. How can I fix whatever I messed up?

---

### Post by TeoBigusGeekus on 2009-06-29
Go to System->Admininstration->Synaptic Package Manager
and uninstall the packages.

---

### Post by Legace on 2009-06-29
Reboot PC, select "Recovery mode" (you might need to press ESC) in boot-manager (GRUB) and then go for "root shell" option (you might need to press the DOWN arrow a couple of times). 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```

then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

---

### Post by Laysan_A on 2009-06-29
You didn't include any system specs. in your post (you might think about putting them in your sig).

If you have a 64bit system you'll get much better flash performance if you install the 64bit flash from adobe. Here's a link that will tell you all you need to know (if you don't have a 64bit system, just ignore this).
[http://ubuntuforums.org/showthread.php?t=985479](http://ubuntuforums.org/showthread.php?t=985479)

---


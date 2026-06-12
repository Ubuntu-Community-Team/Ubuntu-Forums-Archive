---
title: "Graphics Fail"
date: 2009-09-02
forum: General Help
---

### Post by sheffne on 2009-09-02
I installed ubuntu today, and it booted fine.  After turning it off I cam back and now I have a graphics fail.  Basically when I boot and almost get to the desktop, my comp freaks out and gives me some sort of lines, squares and colors all over the screen.  I am running off Radeon 9600 SE video card and AMD Athlon 64 if that helps. 

Really need a solution, this is starting to piss me off.

---

### Post by PRC09 on 2009-09-02
I dont know of a solution but a little reading doesnt hurt.This may not help but ATI seems to be a problem for alot of people.


[http://ubuntuforums.org/showthread.php?t=978967&highlight=ati](http://ubuntuforums.org/showthread.php?t=978967&highlight=ati)

---

### Post by NoaHall on 2009-09-02
Boot into recovery, do "sudo apt-get remove --purge xorg-driver-fglrx" Boot again.

---

### Post by biffen on 2009-09-13
Five minutes ago, my computer looked like this: [http://biffnet.se/graphics_crash.JPG](http://biffnet.se/graphics_crash.JPG)

Now it works fine again =)

Thanks for the tip. What did I uninstall? :P

---

### Post by jocko on 2009-09-13
> **biffen said:**
> Five minutes ago, my computer looked like this: [http://biffnet.se/graphics_crash.JPG](http://biffnet.se/graphics_crash.JPG)

Now it works fine again =)

Thanks for the tip. What did I uninstall? :P
Well your problem was probably that you had tried to install ati's proprietary graphics driver, which does not support your graphics card, so you fixed it by uninstalling that driver.

---


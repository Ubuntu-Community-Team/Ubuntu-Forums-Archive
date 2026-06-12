---
title: "Wireless Keyboard issue"
date: 2012-08-29
forum: General Help
---

### Post by Snoo on 2012-08-29
Hi There,
I had a strange problem where by my wireless keyboard wouldn't work on boot up. Mouse works fine. If I unplug then replug the dongle it works.
Thinking the keyboard was duff I today bought a new keyboard/ mouse wireless combo. It's a different make, yet it does exactly the same.

Anybody any ideas what is causing this?

---

### Post by magpie03 on 2012-08-29
I had the same problem. Wireless mouse/keyboard combo and a wireless trackball. I was running Ubuntu 12.04 but it was to buggy so I went back to 11.10. Same problems in both versions. Sometimes mouse or trackball would work. Sometimes keyboard only. I would just reboot till they all worked. I do not know why they all work now, but after about four days of trying to firgure it out, it just started working. When you boot up and only have a mouse or keyboard working, reboot it first without removing the dongle and see if they both work. May have to do it a couple times. If you get them working, you may have to do it again the next day, but like I said, after the third or fourth day Ubuntu seems to realize they are there and hopefully your problem is solved. You could also try another USB port.
Hope this helps.......

magpie........

---

### Post by Snoo on 2012-08-30
Interesting. This is actually my 3rd combo in around 3 months! I have 18 month twins and assumed they had broken them. My son likes to ride his tricycle over the keyboards! 
Seems it was actually Ubuntu though when I dragged the old ones out of their toybox.

---

### Post by Statia on 2012-08-30
Just a wild shot, but see if enabling "USB legacy mode" in the BIOS makes a difference.

---

### Post by SJR Dorset on 2012-08-30
I have a similar issue with my Logitech mouse and keyboard. After much experimentation I have found that if I hit the return key on the Grub screen the keyboard and mouse usually works when I get to the Ubuntu login screen. Because of this I have increased the time delay on the Grub screen to several minutes so I don't miss pressing the return on boot up.

---


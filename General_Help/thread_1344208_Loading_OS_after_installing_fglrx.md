---
title: "Loading OS after installing fglrx"
date: 2009-12-02
forum: General Help
---

### Post by Wish4Me on 2009-12-02
I installed fglrx the restricted driver for my Radeon HD 5850 and now I cannot boot. It brings me to a black screen (with some smudging) after the initial kubuntu loading bar.

I can load the recover mode but I don't know the syntax for disabling the restricted driver in the terminal.

I read some documentation about why this might be occuring but I couldn't find anything not outdated. The card was recently released so I am not sure if there are some driver issues or if something else is happening.

---

### Post by Wish4Me on 2009-12-02
Anyone?

---

### Post by prions on 2009-12-02
Did you remove the open source driver that came with Ubuntu? I had this problem also.


I think you go to synaptic and remove xorg-fglrx

---

### Post by Renée Jade on 2009-12-04
I had this problem a while ago. You can fix it by removing the fglrx driver. I used this howto:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

to get rid of fglrx and reinstall the ATI software. This was less thank a month ago on Jaunty. It worked perfectly for me.

---


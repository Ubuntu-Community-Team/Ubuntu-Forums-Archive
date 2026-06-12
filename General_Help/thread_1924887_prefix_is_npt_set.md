---
title: "prefix is npt set"
date: 2012-02-13
forum: General Help
---

### Post by heruvim on 2012-02-13
I install ubuntu 11.10, using wubi. It asks to reboot.
I reboot, than the message in bios: try hd(0,0) prefix is not set. Than  it disappears and installation completes. After one more reboot.
Again this message: "try hd(0,0) prefix is not set". And i enter ubuntu.  But there is some problem with the screen it doesn't show the working  place properly, only stripes in different colors and loading logo of  ubuntu 5 times in a line. (i can be false with terms) 
I can open ctrl+alt+f1 and screen becomes black, i even can see that there are some strings, but can't see the letters. So I uderstand that OS have a response on my actions, but visually - impossible to see anything
I tryed to burn iso on disk and use "try it", booting from disk
It displays me language select and after I choose it, there is only black screen 

What shall I do?
thank you all for attention

---

### Post by ajgreeny on 2012-02-13
When you get to the "Try Ubuntu" option menu hit F6 and try the various boot options starting with **nomodeset**, but if that is no good try the others one by one.

---

### Post by heruvim on 2012-02-13
Thank you - it has helped me to boot from disk and load "Try it"
All is clear and properly seen. But the problem with already installed ubuntu isn't solved.

---

### Post by bcbc on 2012-02-13
Press 'E' on the first entry in the grub menu, add nomodeset and Ctrl+X to boot. See here for more info: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

PS the 'prefix' not set error is meaningless - it shows on all wubi installs since 11.04 until such time as the grub devs remove it or its cause. It doesn't signify any problem.

---

### Post by heruvim on 2012-02-14
Thank you very much, All is being working now

---

### Post by Rubi1200 on 2012-02-14
Excellent! 

You got the best help possible from our 2 esteemed members.

Enjoy and please mark this Solved using the Thread Tools near the top of the page.

---


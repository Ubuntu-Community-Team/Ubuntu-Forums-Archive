---
title: "New to Ubuntu please help"
date: 2010-11-28
forum: General Help
---

### Post by ubutipss on 2010-11-28
I was given a computer that has the Ubuntu operating system installed I was able to at least get online with it. I tried to upgrade it (don't know what version was installed on it) using the Update Manager. When the computer restarted I got two error messages:
 
Error no suitable mode found
 
Error unknown command "terminal"
 
the system then went on through the Ubuntu logo screen but then I got a black screen. I couldn't get the computer to do anything. 
 
If you've had this happen and can help me on how to at least restore the computer back to its previous state before trying to upgrade I would be eternally greatful.
 
Thanks
Ubutipss

---

### Post by mikewhatever on 2010-11-28
I don't know what went wrong with that update, but that may have been a push in the right direction. Even if the computer came from a trusted source, it's probably best to format everything and reinstall.

---

### Post by jerome_rajan on 2010-11-28
Did you, by any chance, try to interrupt the update process? It would be easier to help you if you give more details. And welcome to the world of Ubuntu :)

After the initial hiccups, I'm sure you'll never want another OS

---

### Post by coffeecat on 2010-11-28
I think the OP has encountered this bug:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/519358](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/519358)

Relevant thread:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1529764](http://www.uluga.ubuntuforums.org/showthread.php?t=1529764)

However, it should have been fixed by now, so the update/upgrade should have dealt with it and the black screen after the login screen is concerning. Perhaps a video card issue? Without knowing what the graphics cards is and whether the previous owner installed a proprietary driver, this could be difficult to troubleshoot.

@ubutipss, before you do anything else, you might want to see if the latest version of Ubuntu runs OK on that machine from a live CD. You can so this without affecting what's on the hard drive in any way. And then, if it does run OK and you like what you see, you can do a fresh install from the live CD. Download the ISO for the CD from here:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

And useful instructions for getting it onto CD here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---


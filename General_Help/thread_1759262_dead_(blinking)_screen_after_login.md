---
title: "dead (blinking) screen after login"
date: 2011-05-15
forum: General Help
---

### Post by airspoon on 2011-05-15
Okay, so I just installed Ubuntu 11.04 from a USB thumb drive and the instillation seemed to work without a hitch. Even after the initial reboot, it seemed to get to the login screen okay, however after logging in, the screen is just filled with what looks like the default Ubuntu wallpaper (the "purplish" one). My computer isn't doing anything else, it's just stuck on that screen with the wall paper and no other options.
 
If I right click with the mouse, the menu that appears briefly shows, then goes away, then shows again and goes away again (slow blink). After a few minutes, it appears as if the screen locks and blinks between the "purplish" wallpaper and a blank screen. Then, when I move the mouse, the login to unlock the screen has that same slow blink.
 
Before installing Ubuntu on this computer, I ran it from the thumb drive and everything seemed to work perfectly. It's only after installing it that seems to have fried my computer.
 
Can anyone please help? My computer is a Dell P4 3ghz, 1gb RAM, 80g HDD and I installed Ubuntu 11.04 along side Windows XP Professional, giving Ubuntu the majority of the drive (70gigs).
 
Also, when starting up, the screen goes all crazy with white and black spots, where I assume the start-up senquence does its checks (like other linux distros).
 
I appreciate any help given, thanks in advance!
 
--Matt

---

### Post by fbroce on 2011-05-15
There are a couple of things you could try. I hesitate to have you reinstall the boot loader since you are trying to run XP and Ubuntu. However, I had a similar problem and ran update-grub2 and it fixed it. First you have to get to a console screen.

Try hitting alt-shift F1 when you get the purple screen. It should return you to the console login screen. Then you might try sudo dpkg-reconfigiure xserver-xorg. This should reconfigure the video. Then reboot and see what you get. If that doesn't work...you can try the update-grub2 command after logging in the console again.

Good luck.

Fred-

---

### Post by airspoon on 2011-05-15
Thanks for the reply. Alt-shift-f1 didn't do anything. It's just that purple screen with nothing other than the mouse cursor.

---

### Post by airspoon on 2011-05-15
Once I login, I can't do anything. Even trying to shut down is very difficult, as the option menu after pressing control-alt-del just flashes very briefly before being stuck again on the purple screen.

---

### Post by airspoon on 2011-05-15
How about trying to reinstall? Will it remove this current install? I believe that my Windows XP is now fried too, after trying to install Ubuntu.

---

### Post by airspoon on 2011-05-15
okay, I was just able to get a "recovery console". Is that what you were talking about? There was an option for it on the login screen.
 
Thanks.

---

### Post by airspoon on 2011-05-15
I tried typing "sudo dpkg-reconfigure xserver-xorg" at the recovery console and then I rebooted. It is still dead after I login. However, it does seem to allow me to login to "safe-mode" with everything seemingly working fine, though only in safe-mode. I don't know if this may help narrow whatever is going wrong.

---

### Post by jerrrys on 2011-05-16
has this been mention ?

[http://ubuntuforums.org/showthread.php?t=1756110](http://ubuntuforums.org/showthread.php?t=1756110)

---


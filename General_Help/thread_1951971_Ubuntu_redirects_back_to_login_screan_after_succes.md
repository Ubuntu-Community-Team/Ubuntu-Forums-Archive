---
title: "Ubuntu redirects back to login screan after successful logon"
date: 2012-04-03
forum: General Help
---

### Post by sjur on 2012-04-03
Just after I successfully login, I get a black screen with a blinking dot, and I get redirected back to the login screen. I'm able to use the guest account normally, and I still get "wrong password" when I should. This appeared right out of the blue one day. I'm using 11.10. Has anyone else experienced this? Does anyone know how to solve it?

---

### Post by ccrs8 on 2012-04-03
> **sjur said:**
> Just after I successfully login, I get a black screen with a blinking dot, and I get redirected back to the login screen. I'm able to use the guest account normally, and I still get "wrong password" when I should. This appeared right out of the blue one day. I'm using 11.10. Has anyone else experienced this? Does anyone know how to solve it?

I've experienced this sporadically starting with Ubuntu 10.10.  I'm now using Xubuntu 11.10.  When it does happen, I can usually log in successfully the second or third time.  It currently hasn't happened to me in a few weeks, but before that it was happening about every other login attempt for a few weeks.  I've read other reports of this happening to people, but unfortunately I have not seen a great solution.

---

### Post by sjur on 2012-04-03
Had it just flipped once, it would only have been a slight annoyance, but since I'm now effectively locked out from my account, I'm more than a little desperate (and since there are no other accounts with sudo rights on the computer, I feel sorta f*cked)...

---

### Post by sjur on 2012-04-04
Does anyone know how to solve this?

---

### Post by squilookle on 2012-04-04
Most likely not the same issue, but I ran into something with similar symptoms on Kubuntu 12.04 last night. I logged in, the KDE splash screen appeared for a second, then the screen went black, and then back to the log in screen. 

I'm not sure what the cause was, whether my issue was something different but with similar symptoms, or whether there is a common component in Ubuntu and Kubuntu that caused the issue, but I logged into a terminal and ran apt-get update/upgrade and restarted, and that fixed my issue. 

Are you able to try the same?

---

### Post by CrazyBillyO on 2012-04-28
I originally got my laptop back in December 2011 (running Ubuntu 11.10 64-bit), and it's been doing about that same thing since I got it:  put in and confirmed the password, screen goes black with a cursor, and then dumps back to the login screen again.  At first it seemed to only happen every other time, but I think it happened the last 2 or 3 times I started the machine, so I'm somewhat concerned it's getting worse.  The login is successful after the second attempt; I've never had the screen go black after the second attempt.

Also of note, I've noticed that the screen doesn't just go black with a cursor in it.  At least once I've seen text similar to "[ OK ]" appear in the upper-right when the screen goes black.  I'm not sure what this means or what significance this has.

---

### Post by CrazyBillyO on 2012-05-05
I have a few more details related to this.  Lately, the nVidia logo has been flashing briefly on the black screen before going back to login screen.  My laptop has a GeForce GTX 560M using the 280.13 driver, running 11.10 64-bit.  I've noticed similar, more serious issues with others running the 295.40 driver where a black screen is persistent after login.  There are other threads concerning this, such as [http://ubuntuforums.org/showthread.php?t=1967794](http://ubuntuforums.org/showthread.php?t=1967794).  The driver version is different, however, and the system isn't non-responsive after login.__[]("http://ubuntuforums.org/showthread.php?t=1967794")

---

### Post by Park Bom on 2012-05-05
I had the same issue just a couple days ago, but with Xubuntu. This is what I followed to fix it:

[http://ubuntuforums.org/showthread.php?t=1309603](http://ubuntuforums.org/showthread.php?t=1309603)

> Try switch to text console (Ctrl+Alt+F1), log in and remove file $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml, log out from text console, switch back to graphical login screen and try login again. 

I understand that you're not using xfce4, but perhaps the displays.xml applies to this situation as well? I don't know where to find it in Ubuntu though. Hopefully someone else knows!

---

### Post by CrazyBillyO on 2012-05-19
I don't see that file anywhere.  I don't think it applies in our situation.

---


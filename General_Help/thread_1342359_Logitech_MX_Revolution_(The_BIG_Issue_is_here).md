---
title: "Logitech MX Revolution (The BIG Issue is here)"
date: 2009-11-30
forum: General Help
---

### Post by expxe on 2009-11-30
Logitech MX Revolution. This is a $50 mouse. It does not work properly in linux (seems to be a recurring theme for most hardware, why is that?)

I have tried btnx and other outdated tutorials scattered around the forum. I should NOT have to go thru this to get a simple mouse to work. Do all linux users stick with basic two button mice? **Why should linux users always have to settle for less?**

Can someone who has this mouse please post a step by step guide on how to set up all the buttons and get them working? I would really appreciate the support. Thank you.

---

### Post by iNaitvad on 2009-11-30
Did you google it first? I found several solutions, i cant probe them, i dont have a MX Revolution, but this might help you...dont be lazy google...
[http://ubuntuforums.org/showthread.php?p=2727025](http://ubuntuforums.org/showthread.php?p=2727025)
[http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/howto_logitech_mx_revolution_on_ubuntu](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/howto_logitech_mx_revolution_on_ubuntu)
[http://ubuntuforums.org/showthread.php?t=277388](http://ubuntuforums.org/showthread.php?t=277388)
check those sites... maybe there is more info (more updated...)

---

### Post by goatgonads on 2009-12-01
Mine worked fine right out of the box (9.10) aside from not being able to change what the buttons do (with out having researched it). The "search" button searches, the thumb buttons work as a forward and backward on web pages.

FYI, I used the above information, installed btnx and it works great (after a restart)

Thank you [iNaitvad]("http://ubuntuforums.org/member.php?u=281980")

---

### Post by Psychodox on 2010-01-21
I also tried several of the MX Revoltion setups for older builds here and other places I found through Google. Eventually I was able to get everything to work like I hoped. I'm not sure how stable it is because I didn't find it but McGyvered it.

First install [revoco]("http://www.toosweettobesour.com/2009/05/13/logitech-mx-revolution-revoco-in-ubuntu-904-jaunty-click-to-click-even-after-a-resumewakeup/") to control the 'free' spin of the main wheel, follow the install instructions from [here]("http://www.toosweettobesour.com/2009/05/13/logitech-mx-revolution-revoco-in-ubuntu-904-jaunty-click-to-click-even-after-a-resumewakeup/") to install revoco. I used the setting <revoco auto=10,10> (<revoco auto=15,15> would be no 'free spin' <revoco auto=0,0>would be all 'free' spin)

If btnx is not installed go ahead and install btnx <sudo apt-get install btnx>
After btnx is installed start btnx configuration with <sudo btnx-config> without sudo permissions, btnx couldn't detect my mouse.
Once my mouse was detected btnx asks to hold a mouse button untill the progress bar finishes. For me this didn't occur, I even taped one of my mouse buttons for about 30 minutes, and the progress bar wouldn't get past about 20%.
Instead tap the button you want to be detected about 5? times, until the progress bar fills out then click 'add'. Do this for all the buttons on the MX Revolution and name each button something easy to remember.

Once all the buttons were added, mapping them with btnx was straight forward after that, making sure to click 'Activate' on all the customised mapped buttons.

Finally I went to Preferences>Keyboard Shortcuts and disabled search so the top 'search' button would stop doing both; searching and doing my custom mapped function on a single click.

As a matter of course I always reboot after any major change, and rebooted 2 or 3 times through this process.
(using MX Revolution & Ubuntu 9.10)

---


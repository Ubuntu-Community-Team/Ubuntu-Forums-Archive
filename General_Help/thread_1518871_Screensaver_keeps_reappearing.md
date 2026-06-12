---
title: "Screensaver keeps reappearing"
date: 2010-06-27
forum: General Help
---

### Post by ComputerJy on 2010-06-27
Hi,
I have a problem with the screensaver. I dismiss the screensaver and enter my password. A second later, the screensaver reappears, so I have to dismiss it and enter my password again.

---

### Post by hansdown on 2010-06-27
Hi ComputerJy.

You can change the length of time, before the screensaver starts.

Click system> preferences> screensaver

"Regard the computer as idle after:" can be changed with the slider, to a longer time.

If you prefer the screensaver to not lock the screen, you can uncheck the box.

---

### Post by ComputerJy on 2010-06-27
No, I want it to lock the screen. And I have configured the time. My problem is, it shows up again after I dismiss it.

---

### Post by hansdown on 2010-06-27
> **ComputerJy said:**
> No, I want it to lock the screen. And I have configured the time. My problem is, it shows up again after I dismiss it.

O.K.

May I ask which screensaver you are using? Also, which version of ubuntu.

---

### Post by ComputerJy on 2010-06-27
I'm using the BSOD screensaver on Lucid

---

### Post by hansdown on 2010-06-27
> **ComputerJy said:**
> I'm using the BSOD screensaver on Lucid

Just to be clear, are you using xscreensaver?

---

### Post by ComputerJy on 2010-06-27
I'm not really sure, this is the result of `dpkg --get-selections|grep -i screensa`
> gnome-screensaver                install
screensaver-default-images            install
xscreensaver-data                install
xscreensaver-data-extra                install
xscreensaver-gl                    install
xscreensaver-gl-extra                install


---

### Post by hansdown on 2010-06-27
I'm betting on xscreensaver.

If you look in system> preferences, you might see two screensaver options.

This is not going to help, but I wonder if it goes back to a problem in ubuntu 4.10 and 5.04.

The xscreensaver was not grabbing the keyboard, so when unlocking the screen, it was restarting.

[http://www.linuxcompatible.org/news/story/usn_269_1_xscreensaver_vulnerability.html](http://www.linuxcompatible.org/news/story/usn_269_1_xscreensaver_vulnerability.html)

The screenshot below shows the relevant part.

---

### Post by ComputerJy on 2010-06-27
As I understood, the bug says the key press is being passed to the active application window. Which is not the case here. The screensaver catches the key press, shows the password dialog, I enter my password, the screensaver is dismissed and my desktop is shown. A second or two later, the screensaver reappears. And I have to dismiss it again using the same previous steps.

Besides, I don't have the package xscreensaver installed

Thanks for the try anyway

---


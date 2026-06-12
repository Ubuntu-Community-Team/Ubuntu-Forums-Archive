---
title: "Upgrade problem: Aplications ALWAYS minimized"
date: 2010-05-02
forum: General Help
---

### Post by SKoziner on 2010-05-02
Hi! Sorry for my bad english, but I really need help.

I have upgraded my netbook from UNR 9.10 to 10.04, and after installing everything, every time I open something (a folder, aplication, movie, whatever), after a half of a second it minimize itself.

So, I cannot do ANYTHING, 'cause every time I open something go to the taskbar and I'm done, even the shuting down minimize.

I use my netbook to work, so please anything you can suggest really helps me.


Thanks!

---

### Post by ehaus on 2010-05-03
I am having the same problem.  I just upgraded yesterday (May 1).  I had Ubuntu 9.10 netbook remix, and upgraded via synaptic.

Everything installed fine, and it seems normal when I boot.  However, if I start any application, it will appear for a second or two, and then minimize itself.

Whether I click the icon in the task bar, or ALT + TAB to get back to the window, the same thing happens.

I have tried reboot the machine, opening different applications, etc.  Doesn't seem to help.

It's an ASUS EEE PC, but there doesn't seem to be anything in the forums regarding this machine.

Any suggestions on how to debug this would be greatly appreciated.

---

### Post by mje1708 on 2010-05-03
I know you guys probably don't want to hear this but I would recommend a clean fresh install rather than an upgrade. Every time i tried upgrading with whichever version of ubuntu on whichever machine I always got some problems.

But before you do that try running on a flashdrive and see if you get the same issue - if not you can safely install and know your problems will be resolved. If yes then you will know you have some sort of hardware incompatibility issue.

I have an Asus eee pc900 netbook running 10.04 netbook remix and a desktop running standard - both had issues of one sort or another when using the upgrade route. Finally installed both with a clean install and now both work great. I know it is a nuisance - putting back settings, backing up data etc but believe me it is worth it in the long run.

Regards

Mike

---

### Post by SKoziner on 2010-05-03
ehaus: It's a Samgung N210, but I think it doesn't have a relation with the hardware either.

mje1708: well, i was hopping to avoid that, but I think you're right.


so, to reinstall everything T_T

---

### Post by SKoziner on 2010-05-03
Yeah! Fixed!

To fix this, you have to uninstall the nvidia drivers who comes by default.

To make this, try to get out to you sesion, login in Gnome mode, and uninstall it with Synaptic.


Thanks for the help! :D

---


---
title: "Completely unresponsive after panel move, reboot doesn't work"
date: 2010-12-18
forum: General Help
---

### Post by Bobazonski on 2010-12-18
Ubuntu 10.04. I got bored and decided to move the panels around. One somehow got stuck on top of another and I couldn't use the panel that contained all open windows as well as the menus. I tried the ctrl+alt+tab shortcut but nothing would work, it would never focus on a panel and whatever keys I used after that would select things on the desktop.

Since I couldn't do anything with the open windows and I couldn't open any new ones, I figured a reboot might work. So I rebooted, and was welcomed by a desktop background with no icons, and only a gray box where one of the panels should have been. Completely unresponsive, all I could do was move the mouse. No keyboard commands worked.

I also tried in recovery mode with failsafe graphic configuration, no luck.

I do have a Nvidia card and drivers, I know this is often the cause of graphical issues.

Really need some help. As of now, I can't use Ubunutu at all and have to boot into Windows.

---

### Post by lmarmisa on 2010-12-18
I recommend to reset your gnome-panel to default.

Try this method. Open a text mode terminal pressing Alt + Ctrl + F1, login in to your account and type these commands:

```

mv ~/.gconf/apps/panel ~/panel.bak
sudo reboot

```If everything works fine again, you can remove the backuped panel directory using this command:

```

rm -r ~/panel.bak

```

---

### Post by Bobazonski on 2010-12-18
Thank you I'll give it a try

EDIT: It worked. Thank you very much

---

### Post by lmarmisa on 2010-12-18
> **Bobazonski said:**
> Thank you I'll give it a try

EDIT: It worked. Thank you very much

Great!!. :D

Please, mark the thread as SOLVED.

---


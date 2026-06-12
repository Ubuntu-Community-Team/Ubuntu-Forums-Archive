---
title: "can't shut down"
date: 2006-04-01
forum: General Help
---

### Post by piq on 2006-04-01
Installed Automatix and now I'm not able to shut down the computer by System and Log Out. The only option I get when I press log out, is to log out.

---

### Post by taurus on 2006-04-01
Just log out first and then pick shutdown when you get back to the GUI login screen.

---

### Post by piq on 2006-04-01
[QUOTE=taurus]Just log out first and then pick shutdown when you get back to the GUI login screen.[/QUOTE]

So I should shut it down manually by pressing the power button?

---

### Post by taurus on 2006-04-01
No, don't do that or you will damage your filesystems.  Log out and when you get back to the GUI login screen, there is an option at the bottom to let you either reboot or shutdown!!!  Do it from there, not pushing the power button...

---

### Post by piq on 2006-04-01
I haven't had to use that way to shut down the computer before. I tried to write shutdown and it said I had to be root to be able to do that, and I thougt I was, well anyway. When I wrote shut down, nothing happened. I'm sorry for not knowing how to do this. I guess I kind of need windows even in the world of linux.

---

### Post by taurus on 2006-04-01
If you want to shut it down before you log out, then open a terminal and run this from the prompt,
```

sudo shutdown -h now

```
Otherwise, log out and from the screen that you see when you just boot Ubuntu, pick the shutdown option from there!!!

---

### Post by piq on 2006-04-01
This happens:

Broadcast message from root (pts/0) (Sun Apr  2 01:45:01 2006):

The system is going down for system halt NOW!


... and then nothing

---

### Post by Omnios on 2006-04-01
wrong post lol

---

### Post by piq on 2006-04-01
glad I could make you happy

---

### Post by piq on 2006-04-01
Can someone please help me! What should I write in the terminal to get the computer to shut down?

---

### Post by taurus on 2006-04-01
Can you log out from Gnome???

Here's a screenshot of your desktop, [http://shots.osdir.com/slideshows/slideshow.php?release=465&slide=24](http://shots.osdir.com/slideshows/slideshow.php?release=465&slide=24), so click on the System and Log out!  Then, you will see this screenshot, [http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=26](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=26), or something similar to that!  Do you see anything interesting at the bottom left corner???

---

### Post by Ramses de Norre on 2006-04-01
Does sudo init 0 work?
sudo halt maybe..
Also try the loging out.

---

### Post by piq on 2006-04-02
Yes, I can log out of Gnome, but when I log in again I don't get the window with Ubuntu-logo and options to log in or shut down. Is it possible to start the x-window without being logged on?

---


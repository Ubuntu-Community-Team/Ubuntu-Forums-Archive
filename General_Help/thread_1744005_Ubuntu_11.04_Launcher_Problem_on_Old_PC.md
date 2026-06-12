---
title: "Ubuntu 11.04 Launcher Problem on Old PC"
date: 2011-04-30
forum: General Help
---

### Post by GMayank on 2011-04-30
I am a newbie to the world of Linux. Recently, I have upgraded to Ubuntu 11.04. But after upgrading some problems, firstly I'm unable to see the Launcher bar and the Unity interface.

I have initially installed Cairo-Dock which is the only thing that still appears on Desktop. Also my PC is quite old.:oops: Here is my PC configuration:
System: Windows Xp Sp3
        Intel Pentium 4 with 3.06 Ghz
        760 MB RAM.

Thanks in advance.

---

### Post by mem101296 on 2011-05-01
Same with me, I had Ubuntu 10.04 and upgraded to 11.04 and the top bars gone, so is the launcher bar. I can open the terminal thanks to the keyboard short cut. But i cant use any apps with out using terminal. I have an Acer Aspire One D55. Ever thing that would be on the tops bars there I just cant see them. I need help too.

---

### Post by einoj on 2011-05-03
I registered to say that I have the same problem with my asus 1015pm after updating to ubuntu 11.04.

I don't remeber exactly what version I upgraded from. I think it was the newest version of the netbook ubuntu that was available in the first week of march, which was when i installed the OS on my 1015pm.

---

### Post by osama ibrahim on 2011-05-03
[B]Unity doesn't work with your computer's hardware? You have 3 options:
[/B]- in the login screen, select the **"Ubuntu Classic"** session and everything will look like in Ubuntu 10.10 (except for updated packages and overlay scrollbars).
- [B]use Unity 2D:
[/B]```
sudo apt-get install unity-2d
```- **install GNOME 3 with GNOME Shell** via [GNOME 3 PPA]("https://launchpad.net/%7Egnome3-team/+archive/gnome3") (warning: you won't be able to use Unity after using this PPA) or if you want to use both Unity and GNOME Shell, [compile it yourself]("http://www.webupd8.org/2010/10/install-gnome-shell-from-git-in-ubuntu.html") (this will allow you to easily switch back to Unity if you want).


SOURCE:[http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html](http://www.webupd8.org/2011/04/things-to-tweak-fix-after-installing.html)

(The second option Works with me perfectly................)

---


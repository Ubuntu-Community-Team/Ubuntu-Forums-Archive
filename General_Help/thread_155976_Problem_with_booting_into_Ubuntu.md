---
title: "Problem with booting into Ubuntu"
date: 2006-04-06
forum: General Help
---

### Post by socialreject on 2006-04-06
Okay, so I installed Ubuntu 5.10 for the second time and when I boot up the computer into Linux it runs some checks (all of which checked 'OK') stays in DOS mode with the old fasioned black screen 'n gray text and prompts me for my username and password.. I enter it and it shows me some text about how the third-party apps bundled with Ubuntu are copyrighted or some other stuff and something about "NO WARRANTIES" (If you want a full quote I can reboot the computer and check). After entering my user name and password and then it says something like "alex@ubuntu:~$". I've tried entering various stuff but no luck. Is this a common problem that's easy to fix or what?
Any help is appreciated, and if you need more information, I'll try to answer as best as I can.

Thanks in advance.

---

### Post by localzuk on 2006-04-06
How did you install it? Did you do a server install or a normal install? If you did a normal install, try typing startx at the prompt and see if it launches the GUI. If it doesn't, it will provide you with some error data (use arrow keys to scroll down when it does). Provide us with the errors that are shown.

---

### Post by socialreject on 2006-04-06
I did a server install

---

### Post by Sutekh on 2006-04-06
Then there is no problem/error.

By choosing a server install you didn't install a GUI/desktop environment

Have a look at this site, and click on the Desktops at the bottom for some screenies on some environments, and maybe you can decide what you want.

[http://xwinman.org/]("http://xwinman.org/")


If you want [GNOME](www.gnome.org) - Default Ubuntu Desktop, I'd use this command
```
sudo apt-get install ubuntu-desktop
```When prompted for a password, use your login one.

If you want [KDE](www.kde.org) - Most Common Linux Desktop, I'd use
```
sudo apt-get install kubuntu-desktop
```

If you want [XFCE](xfce.org) - very light desktop, I'd use
```
sudo apt-get install xubuntu-desktop
```

These commands will install the respecitve desktops with most of the basic programs you will need.

---

### Post by socialreject on 2006-04-06
Thanks! It worked great. After sitting through 10 minutes of it installing more packages it prompted with another "alex@ubuntu:~$". I didn't know what to do so I just rebooted hoping nothing would mess up. I booted into Ubuntu and it ran another one of those checks and everything worked. Again, thanks:D

Now I'm off to find some programs

---

### Post by localzuk on 2006-04-07
Can I ask you why you did a server install? :)

---

### Post by socialreject on 2006-05-24
It was the only option I saw that wouldn't overwrite Windows.

..and sorry for bumping a month and a half old thread.

---


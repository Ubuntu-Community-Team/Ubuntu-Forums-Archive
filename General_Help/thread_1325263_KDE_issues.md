---
title: "KDE issues"
date: 2009-11-13
forum: General Help
---

### Post by Butterknife on 2009-11-13
It's been ages since I worked in KDE, and every time I tried in the past few years, I was unable to configure wireless network, so having a laptop, it was pointless running KDE. The other day, I decided to give it another go and I installed the environment, which seemed to work, judging by no errors returned and boot screen changing from Ubuntu to Kubuntu. I switched to KDE using terminal so after restart I was able to log in to it. However, after login, all I could see was an open terminal and nothing else. Nothing. No panels, no icons, clicking anywhere on the desktop did nothing at all, couldn't move around terminal window, no keyboard shortcuts launched anything and by then I've had enough and switched back to Gnome. Curiosity is killing me, though, and I would like to know what caused this and if there are any ways to fix it as I really like Kubuntu's effects.

---

### Post by LoloftheRings on 2009-11-13
Really strange, what you see is basically one program, running on the graphical server (X.org).
The program is xterm. You can run this by running startx from a tty. KDE is not running at all. From the terminal window you get, you could run 'startkde' to run KDE. This is of course not what you want. Maybe you have to select KDE from the login manager. I guess it's default was "Run .Xclients script". Are you using GDM or KDM?

If it's set to KDE, you might wanna change it to run .Xclient script and edit (create it if it doesn't exist) the /home/yourname/.Xclients and add this line to it:

```

startkde

```

Hope this will fix it

---

### Post by Butterknife on 2009-11-13
Thanks for the reply. I'm running GDM at the moment as default (Gnome, right? I'm a newbie), installed KDE through apt-get. I would try running "startkde" but when I log in to KDE, the terminal that open doesn't recognize me typing and is almost totally unresponsive. I will try switching to KDE again and selecting it from the login manager if that's the problem. If not, can you tell me step-by-step how to run .Xclient script and edit it? As I said, I'm new, can use most of basic things but am not so good when it comes to command lines.

---

### Post by LoloftheRings on 2009-11-14
You first need to move your mouse over the terminal window to make it gain focus. 

Editing the .Xclients script is not hard at all. Open up the text editor gedit (applications -> accesoires -> text editor) and enter the following:

```

startkde

```

press the save button, save it as .Xclients (don't make typo's here) in your home directory.

If you wanna do it quicker, enter two commands at the terminal:

```

rm .Xclients #to make sure any old .Xclients script won't be bothering you, this command will probably tell you the file doesn't exist.
echo startkde >> .Xclients #to quickly write the line startkde to the .Xclients file

```

Now logout and select run .Xclients script from the dropdown menu.

---


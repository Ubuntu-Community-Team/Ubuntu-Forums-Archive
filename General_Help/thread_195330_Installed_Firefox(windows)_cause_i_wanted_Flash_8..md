---
title: "Installed Firefox(windows) cause i wanted Flash 8...need help"
date: 2006-06-12
forum: General Help
---

### Post by konacoffeeguy on 2006-06-12
Ok so I installed it with WINE but the problem is, how in the world do I open FireFox(windows ed) there is no icon or anything to click on. Im a little confused? .... Help>>>??? 

 Thanks to anyone that does , 

 Konacoffeeguy

---

### Post by amunimanghi on 2006-06-12
maybe type ```
firefox
``` in the terminal. the terminal is located under applications => accesories =>Terminal. It also could be under Applications => Windows Applications. Windows applications should be there. If not, use alacarte to check it in.

---

### Post by Mr_Congeniality on 2006-06-12
Shouldn't og Flash Player 8.5 with linux support been released like ages ago?

---

### Post by kingsidy on 2006-06-12
i got flash working in firefox linux. you just need to install gsfonts and gsfonts x11. then point to /usr/lib/firefox during macromedia flash player install

---

### Post by blackjack6.21.91 on 2006-06-12
What you download with wine should be located in ~/.wine.
To access this file, you can go to your home folder and, if you don't see hidden files by default, press <Control><H> to locate a folder called .wine.  Click on that, and then on a folder called Drive C (if this doesn't exist, you probably havent configured WINE yet, go [here]("http://ubuntuforums.org/showthread.php?t=149585")). Now you should see a folder for Program Files.  Click that.  There should be a firefox folder (if not, you don't have firefox).  Go inside that and there should be a firefox icon that opens with WINE automatically!

---

### Post by konacoffeeguy on 2006-06-12
[QUOTE=kingsidy]i got flash working in firefox linux. you just need to install gsfonts and gsfonts x11. then point to /usr/lib/firefox during macromedia flash player install[/QUOTE]

So what you are saying is that I don't need to install the windows version of FireFox to veiw Flash 8 websites??? If this is the case, how can I do this? Or where can I find a place to do this? I know you just told me... kind of but what did you just say lol sorry for being such a noobie about this but when in Rome do as the Romans. Thanks, 

 Konacoffeeguy

---

### Post by DoktorSeven on 2006-06-12
Flash for Linux Firefox is version 7.  Since some sites need v8, and Linux Flash doesn't go up that high, some other method is needed, and the easiest way is to run Firefox (Windows version) in Wine and install Flash 8 (Windows) under it.

This is not about running the Linux Firefox, nor its associated Flash plugin.  You **do** currently need a solution such as this to run Flash 8; native Flash won't do it.

Firefox for Windows is installed in ~/.wine/drive_c/Program\ Files/Mozilla\ Firefox/ by default as "firefox.exe".  The easiest way to run it is to create a shortcut on the desktop or in your launcher menu that runs:

**wine /home/*your username*/.wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe**

substituting your username for *your username*. of course.

---


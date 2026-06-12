---
title: "Need info on finding a terminal program"
date: 2011-04-27
forum: General Help
---

### Post by scampbell70 on 2011-04-27
I tried Mint for a few days and one thing I really liked was that the terminal had witty little quotes when I opened it. I am wondering how this is done, is there different terminals that you can download that include such things or is that an add on that you can download to add to any terminal.


Thanks for the help in advance

---

### Post by VCoolio on 2011-04-27
It's not the terminal app, you can do that in any terminal. Put a command that produces a quote at the end of the file ~/.bashrc and voila. Like explained [here](http://enli.co.cc/customization/spice-up-ubuntulinux-terminal-with-quotes-motd-each-time-it-is-started-using-cowsay-and-fortune/), only where it says "sudo gedit /etc/bash.bashrc" you can just do "gedit ~/.bashrc" as well, no need for root permissions. You need to do gksudo with graphical apps like gedit anyway.
Explanation: the point is, your terminal app runs bash when it starts. Bash does everything that /etc/bash.bashrc and ~/.bashrc tells it to do, like how the prompt looks like and load aliases and stuff. If you add a command in ~/.bashrc, at the end, it will be executed every time bash is started, like when a terminal is opened. Run "bash" inside a terminal and you'll have the quote again.

---

### Post by scampbell70 on 2011-04-27
thanks I will look it up and let you know how it goes.

---

### Post by rubylaser on 2011-04-27
I believe Mint just uses fortune and cowsay to do the funny quips. You can set it up like this...
```
sudo apt-get install fortune cowsay
```

Then edit your .bashrc like this
```
sudo nano /etc/bash.bashrc
```

And paste this at the bottom
```
fortune | cowsay -n
echo
```

Hope that helps.

Edit: I Should have read above post, covers exactly what I said :)

---

### Post by scampbell70 on 2011-04-29
Thank you both that is exactly what I was looking for and it works awesome.

---


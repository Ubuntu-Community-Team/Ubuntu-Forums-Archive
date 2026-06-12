---
title: "I can not login to my ubuntu , please do help me"
date: 2010-12-28
forum: General Help
---

### Post by maizuddin35 on 2010-12-28
Hello guys, 

again, I think I messed something up with the nautilus, I want to remove nautilus via synaptic , I'm not sure what do I did wrong but , before the process removing the nautilus is over, suddenly it restarted and I at my login screen.
When I want to login , I can't , I will be back at the login screen, what I can see is, there is no ubuntu user session below. I can't choose a thing. I can't go into my ubuntu desktop.

Now I'm running with my external hdd ubuntu or windows. please help . thanks in advance

---

### Post by Verbeck on 2010-12-28
login to the xterm session and enter *sudo apt-get install ubuntu-desktop*
it should give back the gnome session

---

### Post by maizuddin35 on 2010-12-28
I should have an internet connection if its like that , right?.
right now, I use my college wifi connection and it needed a user login, if I can connect to internet without the browser, that would be easy.

---

### Post by maizuddin35 on 2010-12-28
xterm, is via the user session also right . The thing is, there is NOTHING inside the user session option. Nothing to choose

---

### Post by Verbeck on 2010-12-28
then could you try it from tty1 (ctrl+alt+F1)

---

### Post by Bucky Ball on 2010-12-28
If you can get to a cursor in busybox or tty try:

```
startx
```

---

### Post by gradysghost on 2010-12-28
To answer your other question, yes, you should have an Internet connection if you connect via a network cable.  If you're wireless, you may have some problems.

---

### Post by maizuddin35 on 2010-12-28
Ok I'll try with tty1 , but if I want to sudo apt-get install ubuntu-desktop , I should have internet connection to run that. Now, the problem is, I need to gain access to my college wifi login screen to gain access to the internet. If I'm not mistaken there is a way that I can browse internet via command line/terminal isn't . but how?

---

### Post by maizuddin35 on 2010-12-28
@BuckyBall, where I should run that **startx **?

---

### Post by thomasyen on 2010-12-28
@maizuddin35: type it at a command prompt like tty1

If you happen to have a browser that doesn't rely on X (for example elinks), then you could try authenticating your connection. Hope this helps.

(Since you say you can see the login screen, I suspect that the problem lies not in X but in the configuration files for GDM.)

---

### Post by maizuddin35 on 2010-12-28
@thomasye, tq for letting me know about that, let me try with this one.

---

### Post by Bucky Ball on 2010-12-28
> **thomasyen said:**
> @maizuddin35: type it at a command prompt like tty1



That's right. If you boot and it drops you to a command shell and you are root, type 'startx' there. If you are not root but your user name, type:

```
sudo startx
```If you can boot the recovery kernel and get to recovery options, choose 'Drop to root shell' (or whatever it is) and type it there.

If this works (and if you have it installed) this will take you to a desktop where you can get your ethernet up and have a bit more control solving your issues.

---

### Post by maizuddin35 on 2010-12-28
hey guys, 

I'd tried sudo apt-get install ubuntu-desktop and it failed because I don't have any internet connection.I just can't connect to the internet .

and I also triied startx and sudo startx , and there is nothing happen. some word come out, thats all.

Thank you for all the help , but for now, is there any chance that I can install ubuntu-desktop via live cd?

---

### Post by thomasyen on 2010-12-30
Maybe you could boot from CD and use the included Firefox to authenticate? Best of luck to you on restoring your system!

---

### Post by WthIteh on 2010-12-30
> **thomasyen said:**
> Maybe you could boot from CD and use the included Firefox to authenticate? Best of luck to you on restoring your system!
For repairing from a LiveCD you could
 - boot from LiveCD
 - open a terminal
 - considering that your root partition is mounted at /media/XXXX
     - you could mount it by clicking on your hard disk icon if it is not currently
 - chroot /media/XXXX     in the terminal
 - since now every command will be executed on your installation (not on live system).
 - aptitude clean && aptitude update && aptitude upgrade && aptitude install ubuntu-desktop

---

### Post by Bucky Ball on 2011-01-01
It may not be clear that the last line of [WthIteh]("http://ubuntuforums.org/member.php?u=1210927")'s post is a command you should type into the terminal:

 ```
aptitude clean && aptitude update && aptitude upgrade && aptitude install ubuntu-desktop
```

---

### Post by maizuddin35 on 2011-01-02
thanks to everyone who helped me with my problem . Now, my problem is solved. I make a new thread , and here it is [http://ubuntuforums.org/showthread.php?t=1656431](http://ubuntuforums.org/showthread.php?t=1656431)

---


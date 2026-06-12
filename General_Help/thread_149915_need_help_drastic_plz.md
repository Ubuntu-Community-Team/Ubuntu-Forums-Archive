---
title: "need help drastic plz"
date: 2006-03-24
forum: General Help
---

### Post by LORD_PoLvO on 2006-03-24
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)
on this i am up to step 10 and i am stuck i have had to log of my ubuntu and into xp so i can post this firstly can i continue straight fropm step 10 or do i have to go again also the file is located on my desktop but i dont know the "directory" can someone please tell me becasue i want this to work for me

---

### Post by Mustard on 2006-03-24
You've posted this in two sections of the forum, which one am I supposed to answer in?

Secondly what are you stuck with?  Getting to the directory from command line?

```
cd ~/Desktop
```

or

```
cd /home/your_user_name/Desktop
```

---

### Post by Zeroangel on 2006-03-24
the ~ is just shorthand for /home/yourusername/

The desktop's location on the hard drive is /home/yourusername/Desktop ( also known as ~/Desktop )

---

### Post by LORD_PoLvO on 2006-03-24
if i load up ubuntu i can go straight from step 10 ? also ty for your help sorry for being a pian i posted in 2 sections coz no 1 replied to the other 1 sorry ](*,) neway ty ima go try and finish it off its hard becasue in the non gui command line i cant read the instructions lol

---

### Post by Mustard on 2006-03-24
[QUOTE=LORD_PoLvO]if i load up ubuntu i can go straight from step 10 ? also ty for your help sorry for being a pian i posted in 2 sections coz no 1 replied to the other 1 sorry ](*,) neway ty ima go try and finish it off its hard becasue in the non gui command line i cant read the instructions lol[/QUOTE]

It might be possible for you to use a command line web browser if your internet connection is working from ubuntu.  I can explain how to install if you like.

---

### Post by LORD_PoLvO on 2006-03-25
internet works from ubuntu but not for long and not all the time

---

### Post by Mustard on 2006-03-25
[QUOTE=LORD_PoLvO]internet works from ubuntu but not for long and not all the time[/QUOTE]

Well I just ran this command which shows some browsers that are available...

```
mustard@slave:~$ apt-cache search links | grep browser
elinks-lite - advanced text-mode WWW browser (lite version)
links - Character mode WWW browser
links2 - Web browser running in both graphics and text mode
man2html - turns a web-browser and an httpd-server into a man pager
tkman - A graphical, hypertext manual page and Texinfo browser
elinks - advanced text-mode WWW browser
mustard@slave:~$

```

To install say, links, you would type..

```
sudo apt-get install links
```

I would imagine the command to execute it is something like..

```
links http://www.ubuntuforums.org
```

Clicking on the top line of the browser should reveal a menu.

As long as your internet connection holds up, you should be able to browse to the web page you need and read the instructions from the command line.  You can have several terminals running using the ctrl + alt + f1 to f6 keys.  You can switch from one to the other so that you can have the browser running in say, ctrl + alt + f2, while you do the actual commands in ctrl + alt + f1.  Good luck with it. :)

---


---
title: "Accessing &quot;System Settings&quot; using Terminal"
date: 2011-06-14
forum: General Help
---

### Post by JuR-97 on 2011-06-14
Hello,

I have been wondering how I can access System Settings using Terminal? I would like to hear this because I can not see the bar on the top with log in, log out, shutdown, clock, calendar, evolution mail and other things. So the terminal is maybe my only way to access them. Why? Because I'm having Ubuntu on my laptop, and there are really really heavy theme and graphic settings set on, and my computer lag lags and lags and buggy bugs :icon_frown: when there comes a pop up, i change window etc.

Can you please help me with this matter?

--
Sincerely
JuR

PS: When I got private message on this forum, pop up shown up and my laptop crashed. That is annoying.

---

### Post by jerrrys on 2011-06-14
are you running ubuntu 11.04?

---

### Post by JuR-97 on 2011-06-15
> **jerrrys said:**
> are you running ubuntu 11.04?

Yes I'm

---

### Post by jerrrys on 2011-06-15
do you have the necessary system resources?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

if you want to run from terminal, you can.  but why bother loading a GUI if your not going to be able to use it.

---

### Post by JuR-97 on 2011-06-15
> **jerrrys said:**
> do you have the necessary system resources?

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

if you want to run from terminal, you can.  but why bother loading a GUI if your not going to be able to use it.

Yea, many times better. 
The first time I started up Ubuntu, all the bars were in their places and everything was ok. Then I restarted it... And, there is no menus, no bars. Only way to access files is via browser, and when i did that i searched for terminal and now i have the shortcut to terminal on my desktop.

---

### Post by jerrrys on 2011-06-15
your new to Ubuntu and 11.04 is a work in progress.  If you want something that you can just use for now, I would suggest trying 10.10.  

to answer your question.  there are probably 1000'S of commands.  a place to start

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=terminal+cli+commands&as_qdr=all&sa=Google+Search&lang=en#1185](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=terminal+cli+commands&as_qdr=all&sa=Google+Search&lang=en#1185)

---

### Post by JuR-97 on 2011-06-15
> **jerrrys said:**
> your new to Ubuntu and 11.04 is a work in progress.  If you want something that you can just use for now, I would suggest trying 10.10.  

to answer your question.  there are probably 1000'S of commands.  a place to start

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=terminal+cli+commands&as_qdr=all&sa=Google+Search&lang=en#1185](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=terminal+cli+commands&as_qdr=all&sa=Google+Search&lang=en#1185)

Yea, thanks for this, but is there command to open the settings via terminal?

i recently typed: "sudo apt-get install system-settings" but it told me download it from the internet. I just thought is this really the real "System Settings"..? I don't think so.

---

### Post by jerrrys on 2011-06-15
i do not know of one command for all system settings.  like i said; there are 1000's.  example, to reset/ restore desktop

[http://ubuntuforums.org/showthread.php?t=1702203](http://ubuntuforums.org/showthread.php?t=1702203)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=restore+natty+11.04+desktop+terminal+cli&sa=Search&cof=FORID:9#1485](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=restore+natty+11.04+desktop+terminal+cli&sa=Search&cof=FORID:9#1485)

---

### Post by heyandy889 on 2011-07-08
The question is, how to run the application named "System Settings" from the terminal? I am also looking for the answer to this question. I think that jerrrys is assuming the OP wants to change a bunch of system settings. In reality, there is an Ubuntu application named "System Settings," and that is the application in question.

edit: Bang. Found the answer.

```
gnome-control-center
```

---


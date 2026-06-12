---
title: "Random Logging Out"
date: 2012-02-29
forum: General Help
---

### Post by JosephBeck on 2012-02-29
The problem is Ubuntu 11.10 will randomly log me off. I had the problem before where it was so bad that I had to switch to only using Gnome Shell to do things vs. Unity 3D and 2D. I changed to Linux Mint 12, was ehh cause I liked Mint 11 better. In the end I wanted to see if I could get Ubuntu 11.10 to work so I just reinstalled it and removed Mint. It was running nice for a little while but now the log off problem is back. I think it is related to flash because it only does it when a site uses certain flash such as opening a youtube video, tumblr, flash games, etc. I haven't changed anything so I dont see why it is doing it now when it wasn't doing it days ago. It is a little obnoxious to have to keep logging in because it has a hissy fit. 

Any solutions would be great. If anyone needs any of my Terminal output just ask and tell me what you want me to put into the terminal. I am fairly familiar as I've been using Ubuntu a few months now but not entirely perfect with all the specific Terminal commands. 

I use the most up to date Google Chrome as far as a browser, the linux version of course. Also this is not just a Unity problem because it does it in Gnome as well, just not as often.

---

### Post by JosephBeck on 2012-02-29
Bump Since This Got Quickly Buried x-x.

---

### Post by imachavel on 2012-02-29
> **JosephBeck said:**
> The problem is Ubuntu 11.10 will randomly log me off. I had the problem before where it was so bad that I had to switch to only using Gnome Shell to do things vs. Unity 3D and 2D. I changed to Linux Mint 12, was ehh cause I liked Mint 11 better. In the end I wanted to see if I could get Ubuntu 11.10 to work so I just reinstalled it and removed Mint. It was running nice for a little while but now the log off problem is back. I think it is related to flash because it only does it when a site uses certain flash such as opening a youtube video, tumblr, flash games, etc. I haven't changed anything so I dont see why it is doing it now when it wasn't doing it days ago. It is a little obnoxious to have to keep logging in because it has a hissy fit. 

Any solutions would be great. If anyone needs any of my Terminal output just ask and tell me what you want me to put into the terminal. I am fairly familiar as I've been using Ubuntu a few months now but not entirely perfect with all the specific Terminal commands. 

I use the most up to date Google Chrome as far as a browser, the linux version of course. Also this is not just a Unity problem because it does it in Gnome as well, just not as often.

Flash is java code used to assist graphics library API sitting on top of compiled c. It helps mostly browser pages load streaming video formats. It does almost nothing else, I've never heard of flash effecting he GUI, in fact the GUI I believe uses OpenGL graphic library API. What exactly is the issue you are having? Switching an interface won't really address the issue. Also I like Linux mint and ubuntu also.

I don't know the issue, as you didn't give full details. I hope you reinstalled correctly, would like to know the size of your swap partitions and what not. Don't remember the command to view your partition table. If you open up boot repair you can create a boot script. Then upload it as an attachment in your post. However I'm guessing this has nothing to do with the issue, and that your issue is related to a configuration issue

---

### Post by JosephBeck on 2012-02-29
> **imachavel said:**
> Flash is java code used to assist graphics library API sitting on top of compiled c. It helps mostly browser pages load streaming video formats. It does almost nothing else, I've never heard of flash effecting he GUI, in fact the GUI I believe uses OpenGL graphic library API. What exactly is the issue you are having? Switching an interface won't really address the issue. Also I like Linux mint and ubuntu also.

I don't know the issue, as you didn't give full details. I hope you reinstalled correctly, would like to know the size of your swap partitions and what not. Don't remember the command to view your partition table. If you open up boot repair you can create a boot script. Then upload it as an attachment in your post. However I'm guessing this has nothing to do with the issue, and that your issue is related to a configuration issue

I don't think I can be any more clear. It is logging me off, aka., Ubuntu is blacking out and going to the log in screen. It does it whenever I access a Java / Flash heavy website. And it did address the issue as I said. Gnome was not as effected as Unity. I have Ubuntu as the only thing on my Computer with access to all 160gigs, as this is a netbook. It was installed correctly each time. As I said, it worked perfectly and has randomly just started acting up again. If it was installed wrong, it would do it since I installed it, not act up at random later down the road.

---

### Post by syrex314 on 2012-02-29
Sounds like Xorg is crashing. Anything fishy in /var/log/Xorg.0.log ?

---

### Post by imachavel on 2012-02-29
Yes indeed sorry if you made a previous thread about this. So java code is messing up gnome interface, or at least flash code, you may need to dig around some folders and find some code files for gnome, I think it's called gtk? Me and mg&tl did a practice gtk file one day, no idea how the java sits on top of the compiled c code. Come to think about It, I talk a lot of crap. I said GUI is a graphics API library?? No it's wrong. The graphics API library helps load pictures, images, and may assist the GUI to load code bits into the gpu. But the GUI itself the interface which works with the back end compiled code is written in c or c++ with classes. So the java library that works with gnome guincould be corrupt. Or flash library wherever it's stored, or both. Probably both. Since one thing causes the entire gnome interface to fail. I'd go digging around and look for malformed lines of code, but I wouldn't know where to tell you to start looking. Any updates, upgrades helped??

Sudo apt-get install update
Sudo apt-get install upgrade

Did you also say this error has occurred after a fresh reinstall?? Weird. Maybe it's driver related? But that makes no sense, gnome is just the interface. Like I said, something linking whatever helps video library API code, run on top of java, which is what flash is written in, which sits on top of compiled c, is messing up. I'm not sure where the interface comes in, that is so strange, the interface just allows the user to interact with the file system. Why gnome and not unity??? I think I've got it, different plug ins. Definitely, perhaps gnome does not like flash. But I haven't heard that before, is there a way you can uninstall flash, and use something else??

Best of luck, I'll be checking the thread for an answer. Btw, how are your video decodes looking? Please type:

Lspci - v and list return syntax

Also type in

Is it show ffmpeg? I'm not sure

Try:

-vcodec codec, I just don't remember. Have you installed vlc media player? This is usually a good way to install up to date codecs, and once installed, updates should update your video decoders

---

### Post by imachavel on 2012-02-29
> **syrex314 said:**
> Sounds like Xorg is crashing. Anything fishy in /var/log/Xorg.0.log ?

Yes upload the logs a an attachment

---

### Post by JosephBeck on 2012-03-01
Ill attach both the xorg and lscpi-v outputs in this post.  It did it badly before while updating and what not wouldn't fix it. Its happened again but just once since the fresh install. I am hoping it doesn't get out of control again. I do have VLC.

---

### Post by JosephBeck on 2012-03-05
Ok this is seriously becoming a problem again. It has logged me out three times in a row in the last 5 minutes. Can ANYONE help me fix this issue which I am 95% sure is tied to flash.

---

### Post by matt_symes on 2012-03-05
Hi

> Sounds like Xorg is crashing. Anything fishy in /var/log/Xorg.0.log ?

I would place money on that.

Try disabling or uninstall flash. Does it still crash ?

You can manage your plugins in chromium by typing

```
about:plugins
```

into the navigation bar. From there you can disable flash for a while, while trouble shooting.

What version of flash are you using and how did you install it ?

There is nothing in that log file you posted that i could see.

Is there anything in ~/.xsession-errors in your home directory ?

Anything in /var/log/syslog ?

Kind regards

---

### Post by JosephBeck on 2012-03-05
> **matt_symes said:**
> Hi



I would place money on that.

Try disabling or uninstall flash. Does it still crash ?

You can manage your plugins in chromium by typing

```
about:plugins
```

into the navigation bar. From there you can disable flash for a while, while trouble shooting.

What version of flash are you using and how did you install it ?

There is nothing in that log file you posted that i could see.

Is there anything in ~/.xsession-errors in your home directory ?

Anything in /var/log/syslog ?

Kind regards


I use Google Chrome so Flash is automatically installed, it is 11.1 r102. I just disabled it so we shall see if it helps any. Ill upload the .xsession-errors since I am not familiar with that sort of thing as well as the syslog for you.

Syslog was too big for the forum so I used an alternative site to upload:

[https://rapidshare.com/#!download|431tl|3870235435|syslog.doc|543|R~0|0|0|RapidPro](https://rapidshare.com/#!download|431tl|3870235435|syslog.doc|543|R~0|0|0|RapidPro) expired. (34fa3175) select the middle option to save to your computer.

---

### Post by matt_symes on 2012-03-05
Hi

You are using gnome shell and not Unity ?

Kind regards

---

### Post by JosephBeck on 2012-03-06
> **matt_symes said:**
> Hi

You are using gnome shell and not Unity ?

Kind regards


I use both. I use gnome shell when it keeps logging me out. The problem happens in both but it is far worse in Unity.

---

### Post by davidvandoren on 2012-03-07
What's your cpu?

If you have an I3 OR I5 go into the bios and disable multi threading.

Allow only one thread per core and see if it helps.

---

### Post by JosephBeck on 2012-03-07
> **davidvandoren said:**
> What's your cpu?

If you have an I3 OR I5 go into the bios and disable multi threading.

Allow only one thread per core and see if it helps.

Mines just a netbook, its an Intel Atom, HP 210 mini >_>... Would I still be able to do it from the starting bios screen?

---


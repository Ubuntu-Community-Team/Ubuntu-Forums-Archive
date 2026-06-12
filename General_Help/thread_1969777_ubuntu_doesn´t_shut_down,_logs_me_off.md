---
title: "ubuntu doesn´t shut down, logs me off"
date: 2012-04-30
forum: General Help
---

### Post by Salvagluque on 2012-04-30
Hello guys,

Since  I installed ubuntu 11.10 and nnow with ubuntu 12.04, I have this bothering situation. When I shut down the system I´m taken to the user selection screen where I try again to shut down from but with similiar results any idea what can be looping me into this screen?

thanks.

---

### Post by uylug on 2012-04-30
Do you have OpenSSH Server installed? If there is anyone else using the system, it won't shut down.

---

### Post by Salvagluque on 2012-04-30
nop, and it happens every single time i shut it down.

---

### Post by Salvagluque on 2012-05-05
Something else I noticed about it is that the ubuntu 11.10 loading comes in qhen I start the machine. But this situation started when I had ubuntu 11.10 so I hink there has to be an unconsitency in the system which was carried into this one. any idea how can I wipe out all the old stuff from the previous version?

Thanks

---

### Post by Favux on 2012-05-05
Sounds like Shutdown... is somehow acting like Log Out...  Got cross-linked somehow?

When you chose Shutdown what happens when you use Restart?  The same thing?

---

### Post by Salvagluque on 2012-05-05
You got it. That´s exactly what happens. If I choose restart does the same. It doesn´t matter if I´m in the log in screen, it doesn´t shut down nor restarts.

---

### Post by Favux on 2012-05-05
It beats me what could be cross-linked.

If an ***[fschk]("http://linux.die.net/man/8/fsck")*** doesn't fix the problem.  I don't know what to look at.

Could be a corrupted install.  Reinstall?

---

### Post by Salvagluque on 2012-05-09
I tried fschk but it says it will damage my sytem. so I think I´ll have to try a reinstall later.


Thanks

---

### Post by Salvagluque on 2012-05-10
I found that also some apps don't start now but they used to in 11.10. I tried to run the same app several tiems from the ubuntu menu but nothing.
Then I opened a terminal and worte the name of the application and only then it kinda tried to start but I ended up with a blank window.

The terminal was root by the way.

---

### Post by Favux on 2012-05-10
You shouldn't open applications as root.  That can mess up permissions.  They can store data and config files and what not in /home/username and you don't necessarily want those permissions changed to root.

For example you only open nautilus as root if you want to manipulate some system files 'gksudo nautilus', because the system files are root.  But you want to shut it down as soon as you finish because you don't want to accidently change permissions in your /home/username directory for example.  Same thing with 'gksudo gedit'.  And you want to use the graphical root 'gksudo' for gui programs instead of 'sudo' because just 'sudo' can mess up gui programs.

---

### Post by Shadius on 2012-05-10
Hmmm...I can't understand why **fschk** would say it'll damage your machine. Isn't **fschk** supposed to fix file system errors? :confused:

---

### Post by Salvagluque on 2012-05-10
Favux: It was more of a "desperated move" since the application didn´t open in any other way. errr... I didn´t use sudo nor gksudo to open it, I just simply wrote down "gwaei" (the apps name) and ran it. I think that´s not as hazardous as the ways you mention. Thanks for telling me that, I didn´t believe that could happen.

Shadius:** Yeah, isn´t that  weird?!?**  But that´s in fact what the message said: If you run **fschk** your system **will** be damaged, that doesn´t bring a shade of hope or anything, just no option. Maybe it was because I only wrote fschk in the terminal and I didn´t add -f or any other specification, but still it shouldn´t come up with a message like that when the app is supposed to do the opposite.

Well, I think I´ll see if there is an fschk option that doesn´t **destroy** my computer. hahaha

---

### Post by Favux on 2012-05-10
Hi Salvagluque,

It sounds like you were trying to run fschk on a mounted drive.  It should be unmounted.

---

### Post by Salvagluque on 2012-05-10
Well, yeah. It´s actually the same in which I have ubuntu installed. Well, I think that´s the reason why it would damaged my system. I guess if I want to check this drive then I have to use another ubuntu installed in another drive or maybe through the installation disk,right?

---

### Post by Favux on 2012-05-10
Right, you can use a live CD or whatever.

---

### Post by Salvagluque on 2012-05-18
well, I rebooted the whole system and... that was it! obviously there was some crossed wire somewhere which could be solved with an fschck (if I did it the right way) but even is a pain in the rear, I decided it was best to start fresh.

So thanks to everybody for the comments I'll keep in mind the fschck if there's an ocasion where i have to check the system up again.

By the way, I stumbled upon this weird solution on how to solve the detection of 2 screens desktop.
[http://ubuntuforums.org/showthread.php?t=1982598](http://ubuntuforums.org/showthread.php?t=1982598)

See ya.

---


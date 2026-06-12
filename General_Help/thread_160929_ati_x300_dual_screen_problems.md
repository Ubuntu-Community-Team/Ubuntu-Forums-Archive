---
title: "ati x300 dual screen problems"
date: 2006-04-15
forum: General Help
---

### Post by gtfan1 on 2006-04-15
i have an ati x300, and want to get my dual screen setup to work again.  i am at a complete loss of what to do

---

### Post by gerbman on 2006-04-16
[QUOTE=gtfan1]i have an ati x300, and want to get my dual screen setup to work again.  i am at a complete loss of what to do[/QUOTE]Hey there. It's totally possible...I think. I have an x600 on my Dell laptop and got dual screen working by running the following:```
sudo fglrxconfig
```This will create a new xorg.conf file for you in /etc/X11. It should back up your current one, but you might want to back it up yourself just to make sure. Run through the configuration program, and then hit CTRL+ALT+BACKSPACE to restart X. If it won't initialize correctly, don't worry. Just copy the original xorg.conf file back to /etc/X11/xorg.conf and restart again.

Hope that gets you started.

PS - I'm assuming you already installed the drivers for your ATI card. If you haven't, go [here]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide").

---

### Post by gtfan1 on 2006-04-16
thanks for the help, but i have no clue how to enter any of the stuff you suggested into linux, i'm a complete begineeri

---

### Post by gerbman on 2006-04-16
Not a problem. What you need to do is open up a terminal window by going to Applications->Accessories->Terminal. That is where nearly all commands you encounter in posts/tutorials/how-to on this forum need to be entered. So, first you need to install the drivers for your ATI x300 card - I link to the guide in my above post. Follow "Method 1" under the Breezy installation. Where does that get you?

---

### Post by gtfan1 on 2006-04-16
i followed the instructions as best as i could, but i am still not able to use dual monitors

---

### Post by gerbman on 2006-04-16
[QUOTE=gtfan1]i followed the instructions as best as i could, but i am still not able to use dual monitors[/QUOTE]Where are you stuck? It always helps to post any error messages you get or commands that don't seem to work.

---

### Post by gtfan1 on 2006-04-16
ok, i tried what the first description said to do, i had some problems doing it.  after i did it i restarted my comp and linux would not start up because the video driver was set up badly, so i reinstalled linux again.  

i'm having alot of problems just understanding what the commands are telling me to do.

---

### Post by gerbman on 2006-04-16
[QUOTE=gtfan1]ok, i tried what the first description said to do, i had some problems doing it.  after i did it i restarted my comp and linux would not start up because the video driver was set up badly, so i reinstalled linux again.  

i'm having alot of problems just understanding what the commands are telling me to do.[/QUOTE]List the commands you're having problems with and I'll explain them.

---


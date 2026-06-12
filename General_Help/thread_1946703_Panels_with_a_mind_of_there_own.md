---
title: "Panels with a mind of there own"
date: 2012-03-25
forum: General Help
---

### Post by Agent26 on 2012-03-25
Hi there all, im running Xubuntu 10.4.2 and its a great OS, Ive been using it for ages but on every system it's always eventually does the same thing to me. My upper and lower panel keep disapearing on there own and for no reason?

Why. If they just stayed Id be 100% happy.
I can get them to re appear by typing xfce4-panel & but when I close my terminal they go again.
 Does anyone know a way to get them to reset themselves back to default and then lock the things down permenently.
Thank you.
p.s I hope a creator of the OS sees this as I can say this has been a regular phenomena on 3 different machines. The reason I love this version so much is because when these panels stay they are my favorite part, 2 panels are better than Windows one and they are more customisable too.

Also On my older satellite laptop I used the same disc to install but for some reason at start up there is some bad crash pixels, it seems to have a message behind a crash that is not showing on any other machine?
Strange.

---

### Post by dino99 on 2012-03-25
might be time for some cleaning:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

sudo dpkg-reconfigure -phigh -a
(be patient, it can take a while, dont stop it)

---

### Post by Agent26 on 2012-03-25
Hi, Thanks Dino I will give those a try.
A little spring cleaning  coming up.

---

### Post by Agent26 on 2012-03-25
OK thats me spring cleaned but still my panels are up the creek.I can open the panel manager and put them back but they don't work properly now. All the new buttons go left instead of right and the tabs I rest there just vanish.

Perhaps they might change themselves back.

I really need a way to reset to default with them....

About the crash screen on the other machine...It reminds me of the speccy days when basic codies would crack games and then leave messages to each other....cracked by the Agent ect...

I wonder if it's posible my copy is a bit dodgy?????

---

### Post by LewisTM on 2012-03-26
To reset the panel configuration:
1. Logout. At the graphical login prompt, press Ctrl-Alt-F1 to enter a virtual login screen. Log in.
2. Delete the panel configuration file:
```
rm ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml

```
3. Press Ctrl-Alt-F7 and log back into Xubuntu. The panels should be reset to default settings.

It's possible that the config of one of your panel items is giving you trouble. More clues can be found in ~/.xsession-errors
The config files for these can be reset the same way by deleting the corresponding .rc file in ~/.config/xfce4/panel

If you want to lock down config files so nothing can ever harm them, use this command:
```
sudo chattr +i <config file> # to lock
sudo chattr -i <config file> # to unlock
``` 

Hope this gets you back in control :)

Cheers!

---

### Post by Agent26 on 2012-03-26
Thank you Lewis, I am going to do that now and will comeback to hopefully make this thread solved. Thank you for the lock down codes.
I don't think my copy is dodgy but better safe then sorry.

After thinking about the crash type message, perhaps it's just the older screen playing up. When you think of it thats a 10 year old laptop and i am running software from 2010 on it, also I used the same disc for my main desk top and there is no crash message there. 
Xubuntu, my personal favorite of the Linux systems.

---

### Post by Agent26 on 2012-03-26
OK Ive tried that now and it has revealed a problem...it says there is no such directory.

---

### Post by LewisTM on 2012-03-26
You might be running an older version of Xfce since you're on Xubuntu 10.04. Execute [FONT="Courier New"]locate xfce4-panel.xml[/FONT] and hopefully you'll find the file elsewhere.

---

### Post by Agent26 on 2012-03-27
Found it, my panels are now reset, back and working fine. Thats some more handy stuff learned, Thank you.

If they go haywire again, there are several ways I can get them now.
Im also building up a lots of other useful codes writing them down so when I get a prob I can just refer to my paper.

      "Thank you"

---


---
title: "No gui after closing/opening laptop"
date: 2012-09-03
forum: General Help
---

### Post by jmtoporek on 2012-09-03
I recently installed ubuntu 12.04 via Wubi on an Compaq laptop with Vista. It works fine for the most part except for one thing - when I boot up to Ubuntu and close/reopen the laptop the screen is frozen. It shows nothing but static and the cursor.

I'd like to fix this, but even if there was a shortcut way to get the GUI back (icons for applications) with some sort of shortcut that would be a big improvement. If I click control-altf1 I get the command line, and if I click control-alt-f7 I get the frozen static screen. What can I do to fix this?

---

### Post by Basher101 on 2012-09-03
Looks like X server does not wake from stand by properly. With the current information you have given, you can only reboot to fix this. Log into your account using the ctrl+alt+F1 console.Enter your username and password. Afterwards type ```
sudo reboot
``` and enter your password again and hit enter to reboot.

if you add more information, such as your hardware, people might help you out more efficiently

peace

---

### Post by Crossbow on 2012-09-03
I had this problem after updating Nvidia drivers.

From: [http://ubuntuforums.org/showpost.php?p=12203435&postcount=16](http://ubuntuforums.org/showpost.php?p=12203435&postcount=16)

> sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current

Then just ctrl-alt-delete to reboot.

---

### Post by jmtoporek on 2012-09-03
I found another post where I tried a solution and for the time being it worked - 

[http://ubuntuforums.org/showthread.php?t=1760565&highlight=frozen+screen+closing+laptop]("http://ubuntuforums.org/showthread.php?t=1760565&highlight=frozen+screen+closing+laptop")

here was what I did that worked - 

*"I'm having a similar problem. You can restart Xorg by going to your System Settings->Keyboard->Layouts->Options->Key Sequence to Kill the X Server and place a check next to ctrl+alt+backspace. Next time it locks up, just press that key combination and log back in. (Something I always enable after an install)"*

I will give the other stuff a shot. For the record a I have pretty cheap laptop and I am running a machines with a Nvidia graphics card. It is a Compaq Presario F700 with an AMD Turion64 x2 chip.

Thanks so much for your response, I really appreciate both of you posting and will give your ideas a try, and will post if these things do the trick.

---


---
title: "how to disable compiz without running ubuntu?"
date: 2009-11-17
forum: General Help
---

### Post by Haribda on 2009-11-17
I have a very serios problem with compiz that freezes my 9.10 ubuntu as soon as it boots up and I see the desktop...

How can I disable it from recovery mode, live cd or something like that? Any ideas please?

---

### Post by lykwydchykyn on 2009-11-17
- Boot to the login screen.

 - Hit  ctrl-alt-f2 to get to a virtual terminal

 - log in to the terminal

 - execute: 
```

sudo aptitude remove compiz

```

 - type "exit" to logout

 - Hit ctrl-alt-f7 to get back to graphical login

 - Login.

---

### Post by Haribda on 2009-11-17
Login screen as in the one just before you put your password? I've disabled that. :( Can I do it while it's booting and there is the ubuntu logo loading?

---

### Post by lykwydchykyn on 2009-11-17
> **Haribda said:**
> Login screen as in the one just before you put your password? I've disabled that. :( Can I do it while it's booting and there is the ubuntu logo loading?

No.  You'll probably have to boot to recovery mode.  In which case, just select the option to drop to a root shell and execute the aptitude command I gave you.  Then reboot.

---

### Post by jpeddicord on 2009-11-17
> **Haribda said:**
> Login screen as in the one just before you put your password? I've disabled that. :( Can I do it while it's booting and there is the ubuntu logo loading?

Alternatively, for 9.10, hold down Shift on boot to bring up the boot menu. Select the first option marked "(recovery mode)" and when prompted, select "Root shell" or similar. From there, simply type ```
aptitude remove compiz
``` and follow the prompts. Type `reboot` once finished.

Once you nail down the problem and you want to try desktop effects again, you can install Compiz by installing the "compiz" package in System > Administration > Synaptic Package Manager, or by running `sudo aptitude install compiz` in a terminal.

---

### Post by Haribda on 2009-11-17
OK, I did the first one but just before it finished I guess ubbuntu loaded up and it got stuck again. I did the second thing and I removed completely compiz.Now when my ubuntu boots up, I can move my mouse but nothing else is loaded. I see the desktop but not the icons and the menus. nothing will work not even ctrl+alt+f2. It's frozen again only the mouse is moving and doing nothing.

I'm really confused and frustrated...

---

### Post by lykwydchykyn on 2009-11-17
How did you come to the conclusion that compiz was causing the problem in the first place?  I'm asking because it might be something else, and if so we need to address that.

What is your video card?

---

### Post by Haribda on 2009-11-17
Well I thought that it was compiz since I was enabling it with the splash screen function when it froze. 40 min before it was working just fine untill I got into the compiz settings.

My video card is Intel 965 express chipset family, I don't know what difference does it make. Thanks

---

### Post by lykwydchykyn on 2009-11-17
> **Haribda said:**
> Well I thought that it was compiz since I was enabling it with the splash screen function when it froze. 40 min before it was working just fine untill I got into the compiz settings.

My video card is Intel 965 express chipset family, I don't know what difference does it make. Thanks

Intel stuff generally works fine with compiz, though I've heard some have had problems with the 965 -- I believe it was blacklisted a few releases back.  I had one once, but it was a few years back so I can't say now if it would cause problems.

A hard lock up like you're experiencing is often caused by a problem with the video driver talking to the video chip, which is why I asked.

When it's locked up see if this gets you to a virtual terminal:

alt-sysrq-R
ctrl-alt-f2

---

### Post by Haribda on 2009-11-18
ctrl+alt+f2 works fine just before the dekstop loading and I'm able to access it while it's booting and I see the ubuntu logo. This is how I removed compiz but this didn't help. 

So, if I'm able to get there, what shall I type/do?

---

### Post by lykwydchykyn on 2009-11-18
I don't run Gnome, so I can check this for you, but these instructions tell you how to change the window manager in Gnome:

[http://www.batushkas.com/desktop-tips/46-changing-your-window-manager-in-gnome-224.html](http://www.batushkas.com/desktop-tips/46-changing-your-window-manager-in-gnome-224.html)

You want to change it from "compiz" to "metacity".

So from the command line, just log in and do:
```

nano ~/.gconf/desktop/gnome/session/required_components/%gconf.xml 

```

Change the word "compiz" to "metacity" and hit ctrl-x to save and quit.

If that doesn't work, I apologize; I'm flying blind here myself since I don't have a Gnome desktop handy.

---

### Post by Haribda on 2009-11-18
Thank you for your input, I appreciate it. What I did today was a clean install 9.10 and the first problem I ran into was my Broadcom wireless (if I activate the driver the pc freezes again)

I guess these are normal issues for now and I will just wait for an update. Thank you.

---

### Post by lykwydchykyn on 2009-11-18
You might want to do a memtest, just to be thorough.  Freezing can be a driver issue, but it can also be caused by (physical) hardware problems.

---


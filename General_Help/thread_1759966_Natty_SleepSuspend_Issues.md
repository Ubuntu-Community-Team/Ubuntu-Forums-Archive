---
title: "Natty Sleep/Suspend Issues"
date: 2011-05-16
forum: General Help
---

### Post by Steve2009 on 2011-05-16
I've been using Natty since the release, but I just started having a problem with it. My laptop won't sleep any more. When I close it or tell it to suspend via the menu, I just get a blank screen and it never goes to sleep. How can I figure out what is causing this and fix it?

---

### Post by Steve2009 on 2011-05-16
Bump. I could really use some help with this. I've been trying to like Ubuntu over the past several months, but problems like this keep me going back to Windows. Windows is so much better when it comes to solving problems.

---

### Post by dFlyer on 2011-05-16
> **Steve2009 said:**
> Bump. I could really use some help with this. I've been trying to like Ubuntu over the past several months, but problems like this keep me going back to Windows. Windows is so much better when it comes to solving problems.

You either like it or you don't. If you want to go back to windows; Good Luck. If you want to solve this problem give us a little history and what you have already tried. Remember and OS is a personal choice and your free to do as you wish.

---

### Post by Steve2009 on 2011-05-16
> **dFlyer said:**
> You either like it or you don't. If you want to go back to windows; Good Luck. If you want to solve this problem give us a little history and what you have already tried. Remember and OS is a personal choice and your free to do as you wish.

I haven't tried much other than uninstalling a couple of programs that I don't need in case they are preventing the OS from suspending. I don't know enough about Ubuntu to know what else to try; that's why I'm asking for help. I don't even know enough to know what information you may need to help me so feel free to tell me.

I just get frustrated because it seems that every time I post on this site I just get ignored. No one helps me and I either end up living with the problem or reinstalling the OS.

---

### Post by dFlyer on 2011-05-16
First what programs did you uninstall? 

Were they programs you added after you install Natty or were they programs you removed from the original Desktop install? 

Can you run synaptic?

---

### Post by Steve2009 on 2011-05-17
I only uninstalled a couple. They were programs that I had installed after installing Natty. One was caffeine but I don't remember what the other was. 

Synaptic runs fine as does everything else.

---

### Post by dFlyer on 2011-05-17
Okay, let just try something. It may or may not work but it should hurt anything. Start synaptic and search for gnome-power-manager. If it's still installed, mark it for reinstallation. Now search for gnome-screensaver and mark that for reinstallation. Last program to search for is pm-utils and mark that for reinstallation. Apply changes, reboot and see what happens.

---

### Post by dFlyer on 2011-05-17
> **Steve2009 said:**
> I only uninstalled a couple. They were programs that I had installed after installing Natty. One was caffeine but I don't remember what the other was. 

Synaptic runs fine as does everything else.

One thing I should have asked above was did you completely uninstall caffiene and all the config files, as caffiene prevents sleep and screensaver.

---

### Post by Steve2009 on 2011-05-20
> **dFlyer said:**
> Okay, let just try something. It may or may not work but it should hurt anything. Start synaptic and search for gnome-power-manager. If it's still installed, mark it for reinstallation. Now search for gnome-screensaver and mark that for reinstallation. Last program to search for is pm-utils and mark that for reinstallation. Apply changes, reboot and see what happens.

I did what you said, but it didn't fix the problem. 

On uninstalling caffeine: I got rid of it using ```
apt-get --purge remove caffeine
``` so it should be completely uninstalled. 

Something that I should probably mention is that the problem comes and goes. I haven't posted for the past several days because the problem was gone. After a reboot today, it's back. 

Thanks for your help!

---

### Post by dFlyer on 2011-05-20
You might want to search your home directory for a hidden file or folder caffeine. If no caffeine file is found than you might want to contact the person who wrote the program to see want files that program changed. My guess is that it would be something in your .gconf folder under gnome-screensaver or gnome-power-manager. Sorry I can't be of much more help.

---

### Post by johnthomson on 2011-05-21
Hello, I have the same problem since installing 11.04. 10.10 worked fine as does 10.04. When I press the power button Suspend works as expected, but
not on 30 minute timeout which just goes to blank screen.
Nothing new installed after 11.04. Have other problems too, but I think they are not associated. ie sometimes have to boot safe graphics and re-establish graphics (Nvidia). Boot fail after disk check. I am running Ubuntu Classic.

regards, John

---

### Post by johnthomson on 2011-05-23
to answer my own post, adding the parameter "nopat" to the GRUB_CMDLINE...
in etc/default/grub
seems to solve both the power management, and the continually having to re-establish the graphics files problem on reboot problem. At least for me.

---


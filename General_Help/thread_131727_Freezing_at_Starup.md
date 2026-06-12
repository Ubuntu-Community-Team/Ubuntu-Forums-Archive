---
title: "Freezing at Starup"
date: 2006-02-17
forum: General Help
---

### Post by SVFUSiON on 2006-02-17
Hello, I just installed Ubuntu on my notebook. After the install was done I had to install xserver-org. Before that I only could get text mode. When I login with the unbutu login (the one that isn't text mode) it starts playing that sound then freezes. Any idea?

---

### Post by kenweill on 2006-02-17
I have no idea. I have never tried installing xserver-org.
What is that for? Im just curious.

---

### Post by RAOF on 2006-02-17
[QUOTE=SVFUSiON]Hello, I just installed Ubuntu on my notebook. After the install was done I had to install xserver-org. Before that I only could get text mode. When I login with the unbutu login (the one that isn't text mode) it starts playing that sound then freezes. Any idea?[/QUOTE]
Have you tried setting the session to "gnome failsafe"?  Does that work?

If you needed to install xserver-xorg, you presumably selected a "server" install.  Maybe you should apt-get install ubuntu-desktop.  Maybe there's a program you need from there before everything will work.

---

### Post by SVFUSiON on 2006-02-17
When I click "Failsafe Gnome" it freezes, when I go in recover mode so I can use the console I tired, "sudo apt-get install ubuntu-desktop and it said the following  packages have been kept back "Linux-image-386 and linux-restriced-modules. 0 upgraded 0 newly installed - to remove and 2 not upgraded.

---

### Post by RAOF on 2006-02-17
How hard does it freeze?  Can you still move the mouse around?  Does pressing Ctrl-Alt-F1 get you to a terminal login screen?  Do the caps-lock etc leds work?

How long have you waited for it?  Presumably long enough to determine that it's not just slow ;).  How do you recover from it?

---

### Post by SVFUSiON on 2006-02-17
The mouse freezes, I have to hold the power button down to shutdown the notebook. I have waited about 10 min to get passed it but it never did.

---

### Post by SVFUSiON on 2006-02-17
also, the capslock does not work when it locks up.

---

### Post by RAOF on 2006-02-17
Woah, ok.  That's a genuine, certified kernel panic :)

From recovery mode, try running "apt-get update" followed by "apt-get upgrade".  That should upgrade the two packages that were kept back.  Maybe the latest kernel has a fix for you.

---

### Post by SVFUSiON on 2006-02-17
did that, still does not work.

---

### Post by kenweill on 2006-02-17
Whats your machine?
I've been with a freezing problem with my current machine before, using IBM ThinkCentre computers.

---

### Post by SVFUSiON on 2006-02-17
Compaq M2000

I just got it working, I just searched the forums some more,

[http://ubuntuforums.org/showthread.php?t=69367](http://ubuntuforums.org/showthread.php?t=69367)

I am going to bed... THANKS EVERYONE for your help!

---

### Post by SVFUSiON on 2006-02-17
doing that, I can not have any 3d accel? hmm?

---

### Post by kenweill on 2006-02-17
I just did insert "noapic" and "apic=off" in my kernel parameter found in GRUB.
I don't know exactly how that works, or for what that parameter is, but it works.

---

### Post by SVFUSiON on 2006-02-17
Could you please tell me how to do that? Maby that will give me 3d accel .

---

### Post by kenweill on 2006-02-17
sudo gedit /boot/grub/menu.lst

Find the line that looks like this:
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash

Modify it to be like this:
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro noapic apic=off quiet splash

Thats what I did. I don't know if it works for you.

---


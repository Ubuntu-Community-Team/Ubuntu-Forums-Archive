---
title: "First Linux Install, Won't Boot"
date: 2006-02-28
forum: General Help
---

### Post by prrometheus on 2006-02-28
Hi All,


My Ubuntu install appeared to go smoothly. It loaded a bunch of stuff from the CD, asked me a few questions, and then asked me to remove the CD and reboot. I did so, and the installer began to load more programs. Eventually it got to a non-blinking cursor on a plain back background and froze. I tried to reboot. The boot-up process seems to go fine, but then it gets to the same non-blinking cursor and freezes. 

Any help would be appreciated. For what it's worth I'm running a Pentium III Compaq Presario desktop. 

Peace.

---

### Post by AnnihilationDreamscapes on 2006-02-28
That sounds like my old problems! Try burning your cd at a lower speed. Sometimes when you burn at high speeds it causes problems when loading the additional packages after your initial boot. I hope I'm right.

---

### Post by liger13 on 2006-02-28
i had the same problem but when i tried it again everything worked out fine.

---

### Post by RAOF on 2006-02-28
It's probably a graphics card issue - what sort of graphics card does your box have?

Anyway, you should be able to boot into "recovery mode" - if you don't see a list of boot options, press "esc" when it says "press esc to see grub menu..." or similar.  Select the "Ubuntu *some stuff* (recovery mode)" option.

Once that's finished booting, you should be at a command prompt.  Type in "dpkg-reconfigure xserver-xorg".  This will configure your GUI (techincally, the X server which is what the GUI uses to draw to the screen).  It will ask a whole bunch of questions; the default answer will be fine, unless you know better.  At one point it will give you a list of possible graphics drivers (nv, ati, radeon, trident, etc).  Select the "vesa" driver - this is a failsafe driver, which should work.

Once you've finished that, and are back at the command prompt, type "exit" to continue booting.  You **should** get to the graphical login screen.

---

### Post by prrometheus on 2006-03-01
No dice, though I did get a little farther. Now the command prompt is [username]@ubuntu:~$

---

### Post by xhie on 2006-03-01
login then try:

sudo /etc/init.d/gdm start

if it says gdm is allready running do 

sudo /etc/init.d/gdm stop   

then that first command. see what it does.

---

### Post by prrometheus on 2006-03-01
Xhie,

It says it is unable to start X-Server because it is not set up correctly (note: I have followed a previous poster's advice and changed the x-server display driver to "Vesa"). Typing "startx" gives an error screen including the line "Fatal server error: no screens found"/

---

### Post by RAOF on 2006-03-01
What does /var/log/Xorg.0.log have to say, particularly (EE)?

Try 
```
cat /var/log/Xorg.0.log | grep "(EE)"
```

---

### Post by prrometheus on 2006-03-01
Raof,

When I ran the command you specified, I received the following output:

"(WW) warning, (EE) error, (NI) not implemented, (??) unknown.

---

### Post by RAOF on 2006-03-01
That's odd.  If it's not working, there should be at least **some** errors.  How about just the output of "cat /var/log/Xorg.0.log"?

---

### Post by prrometheus on 2006-03-01
Raof,

That gives a screen full of hex memory ranges, then at the bottom it says "Missing output drivers.  Configuration failed."

---

### Post by RAOF on 2006-03-01
Ok.  Looks like the X server hasn't been properly installed.

Try running "sudo apt-get install ubuntu-desktop".  Then see if it works.

---

### Post by prrometheus on 2006-03-01
oh, and I have an nVidia Geforce2 graphics card, according to the autodetector.

---

### Post by RAOF on 2006-03-01
Well, the "nv" drivers that it should default to should work fine.  As long as X is installed correctly, which it obviously isn't.

Once everything's up and running, you may want to check out the "nvidia drivers" link in my sig, to get 3d acceleration

---

### Post by mlind on 2006-03-01
and if want to run interative setup wizard for your X
run *sudo dpkg-reconfigure xserver-xorg*. 

Remember to backup original /etc/X11/xorg.conf first.

---


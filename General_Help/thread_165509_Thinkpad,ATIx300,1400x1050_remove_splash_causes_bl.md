---
title: "Thinkpad,ATIx300,1400x1050: remove splash causes blank screen on startup"
date: 2006-04-24
forum: General Help
---

### Post by prokher on 2006-04-24
Hiall.

I have some troubles with Kubuntu Dapper Drake with all latest updates. To investigate them i have to turn of startup splash screen by removing "quite" and "splash" keyword from grub configuration (actually, i've done it on startup with GRUB menu). And, omg, there are black screen in all consoles. I can only wait for X server startup.

Details:

originally i have (from distro & updates):
/boot/vmlinuz-2.6.15-21-686 root=/dev/sda1 ro vga=0x344 quite splash
everything is ok, i see vesafb and fbconf in lsmod and console (i mean system console, involved with ctrl+alt+f1 for example) works great. I mean i have real 1400x1050 in console mode. But, i see splash screen during startup instead of system diagnostic messages i want to see.

i changed that line to:
/boot/vmlinuz-2.6.15-21-686 root=/dev/sda1 ro vga=0x344 quite
or
/boot/vmlinuz-2.6.15-21-686 root=/dev/sda1 ro vga=0x344
and i see only black screen while loading my linux. I have to wait for x startup to see something on the screen. I want to see system loading information (loading modules and etc.) in good resolution of course. lsmod show me, that only fbconf is loaded. (checked with lsmod | grep fb).

Is there anybody can help me with it?

thanks.

---

### Post by Vincent_Lin on 2006-04-25
Try this, even I am T42 user with ATI 9600.

On IBM BIOS setup, go to Config -> Display and set HV expansion to On.

I had palyed with this setting once, hoping to get the effect you described, full screen hi-res display of linux booting processes, to no ends.  Turn HV on will expand a standard VGA text display into full screen (scaled up blur image), but definite the display will come up.

Good luck,

Vincent

---

### Post by prokher on 2006-04-25
Than you for advice but it didn't help. Actually, i am sure that it is a framebuffer problem. It works only when there is "splash" kernel parameter set . I don't understand why :(

---

### Post by Vincent_Lin on 2006-04-25
You were right.  HV option is not related.  I just then found this thread

[http://www.ubuntuforums.org/showthread.php?t=41709&highlight=vga%3D0x3](http://www.ubuntuforums.org/showthread.php?t=41709&highlight=vga%3D0x3)

Hopefully the vga= option, obviously different from what you are using, can give you another idea where to test.

I used vga=794 and the bootup screen is hi-res (1280x1024) as you wanted.  However, I still don't know what the mode number is for 1400x1050, the same mine has as yours.

Vincent

---

### Post by prokher on 2006-04-25
It doesn't work too :( I already found out that my mode is vga=835, but it dosn't work too. ([http://www.thinkwiki.org/wiki/Kernel_parameters](http://www.thinkwiki.org/wiki/Kernel_parameters))

---

### Post by Vincent_Lin on 2006-04-25
While you were looking, I was looking too:D 

I used VGA=834, instaed of 835.  Confirmed VGA=835 also works on my T42.

my lsmod | grep fb gives me vesafb as well as fbcon.  Unfortuantely I don't know how it gets there.  Maybe you should modprobe vesafb as well.

I had installed fglrx driver for my T42, which gives me a nice "feeling" for performance, because I really can't tell the difference from before.  I am also suffering from the Ctrl-Alt-Backspace hangs problem.  I usually do either of two things when I don't use this machine - close the screen(sometimes sleep will work and I can wake it up later without ill effect), or just run sudo shutdown -h 0, instaed of going through gnome menu options for shutdown.

Regards,

Vincent

---

### Post by prokher on 2006-04-25
:) Great! Thank you. Why didn't i get it by myself? ;)
Ok, great, modprobe vesafb works fine. Now i can see my linux consoles in hires. The last question is how to load this module automatically? I can use /etc/modules, but why kernel doesn't load this module by itself, like when i use "splash" parameter ?

---

### Post by Vincent_Lin on 2006-04-25
Hi,

It seems that you started another thread, and another person also started a thread with the same issue.  Unfortunately it also seems that you guys are all using Dapper, and I am using Breezy.  That seems to be the difference.

I did not help too much, huh..

Vincent

---

### Post by prokher on 2006-04-26
Anyway, thank you. 
Btw, what "other" thread do you mean? who started it, where?

---

### Post by Vincent_Lin on 2006-04-26
Search the forum for vesafb, and there are a number of results/threads showing up.  Those who have similar symptons like yours are running Drapper.

Regards,

Vincent

---

### Post by babounours on 2008-04-05
splash needs the fb module so the system loads it automatiquely, if you want it to be loaded without needing to add it in the /etc/modules, you must compile it in the kernel.
By the way I found this thread because of a trouble with my splash:
I recently changed my screen for a 16:9 television that doesnt support 12??x1024 resolution and it made the framebuffer taking a wrong resolution providing a black screen during the startup procedure. I add to change the resolution of the splash screen in /etc/usplash.conf and the update the initramfs :
update-initramfs -u

---


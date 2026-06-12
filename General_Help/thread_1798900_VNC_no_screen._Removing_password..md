---
title: "VNC no screen. Removing password."
date: 2011-07-06
forum: General Help
---

### Post by raphaeltm on 2011-07-06
Hi there!

I'll start off by pointing out that I am an ubuntu newb.

So, I've got a really old machine that I got for free and eventually I want to use it to run things while connected to an arduino, so I don't really need to see what's going on with a screen.

For that reason I set up the "Remote Desktop" application (with a password for access and no confirmation), since I figured that that's one less vga-cable/mouse/keyboard to worry about.  I tried it and had everything running the way I wanted, so I removed the mouse/keyboard and vga cable.  I had expressly set things up the log-in screen so that it would log in automatically. I thought this meant I would now be able to do everything on this crappy old computer without actually having anything other than my ethernet and power cable plugged into it.

So I turn on the thing and wait a bit, knowing that it takes a while to boot. I then launch UltraVNC viewer.  I try to connect, but it doesn't work. After testing with my old laptop as well, I found out that it wasn't accepting the connection because it required somebody to actually input a password before allowing any connections.

This defeats the whole purpose of my setup! I've heard that x11VNC server allows access from the login screen, but... it seems like it's all command-line? Command line stuff confuses me :-( Also, I'm not sure I understand this all very well... if I try to access the computer remotely with x11vnc, will I only have a terminal? or is that just in getting things working? I definitely want a GUI, if possible. 

I just wanted to know if anybody has any suggestions as to whether I should try to figure out x11vnc, or can the default "Remote Desktop" application do what I want it to? Or any other sort of help? :-P

Thanks!

Raphael

P.S. For now it's just for a potential arduino project, but eventually, I'll be wanting to set up a render farm using vnc. Thought I'd let you know in case there is a tool that's better for that sort of application.

---

### Post by krunge on 2011-07-07
x11vnc can connect to the login screen and export it via VNC.

Usually you just have to a line to the file /etc/gdm/Init/Default if your login manager is Gnome Display Manager (GDM) and that will launch x11vnc for each X login.  See the section labelled 'Continuously' here:

[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]

So you will have access to the full gnome/kde/whatever desktop (not just a terminal.)

One thing I'm worried about for you is since you remove the monitor/keyboard/mouse, the X server might refuse to start (e.g. because it doesn't know what video modes the monitor supports.) Since you don't know how to use the Unix cmdline, you might have difficulty checking if the X server is actually running. Anyway, if the X server doesn't start because of no monitor, etc., you'll need to fix that before trying to export it via VNC.

If I understand you correctly you don't need access to the physical hardware, in which case you might want to run a Virtual framebuffer instead. Some ways to do this are using programs "vncserver", "Xvfb+x11vnc -create", and "nx".

---


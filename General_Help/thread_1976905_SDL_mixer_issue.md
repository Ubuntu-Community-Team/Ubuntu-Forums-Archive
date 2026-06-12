---
title: "SDL mixer issue"
date: 2012-05-09
forum: General Help
---

### Post by N1GHTS on 2012-05-09
I created a graphic accelerated application using the SDL mixer which in Ubuntu 11.04 runs correctly and plays sounds as I expect but when I run it in Ubuntu Server 10.04 with a very basic Xorg installation and "libsdl-mixer1.2" with pulseaudio and alsa installed it does something very strange. 

The only way to hear sounds on that system is if I press Control-Alt-F1 or Control-Alt-F2 or something like that. In other words, I have to change the focus away from the application using that keyboard shortcut method and then I hear all the sounds that were supposed to play playing all at once at the same time immediately after switching the screen. Nothing plays during the program execution.

Does anyone have any idea what could be wrong? The program runs two threads over OpenGL and SDL + SDL_Mixer.

---

### Post by N1GHTS on 2012-05-10
I solved the problem. It was many things, none of which was related to **SDL** or **SDL_mixer**.

For those who want to know how I repaired it, I had to edit **/etc/init.d/pulseaudio** and change the value of **PULSEAUDIO_SYSTEM_START** to **1**. Also, I needed to add the user logged in to Xorg to the following group's: **pulse**, **pulse-access**, **audio**.

```
sudo usermod -G pulse,pulse-access,audio my_user_name
```After a reboot it worked as expected.

This is apparently only required for an Xorg installation with a minimalist window manager or none at all. If Gnome or KDE were installed, they take control of the audio system on their own and it would not be an issue.

---


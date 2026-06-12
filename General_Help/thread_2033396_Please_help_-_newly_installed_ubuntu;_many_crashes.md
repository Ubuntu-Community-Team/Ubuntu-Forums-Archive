---
title: "Please help - newly installed ubuntu; many crashes and problems"
date: 2012-07-26
forum: General Help
---

### Post by Toitovna on 2012-07-26
Hello, I just installed Ubuntu 12.04 on a new computer, and straight away have been experiencing the following problems:

- Music programs like Rhythmbox & Clementine crash and force quit before anything can be played every time
- System Settings crashes every time I try to load the Sound sub option, I still haven't been able to access it
- VLC media player unable to play any avi or mp4 file, doesn't crash just sits there not playing anything
- Thunderbird crashes as soon as I click on any piece of mail
- Chromium unable to load YouTube sites or seemingly anything content-heavy

I'm able to use the internet, launch LibreOffice applications and that's about it. I still haven't been able to play a single song or video and it's kind of ridiculous. I only just bought this computer and obviously need it to be able to do basic things like play my music and movies. PLEASE help me, I am a Linux n00b. Is there a fix to any one or all of these problems that you guys know?

Thanks in advance.

---

### Post by Albury_Boy on 2012-07-26
Hey Toitovna,

I've recently installed 12.04 on two computers myself, and there are always some teething problems on a new install. Luckily they are usually sorted out pretty easily and the system settles down after a little while.

The first step is to make sure your repositories aren't broken, and to run an update.

1. Open a terminal -> ctrl + alt + t OR click on the 'Dash home' icon on the left of your screen and type 'terminal'

2. Enter the command: sudo apt-get update && sudo apt-get upgrade

This will update your system to the newest software releases and 'should' solve your problem. It fixed my desktop straight away after I had similar problems with my install. 

Let me know how this goes :-)

---

### Post by Statia on 2012-07-26
Did you install mp3 support and extra codecs?

Here is a nice starter:

[http://www.omgubuntu.co.uk/2012/04/10-things-to-do-after-installing-ubuntu-12-04](http://www.omgubuntu.co.uk/2012/04/10-things-to-do-after-installing-ubuntu-12-04)

---

### Post by Toitovna on 2012-07-26
OK well I did both of those things, but they didn't solve the problem and now I have another one - whenever I boot Ubuntu, some icons aren't showing up (such as the home folder, system settings, workplace switcher). When I open a folder, such as the home folder, the icons are all white rectangles and the screen behind them is dark blue, as is the navigation and scroll bars.


What is going on?!

---

### Post by Albury_Boy on 2012-07-27
1. Did the updates run ok? 
2. Were there any that failed?
3. Did you note which repositories were being used? eg. Precise, Natty or Quantal
3. What hardware are you using? Do you have a NvIDIA or ATI graphics card?

It sounds like you've got a couple of different underlying problems.

One problem could be that the X server (or graphics server) is not configured correctly, thus the weird colours. Try booting into a recovery mode at the grub menu. If you don't get a grub menu, then hold down shift during boot up. Select the first recovery mode (if there are more than one). Once that boots, select 'boot into failsafe graphics mode', and play with the display settings.

Let me know how you go.

---

### Post by Toitovna on 2012-07-31
I just re-installed ubuntu entirely and it's working fine now :)

---

### Post by Albury_Boy on 2012-07-31
Good to hear. :-)

---


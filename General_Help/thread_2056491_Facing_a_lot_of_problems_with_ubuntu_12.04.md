---
title: "Facing a lot of problems with ubuntu 12.04"
date: 2012-09-11
forum: General Help
---

### Post by Hacht on 2012-09-11
[LEFT]Hi, about three days ago I bought a new Samsung laptop (NP535U3C-A02SE) and the first thing I did when I got it was installing(about 10 times) the Ubuntu 12.04. After that it have just been a nightmare. 
[/LEFT]
 
I put  my ubuntu version on a USB-stick that I installed it from, I had to reboot my computer several times because the installation kept on crashing, I often came to the part where you choose your profile picture and the only thing I could see was myself in the webcam. 

After a while i finally succeeded to install the operating system and from there I have had several other problems: 

- When I sometimes comes to the login screen it just dosnt respond, i press ctrl+alt+F1 and try to halt the system, I see the logo and it just stops, nothing happens after that. 
- Firefox crashes when I browse youtube.com, I thought that "*ubuntu*-restricted-*extras package" * would have something to do with it, but no. 
- In the corner of my screen i have  a little marker that says "AMD Unsupported Hardware", this I think is because I tried earlier to get some drivers for my graphic card in Ubuntus additional drivers support. 
- The sound doesnt work and if I try clicking the sound icon (under hardware) in System settings, System setting crashes. 
- I cant turn my computer of by the help of ubuntu, this I must do by brute force in 9 of 10 cases. 

So:
Do you think it can have something to do with the laptop or ubuntu?
Any idéa how to fix these problems, what do you think I should do?

thanks for your time, sry for bad english
regards KJ

[EDIT] After a lot of different ways by install/uninstall software I somehow got it to work, cant say exactly what I did..

---

### Post by AndyOpie150 on 2012-09-11
Did you install the proper Ubuntu.iso for your system (i.e. the i386 for 32 bit windows OS, etc, etc.)?
What Utility did you use to install the Ubuntu.iso to your USB to make the Ubuntu.iso bootable through your USB (I used the Pendrivelinux utility program with no problems at all)?

Have you tried using the Utility program on the Ubuntu Download site to put the Ubuntu.iso onto a CD? Might work better for your system.

---

### Post by VishnuNJ on 2012-09-11
DO A SYSTEM UPDATE.. newer hardware's drivers will only be available in next ISO.. for this version you have to update to latest.. 


```

 sudo apt-get update -y  && sudo apt-get upgrade -y && sudo shutdown -P  now -r

```Run the above in a terminal..
If system is crashing while doing it.. 
 press Ctrl+Alt+F1, log in, and run it there..

---


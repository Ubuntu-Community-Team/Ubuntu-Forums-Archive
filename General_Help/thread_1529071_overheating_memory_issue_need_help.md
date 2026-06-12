---
title: "overheating? memory issue? need help"
date: 2010-07-11
forum: General Help
---

### Post by rowestayposi on 2010-07-11
[IMG]http://i27.tinypic.com/35hmmnd.jpg[/IMG]


Anytime i open an application like firefox and something starts to load i get that screen.
I downloaded and installed ubuntu desktop i386

---

### Post by chessnerd on 2010-07-11
Curious.

Okay, is this only an issue with the GUI? In other words, does the command-line interface still work?

When the computer boots, press Ctrl-Alt-F2 and you will be at a command prompt. Log in there and then try to use it. If you don't know any commands, here are some -

ls - shows files and folders in the current directory
free - shows RAM and swap usage
cd - changes directories (so in your home folder, cd Documents would move you to your Documents folder)

A good CLI program to test might be nano. Just type "nano" and [Enter] and you'll be in a basic CLI text editor. Ctrl-X will exit it.

If that works, then the issue likely involves X, the Linux windowing system.

In that case, I have some questions:
Is Ubuntu newly installed (have you updated it yet)?
 - If you haven't updated yet, update using these commands:
```
sudo apt-get update
sudo apt-get upgrade
```
 - If you have updated, then this could be an issue with one of those updates.

Do all programs make the system crash (like the calculator, terminal window, etc.), or only select ones (like Firefox)?

What graphics card are you using?

---

### Post by rowestayposi on 2010-07-12
All the other programs work fine. Its when i load a page on firefox that i get that screen. Ubuntu is newly installed, but i will try to update it. I'm not using a graphics card because my old one overheated; i'm using the motherboard now.

---

### Post by rowestayposi on 2010-07-12
tried to upgrade through terminal and im guessing its upgraded. command prompt works fine too.

i dont know if this matters but i installed the OS through a usb drive.
also this is my first time ever attempting to use linux, so bare with me :)

---

### Post by chessnerd on 2010-07-13
Okay, well if Firefox is the only program causing the problem, then it seems like Firefox is where we should start...

Here are several different options:

Switch to another browser -
Under Applications>Ubuntu Software Center simply go to Internet>Browsers and you will see several other browsers that are available for download. Midori and Ephiphany are probably the most popular ones available in there. If you can get one of those working, but don't care for it, then you can also download another browser (such as Google Chrome or Opera) from the Internet.

I would suggest installing another browser anyway. It would be helpful to know if it really is Firefox causing the problem, or if this happens whenever you try to connect to any website through any source.

Reinstall Firefox -
Go to System>Administration>Synaptic Package Manager and type in Firefox. Click on the little checkbox areas of the installed Firefox's components and select them for re-installation.

Upgrade Firefox -
Through a different browser, you could get the Firefox 4 Beta and try to use that. It is very feature-incomplete however, doesn't work with most extensions, and can be unstable. However, it might not cause this problem.

Do install another browser and try to use it, I will be interested to see if that causes any problems. If it doesn't then at least you could browse using that until we find a permanent solution...

---

### Post by rowestayposi on 2010-07-18
i tried to download a new one and it keeps crashing. :(

---

### Post by watupgroupie on 2010-07-18
Post some hardware specs. Could be that once you put enough load on your system it's crashing. Try doing some load intensive things and see what happens (like encoding a video or something?).

---


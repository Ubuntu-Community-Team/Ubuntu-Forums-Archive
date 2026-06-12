---
title: "Comp freezes about 10 secs after log-in."
date: 2011-03-15
forum: General Help
---

### Post by Ruinofthedead on 2011-03-15
Hi.. I recently installed Ubuntu on my spare comp.

It freezes after about 10 seconds after logging in. I don't know why this happens.


It's a Dell Dimensions 4100. Installation went fine. I did everything, didn't skip any checks. It finished normally.

And now my hopes of another working computer have gone down the drains.

---

### Post by Hippytaff on 2011-03-15
Have you tried turning compiz (the magic 3d uberpointless effects) offGo to ->system->preferences->Appreance. Go to the effects tab and choose None.

What are the specs - how much ram, graphics card etc

---

### Post by Ruinofthedead on 2011-03-15
> **Hippytaff said:**
> Have you tried turning compiz (the magic 3d uberpointless effects) offGo to ->system->preferences->Appreance. Go to the effects tab and choose None.

Well, my monitor resolution is all messed up, and I cant see anything. 

Can't access any options.

---

### Post by Hippytaff on 2011-03-15
try rebooting first.

Have you tried [lubuntu?]("http://lubuntu.net/")

---

### Post by Ruinofthedead on 2011-03-15
> **Hippytaff said:**
> try rebooting first.

Have you tried [lubuntu?]("http://lubuntu.net/")

I've tried re-booting. No help.

---

### Post by Hippytaff on 2011-03-15
do you know what graphics card you have?

---

### Post by Ruinofthedead on 2011-03-15
> **Hippytaff said:**
> do you know what graphics card you have?

No. I havent really worried about the graphics card. Windows worked on it before, but Ubuntu is frozen. It's been about half an hour. Still frozen.

Can I like, go into the settings or something?

---

### Post by Hippytaff on 2011-03-15
try pressing ctrl+alt+F1...log in to the terminal...if that doesn't work, reboot into recovery mode.

either way, you should get to a terminal, when you do type ```
lspci
``` and ```
free
```. make a note of the graphics card and the total amount of ram. post it here :-)

---

### Post by Ruinofthedead on 2011-03-15
> **Hippytaff said:**
> try pressing ctrl+alt+F1...log in to the terminal...if that doesn't work, reboot into recovery mode.

either way, you should get to a terminal, when you do type ```
lspci
``` and ```
free
```. make a note of the graphics card and the total amount of ram. post it here :-)

Okey doke. Do I do that on startup? Because I think it will freeze before I get anything. :(

---

### Post by Hippytaff on 2011-03-15
boot and when you get to choose which os to boot into choose recoverymode. If for some reason you don't get the option....don't log into ubuntu graphical bit, but press CTRL+ALT+F1. Then do the commands and report the results :-)

---

### Post by Ruinofthedead on 2011-03-15
> **Hippytaff said:**
> boot and when you get to choose which os to boot into choose recoverymode. If for some reason you don't get the option....don't log into ubuntu graphical bit, but press CTRL+ALT+F1. Then do the commands and report the results :-)


Well, I deleted the Windows XP off of it, and I'm using Lucid Lynx because that's the LTS version. I don't get the option to choose which os. :P

Just CTRL+ALT+F1 on startup?

---

### Post by Hippytaff on 2011-03-15
...or press shift just after boot to get to the 'grub' menu to choose the recovery mode thing

---

### Post by Ruinofthedead on 2011-03-15
I got 250444 total "mem".

It says here that I have a "Matrox Graphics Inc, MGA G400/4500".

I have no idea what this means. Maybe you could help.

---

### Post by Hippytaff on 2011-03-16
Can you try going to the grub menu (By pressing shift at boot) highlighting ubuntu and pressing e. Change 'quiet splash' to nomodeset' and press X (or ctrlX) to reboot.
 
If that works go to system->Administration->Adiitional drivers and install the drover if it is there. If nomodeset doesn't work try the same procedure but add 'acpioff' to the end of the grub line (after 'quiet splash')

---

### Post by Ruinofthedead on 2011-03-16
> **Hippytaff said:**
> Can you try going to the grub menu (By pressing shift at boot) highlighting ubuntu and pressing e. Change 'quiet splash' to nomodeset' and press X (or ctrlX) to reboot.
 
If that works go to system->Administration->Adiitional drivers and install the drover if it is there. If nomodeset doesn't work try the same procedure but add 'acpioff' to the end of the grub line (after 'quiet splash')

Well, none of those worked. Gave me hope though. :'(

I also noticed at the bottom, when I click on my name to Sign In, it has GNOME in the sessions. Can that affect me?

---

### Post by antaios256 on 2011-03-16
gnome is the type of desktop ... if there is a KDE option you can try that, its just a different graphical interface.

---

### Post by TimEnid on 2011-03-16
i experienced freezing after logging in as well. do you have any external hard drives connected to your pc?

---

### Post by Hippytaff on 2011-03-16
Can you boot into a livecd environment?
 
If so can you post the results.txt by running [this script]("http://sourceforge.net/projects/bootinfoscript/")
 
I don't think it is a boot problem, but its worth checking

---

### Post by Rubi1200 on 2011-03-16
Have you tried this?
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Freezes%20right%20after%20entering%20login%20credentials]("https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Freezes%20right%20after%20entering%20login%20credentials")
You can do this from Recovery Mode.

Boot script suggested by Hippytaff is also a good idea.

---

### Post by Ruinofthedead on 2011-03-16
> **Hippytaff said:**
> Can you boot into a livecd environment?
 
If so can you post the results.txt by running [this script]("http://sourceforge.net/projects/bootinfoscript/")
 
I don't think it is a boot problem, but its worth checking

I'll try the boot from CD.

Will post results soon.



*Alright, I clicked Try Ubuntu Without Installing. Currently loading.*

*Took a while to load. I see my mouse, but it's frozen. I'm really thinking the problem is from the Desktop effects, which I will disable. Hope that works.

Alrightey. I think I found out what it is. It's the desktop effects. How can I disable them in Ctrl+Alt+F1 Terminal?

"sudo chmod a-x /usr/bin/compiz" 

That doesn't help.

---

### Post by Hippytaff on 2011-03-16
Also look at Rubi1200's suggestion...Rubi can run circles around me when it comes down to it

---

### Post by Ruinofthedead on 2011-03-16
> **Rubi1200 said:**
> Have you tried this?
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Freezes%20right%20after%20entering%20login%20credentials](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#Problem:%20%20Freezes%20right%20after%20entering%20login%20credentials)
You can do this from Recovery Mode.

Boot script suggested by Hippytaff is also a good idea.


Well, I need a terminal command line to disable compiz.

I dont care if it's a hard kill, or graceful exit. I want it off.

---

### Post by Hippytaff on 2011-03-16
try
get to the login bit, do ctrl+alt+F1 and type```
killall compiz.real
```

---

### Post by Ruinofthedead on 2011-03-16
> **Hippytaff said:**
> try
get to the login bit, do ctrl+alt+F1 and type```
killall compiz.real
```


After entering, I get "No Process Found"

---

### Post by Hippytaff on 2011-03-16
ok then you need to type ```
top
``` then make a note of process id of compiz (PUID or PID) then do```
killall pid {that number}
```

---

### Post by Ruinofthedead on 2011-03-16
> **Hippytaff said:**
> ok then you need to type ```
top
``` then make a note of process id of compiz (PUID or PID) then do```
killall pid {that number}
```

:shock:

I cant even find Compiz in the command list on the right.

---

### Post by Rubi1200 on 2011-03-16
You should also be able to use the commands I linked to in the tty (which Hippytaff pointed you to: ctrl+alt+F).

---

### Post by Ruinofthedead on 2011-03-16
> **Rubi1200 said:**
> You should also be able to use the commands I linked to in the tty (which Hippytaff pointed you to: ctrl+alt+F).

I did those..

They didn't help.

---

### Post by Rubi1200 on 2011-03-16
If you can login at the tty, try to get to the desktop with either:

```
sudo startx
```or 

```
sudo service gdm start
```

edit: did you try rebooting after trying to disable compiz previously?

---

### Post by Ruinofthedead on 2011-03-16
> **Rubi1200 said:**
> If you can login at the tty, try to get to the desktop with either:

```
sudo startx
```or 

```
sudo service gdm start
```

Well, when I boot up, I go to the log-in screen, and Ctrl+Alt+F1.
And I can Log In at the tty.

None of those codes worked.

---

### Post by Rubi1200 on 2011-03-16
When you get to the login screen, have you tried using Safe Graphics Mode?

---

### Post by Ruinofthedead on 2011-03-16
> **Rubi1200 said:**
> When you get to the login screen, have you tried using Safe Graphics Mode?

How would I get to that?

---

### Post by Rubi1200 on 2011-03-16
> **Ruinofthedead said:**
> How would I get to that?
When you get to the login screen, click on your user name but don't type your password yet. At the bottom of the screen you can choose to use safe graphics mode from the menu (default is Gnome regular).

It is also worth considering if this might be a RAM issue (your computer is fairly old right?).

---

### Post by Ruinofthedead on 2011-03-16
Oh wow. I'm such a dork.

The original code that Rubi gave me worked. the sudo chmod a-x /usr/bin/compiz?

It worked. It just didn't give me a message when I entered my password, so I assumed it didn't do anything.

Thanks so much. I appreciate all this help. Sorry if I wasted any time. 

You guys rock. :D

---

### Post by Hippytaff on 2011-03-16
Excellent :-)

glad you sorted it - remember to mark the thrad as solved in the thread tools at the top of the page ;-)

---

### Post by Rubi1200 on 2011-03-16
> **Ruinofthedead said:**
> Oh wow. I'm such a dork.

The original code that Rubi gave me worked. the sudo chmod a-x /usr/bin/compiz?

It worked. It just didn't give me a message when I entered my password, so I assumed it didn't do anything.

Thanks so much. I appreciate all this help. Sorry if I wasted any time. 

You guys rock. :D
Excellent, really glad it worked :-)

And, you didn't waste our time; we are all here to try and help as best we can.

---

### Post by Hippytaff on 2011-03-16
> **Rubi1200 said:**
>  you didn't waste our time; we are all here to try and help as best we can.

I second that

---


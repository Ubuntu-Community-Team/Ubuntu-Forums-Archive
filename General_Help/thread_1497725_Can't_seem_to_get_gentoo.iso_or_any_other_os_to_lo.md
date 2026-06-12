---
title: "Can't seem to get gentoo.iso or any other os to load on my laptop"
date: 2010-05-30
forum: General Help
---

### Post by pr0t3g3 on 2010-05-30
I can't seem to get gentoo, or any other os that I download to cd-r cds to load an operating system.  I've tried multiple things:

1.  right click on the .iso, and select write to disk; it works but it wont load anything not even when I restart with disk in drive.

2.  Mounting with all kinds of .iso mounting programs.

3.  I tried to drag the file to the cd folder and click burn. 


All of those work - that is they copy straight to disk without any apparent errors... but it doesn't load *anything!*


My current os is ubuntu 10.04 (lucid) running on an old dell inspiron 8600 (which works great with ubuntu)

I know there must be a solution but I can't seem to find it; what am I doing wrong?

---

### Post by cariboo on 2010-05-31
I would suggest you use Brasero to burn the iso. You don't want to burn the file to a cd.

---

### Post by pr0t3g3 on 2010-05-31
> **cariboo907 said:**
> I would suggest you use Brasero to burn the iso. You don't want to burn the file to a cd.
ok.... so what do I burn it to?

---

### Post by jocko on 2010-05-31
> **pr0t3g3 said:**
> ok.... so what do I burn it to?
To a cd...

What he meant is that you should not burn the FILE to a cd, you should use the option "burn image" in brasero (or any other cd writing program). An iso file is a copy of the entire file system that is supposed to be on the cd and does not work if you just copy the file itself to the cd.

But to me it sounds that your first problem is that you don't know how to make your computer boot from a cd. You have to go into the bios and set the boot order to boot from cd.

---

### Post by Hman242 on 2010-05-31
Open Brasero and choose Burn Image. Then select the .iso.
EDIT: Damn, beaten.

---

### Post by pr0t3g3 on 2010-05-31
> **jocko said:**
> To a cd...

What he meant is that you should not burn the FILE to a cd, you should use the option "burn image" in brasero (or any other cd writing program). An iso file is a copy of the entire file system that is supposed to be on the cd and does not work if you just copy the file itself to the cd.

But to me it sounds that your first problem is that you don't know how to make your computer boot from a cd. You have to go into the bios and set the boot order to boot from cd. ah I see... :\ I will try

either I'm incredibly dense or this is STILL not working... it doesnt have the option to 'write image to disk'... not that I see anyway


Edit: hmm never mind.. this is one of the things I did with my other ubuntu 10.04 .iso download.. it didn't work .. let's hope this one will work!

---

### Post by pr0t3g3 on 2010-05-31
> **cariboo907 said:**
> I would suggest you use Brasero to burn the iso. You don't want to burn the file to a cd.
I've burned the image of ubuntu 10.04; but when I try to load it it doesn't do anything... and yes I used brasero

I'm not sure if this is helpful or not but, I'm using a sony cd-r compact disk.... and it should have enough space as it's 700 mb

-_-; why am I not surprised... it loaded this and nothing happened..

---

### Post by jocko on 2010-05-31
Have you set your computer's bios to boot from cd?
To get into the bios setup you must press a key (different for different computers) when you see the bios splash screen (the first few seconds after you turn on the power).
Usually the bios splash screen tells you which key to press to get into setup, and some also tell you how to get a boot menu.
If you find out which key to press to get a boot menu, use that and select your cd drive, otherwise go into the bios setup and look around for the boot order settings (again, different computers have different bioses, so I can't give you any exact details where to find this). Once you find it, make sure you set it to use the cd drive before the hard drive.

---

### Post by pr0t3g3 on 2010-05-31
> **jocko said:**
> Have you set your computer's bios to boot from cd?
To get into the bios setup you must press a key (different for different computers) when you see the bios splash screen (the first few seconds after you turn on the power).
Usually the bios splash screen tells you which key to press to get into setup, and some also tell you how to get a boot menu.
If you find out which key to press to get a boot menu, use that and select your cd drive, otherwise go into the bios setup and look around for the boot order settings (again, different computers have different bioses, so I can't give you any exact details where to find this). Once you find it, make sure you set it to use the cd drive before the hard drive.ok.. did you see my last post?  take a look at it again... I uploaded a screen shot
That's a very good assessment... what DO I press to boot a bio's??

---

### Post by cariboo on 2010-05-31
On the Dell boot screen it may tell you what to press to change the boot order, if not press the key to enter the bios setup, and change the boot order there.

---

### Post by pr0t3g3 on 2010-05-31
> **cariboo907 said:**
> On the Dell boot screen it may tell you what to press to change the boot order, if not press the key to enter the bios setup, and change the boot order there.It still doesnt seem to want to let me boot from the boot screen... it doesn't give me a button... I'll just search the net to find it.

---

### Post by jocko on 2010-05-31
> **pr0t3g3 said:**
> ok.. did you see my last post?  take a look at it again... I uploaded a screen shot
That's a very good assessment... what DO I press to boot a bio's??

According to your screenshot it looks like you have burned the cd the correct way.

As I said, I can't tell you which key to press to get into the bios setup, since I don't have access to an identical computer, and I don't have your computer's manual.
You need to reboot your computer and look at the bios splash screen (this shows within the first few seconds after the computer starts to boot, and often shows the logo of your motherboard's manufacturer or whichever OEM (DELL, IBM, Lenovo ...) put your computer together. It should also tell you something similar to "press <some key> to enter setup", and if you are lucky "press <some other key> to enter boot device menu".

If the splash screen flashes by too quickly for you to read, try pressing the Pause/Break key on your keyboard to freeze it, or find your motherboard/computer manual.
The keys I have seen on different computers are Del, F2, Esc or F8 (Think an old dell used F2 for setup and F8 for boot menu).

---

### Post by pr0t3g3 on 2010-05-31
> **jocko said:**
> According to your screenshot it looks like you have burned the cd the correct way.

As I said, I can't tell you which key to press to get into the bios setup, since I don't have access to an identical computer, and I don't have your computer's manual.
You need to reboot your computer and look at the bios splash screen (this shows within the first few seconds after the computer starts to boot, and often shows the logo of your motherboard's manufacturer or whichever OEM (DELL, IBM, Lenovo ...) put your computer together. It should also tell you something similar to "press <some key> to enter setup", and if you are lucky "press <some other key> to enter boot device menu".

If the splash screen flashes by too quickly for you to read, try pressing the Pause/Break key on your keyboard to freeze it, or find your motherboard/computer manual.
The keys I have seen on different computers are Del, F2, Esc or F8 (Think an old dell used F2 for setup and F8 for boot menu).\

Doesnt seem to working; I pressed the boot button and it won't load it... it makes as though it will and just loads ubuntu... i don't understand why it's doing this... i really want this to work... help?

---

### Post by Hman242 on 2010-05-31
Turn your computer off with the Gentoo disc still in the disc drive. Power on your computer and when you manufacturer's logo shows up(Dell, HP, ASUS, etc) there should be some options at the bottom of the screen. Look for one that is similar to BIOS MENU, BOOT OPTIONS, or PRESS ESC FOR MORE OPTIONS. All of those options except the third will show the key you need to press to select that option. It should list the key to the left of said option.

If you choose the BOOT OPTIONS(or similar) option, then skip this paragraph. There should be a menu now that list several things. Look for one that says something along the lines of BOOT OPTIONS. It should say the key next to the option to select it.

Now you will use the arrow keys to select what you want to boot from. You will need to select you disc drive. After doing so, it will boot from the disc and you will go about the install.

---

### Post by pr0t3g3 on 2010-05-31
> **Hman242 said:**
> Turn your computer off with the Gentoo disc still in the disc drive. Power on your computer and when you manufacturer's logo shows up(Dell, HP, ASUS, etc) there should be some options at the bottom of the screen. Look for one that is similar to BIOS MENU, BOOT OPTIONS, or PRESS ESC FOR MORE OPTIONS. All of those options except the third will show the key you need to press to select that option. It should list the key to the left of said option.

If you choose the BOOT OPTIONS(or similar) option, then skip this paragraph. There should be a menu now that list several things. Look for one that says something along the lines of BOOT OPTIONS. It should say the key next to the option to select it.

Now you will use the arrow keys to select what you want to boot from. You will need to select you disc drive. After doing so, it will boot from the disc and you will go about the install.^_^ that's what I did... and it merely booted ubuntu.

I pressed the boot button (f12 for my dell) and then selected boot from cd/dvd etc... and then let it load.. instead of loading the install or anything like that.. it loaded ubuntu with a little disk shape on my desktop... but when I clicked it there was nothing new or special.. same as screen  shot on page 1... then I got angry and selected the options for boot one by one. a couple times it booted ubuntu like normal.. others it either crashed or said: cannot find hardware..

---

### Post by jocko on 2010-06-01
> **pr0t3g3 said:**
> ^_^ that's what I did... and it merely booted ubuntu.

I pressed the boot button (f12 for my dell) and then selected boot from cd/dvd etc... and then let it load.. instead of loading the install or anything like that.. it loaded ubuntu with a little disk shape on my desktop... but when I clicked it there was nothing new or special.. same as screen  shot on page 1... then I got angry and selected the options for boot one by one. a couple times it booted ubuntu like normal.. others it either crashed or said: cannot find hardware..
Exactly what do you get when you press F12? A simple boot menu that only gives you some options for what to boot from? If that does not work you have to go into the actual bios setup and set the boot order there.
Can't give you the specific details for your system, but in one of the sub-menus in the bios setup you should find a list of devices that your computer can boot from. You need to change it so that your cd drive comes first in that list, and your hard drive second, and then save the changes before you exit setup and reboot.

---

### Post by Hman242 on 2010-06-01
Make sure you don't choose Internal Hard Disc Drive, and choose CD/DVD ROM Drive.

---

### Post by pr0t3g3 on 2010-06-01
> **Hman242 said:**
> Make sure you don't choose Internal Hard Disc Drive, and choose CD/DVD ROM Drive.
lol... of course I'm going to choose the cd drive.... that's not the problem here... I figured out that NO disk including my official windows xp install disk will work... which is disturbing...

---

### Post by jocko on 2010-06-02
> **pr0t3g3 said:**
> lol... of course I'm going to choose the cd drive.... that's not the problem here... I figured out that NO disk including my official windows xp install disk will work... which is disturbing...
...but you still haven't said if you have managed to change the boot order in bios, or if you have only managed to get the boot device selection menu, or if you have tried both.

---

### Post by pr0t3g3 on 2010-06-02
> **jocko said:**
> ...but you still haven't said if you have managed to change the boot order in bios, or if you have only managed to get the boot device selection menu, or if you have tried both.
But I have now... and it still didn't work.. which makes me less suspicous of ubuntu trapping me and more of a problem within my own pc...

---


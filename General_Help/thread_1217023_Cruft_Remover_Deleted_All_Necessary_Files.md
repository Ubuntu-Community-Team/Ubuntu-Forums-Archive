---
title: "Cruft Remover Deleted All Necessary Files"
date: 2009-07-19
forum: General Help
---

### Post by tornupletters on 2009-07-19
I installed Intrepid Ibex a couple of months ago and yesterday I found "Cruft Remover". It said it would uninstall all unnecessary packages, so, naturally, I was all for it. Well, then my internet stopped, and everything completely stopped. I shut it down and figured it was just freezing. So, I started it back up, and it went to a DOS looking screen but it was technically the terminal. I tried using several commands, and none of them would work. /deb is gone. I don't know how to use a live cd, and I only have a usb flash drive. Can someone please, please, please help me? My entire life is/was on there. I'm about to have a panic attack.

---

### Post by earthpigg on 2009-07-19
hi,

first, the mandatory lecture. ill say it once, hopefully no one sees a need to repeat it, and we can be done with that part :D

from synaptic package manager:
> cruft is a program to look over your system for anything that shouldn't be there, but is; or for anything that should be there, but isn't.

It bases most of its results on dpkg's database, as well as a list of `extra files' that can appear during the lifetime of various packages.

***_cruft is still in pre-release_***; your assistance in improving its accuracy and performance is appreciated.

words like 'pre-release' and 'alpha stage' and 'beta stage' are simply another way of saying '*this may cause your computer to spontaneously combust*. use at your own risk.' dont use this stuff if it would bother you if your computer grew legs, ran to a cliff, and threw itself off. they are asking you to volunteer your computer as a test dummy when they say something is 'alpha' or 'beta' or 'pre-release' and offer it to you.

you probably already figured most of that out, but i want to make sure you understand exactly where your error was so you do not repeat it in the future. :D (in addition to not having backups of important data, of course).

now that that part is over:

> I don't know how to use a live cd, and I only have a usb flash drive. 

please confirm that the following is the case:
1 - your computer does _*not*_ have a cd drive at all, and you do not have an ubuntu live cd handy.
2 - your computer *does* have a USB port, and you *do* have a flash drive handy over 1 gb, but you do *_not_* have a thumb drive that is already a bootable live USB.

do you have access to a computer that does have a cd burner or cd drive with a functional operating system?

to fix this, you will need:
1) a computer with a functional operating system.
2) internet connection.
3) *either* a usb port or cd burner on that computer.

tell us what you have access to, and we will get you all sorted out and *hopefully* recover the vital data that was on your computer.

**_*do not start trying to install anything on the computer that has your important stuff on it prior to backing up the data*_**. that will be our first step, once we figure out what methods you have available.

---

### Post by tornupletters on 2009-07-20
I do have access to all of those. My computer does have a cd burner/writer. I have a live cd coming in the mail (expedited shipping, so, it should be here soon) I tried to repair the broken packages by using the menu from startup. It fixed some packages I'm guessing, but it didn't help me get back to the GUI.

---

### Post by earthpigg on 2009-07-20
you have a couple options at this point:

1) attempt to repair whatever cruft broke and fix your current install. this will get you 500 nerd points.

2) back up the data on the computer, and reinstall. since ubuntu is super easy to install, that would be the method i would choose in your position - nerd points be damned.

how we will go about achieving option 2.

1. grab a blank CD-R, and burn the ubuntu ISO of your choice at no faster than 8x. directions: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

2. boot from the live CD you just created. select 'try without making any changes', and boot to the graphical desktop from the live cd.

3. places -> computer. you will see your hard drive as "60 GB Media", or however large your hard drive is. open it and navigate to home -> your user name. you will see any documents, music, etc you have saved. for program preferences, go to view -> show hidden files..... all the folders and files you see that start with a period (.) are hidden folders/files that contain your personal settings for programs, firefox bookmarks, etc etc.

4. back up everything you see - except cruft, of course - onto an external hard drive, thumb drive, whatever you like. _verify that it made it to the external hard drive or whatever you used._

4a. do you have any software installed that is *_not_* from the ubuntu repos, and that you _*dont*_ still have a .deb of lying around? if so, we can figure out how to back that up. if you do have a .deb, or can simply download it again, then backing up that programs settings as outlined in step 4 should be enough.

5. re-install ubuntu.

6. once ubuntu is installed again, you can get your firefox settings back by copying your backed up .firefox folder into your new home folder. the same applies for all settings, configurations, etc. if you want to restore all settings for all programs you have installed, then simply copy everything from your backed up /home to your new /home. you will still need to install the software again, but once it is installed it will see the settings that you just put in /home use them instead of the defaults.



does all of that make sense?

---

### Post by tornupletters on 2009-07-22
I'll earn the nerd points later on, I suppose. I'm supposed to be getting a live cd tomorrow in the mail. Booting means that I just pop it into my cd drive and it pops up with a menu suggesting that I "try without making any changes" correct? I've never used the live cd before, so, I don't know. 

It does all make sense except for my above question haha. How do I reinstall ubuntu using the live cd? (all of my questions are about the live cd, I suppose.) Thanks for helping me so far. I hope I can get all of this worked out...

---

### Post by earthpigg on 2009-07-22
> **tornupletters said:**
> Booting means that I just pop it into my cd drive and it pops up with a menu suggesting that I "try without making any changes" correct?

correct. you may have to 'press f12 to enter setup' or something to that effect (maybe f2, maybe del... read when you turn your computer on) to set your computer to LOOK at the CD before booting from hard drive. once you are booted in the live CD environment, you will see the familiar Ubuntu desktop with all the default colors, backgrounds, etc.... and a friendly little button that says 'install', to be used _after_ you make your good solid backup that you double checked to verify contains all ur stuff.

after that, _since you have backed everything up_, it doesn't really matter what you do. installing ubuntu is pretty easy, but screwing an ubuntu install up isn't going to catch your computer on fire or steal your soul if you misread something or press the wrong button. you probably want to hit the 'use entire hard disk' option, in your case.

once you finish the install, remove the cd, and reboot... you can post the output of this command if you want someone to look it over to verify that what you did during the install makes a reasonable degree of sense, if you decided to get adventurous with manually partitioning and/or dual booting and/or a separate /home partition and/or any other option you saw that you elected not to sick with the 'default':

```
df -Th
```

---

### Post by tornupletters on 2009-07-23
thanks so much! if any more questions, I will definitely ask! :)

---

### Post by tornupletters on 2009-07-23
I did what you said, but it won't let me get my pictures, music, etc. because its all password protected. How do I sign in on the live cd?

---

### Post by earthpigg on 2009-07-23
can you be more precise? 

are you saying that, when you installed ubuntu, you chose the option to have an encrypted /home partition?

---

### Post by tornupletters on 2009-07-23
it says "The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "AutoCAD"."

---

### Post by earthpigg on 2009-07-25
give this a shot,

> sudo nautilus

---


---
title: "Noob With A Freezing Netbook"
date: 2011-06-29
forum: General Help
---

### Post by Superpeanut on 2011-06-29
Ok... I JUST made my forum account, so this is my first time doing anything on here. Actually this is some of my first time doing ANYTHING with a Linux system beyond surfing the web, using open office, and installing Skype.

So, here's what my issue is:

I have a Dell Mini Netbook, running Ubuntu 8.04 - "The Hardy Heron". Other than Skype and Chrome, I don't have any programs on my netbook that I didn't get from the "Add/Remove" program.

For a long time now, I have been having an issue with my netbook where after being on for about 5 minutes, sometimes as long as 10 minutes, the system will star to freeze up, to the point where nothing works, not even the mouse. I know it's freezing and not locking because you can move the mouse a little bit, but it is too slow to be able to do anything, and normal processes that take seconds normally, will take upwards of 5 minutes. At least.

At one point I found and ran the Ubuntu-version of Task Manager, System Monitor. I sat and watched it for the 5 minutes it took for the freeze up started happening. RIGHT as the system froze up, both of the CPU's and the RAM maxed out at the same time.


At this point, I would normally just go into Task Manager and see what shouldn't be running, and end whatever I see that I don't like, and then go delete the files for that program(s). Or at the very least, just system restore (because I ALWAYS have backups off the computer). But I don't know how to do any of that on Ubuntu.

So.... Any ideas? The netbook ran fine for almost 1 1/2years before this started happening, and at first it wasn't an issue that happened all the time. It happened every now and then, but restarting the netbook would fix it for a few days. And it slowly became an every week thing, then every day, and now every time the netbook turns on... which kinda sounds like a hardware issue, because software shouldn't change over time if there is no change put into it.

By the way, at the very least I'd like to know if there's a way to totally wipe and re-install my netbook from scratch. I don't need any of the files on it, so that's not an issue. Also I've heard that I might actually want to be using Xubuntu of I'm having a memory issue, so is there a way to replace Ubuntu altogether with this Xubuntu?

So..... ya.

---

### Post by seawolf167 on 2011-06-29
Welcome to the forums!

If you want to sit and watch it since it's only 5 minutes or so... install *htop*

```
sudo apt-get install htop
```then run it in a terminal

```
htop
```and watch the cpu usage - when it "freezes" note the program/process that is hogging all the cpu (at the top of the column) and report back. I had a computer where cups was stealing the cpu because of a bad printer driver.

You can hit 'k', then [ENTER] to kill the process selected and see if that brings it back to normal.

---

### Post by snowpine on 2011-06-29
Welcome to the forums Super Peanut!

Which model of Dell Mini do you have? I have a Mini 9 myself, nice little netbook! :)

Ubuntu 8.04 has reached its "end of life" and is no longer supported. Therefore my suggestion is it may be better use of your time to install a newer, supported version rather than try to troubleshoot an older release. 

However, if you tell me which model Dell Mini you have, I can make a more informed recommendation.

In the meantime, here are a couple of sites with excellent info on the Dell Mini:

[www.mydellmini.com](www.mydellmini.com)
[www.ubuntumini.com](www.ubuntumini.com)

---

### Post by Superpeanut on 2011-06-29
Ok, trying that htop now.

And ya, I have a dell 910. How would I go about upgrading it? is that something I would do by putting the actual install files onto a flash drive and putting them onto the netbook, or is there something on the netbook itself that allows for updating the version itself?

---

### Post by seawolf167 on 2011-06-29
My best advice for this upgrade is to do a fresh install so there aren't any problems with different package versions, etc. Copy your files/documents/folders to an external hard drive and reinstall Ubuntu 10.04 LTS, or if you prefer, a newer version. Then copy your files back to your /home directory (which I suggest to be created on it's own separate partition so this process is even easier the next time around)

---

### Post by Superpeanut on 2011-06-29
Ok, so I should go find an install file for 10.04 and run that on the netbook, or do I need to do something to wipe whats already on there?

---

### Post by seawolf167 on 2011-06-29
You can download it from [here]("http://www.ubuntu.com/download/ubuntu/download").

You don't need to "pre-wipe" anything, just ensure you have all your important documents/files saved elsewhere before you start the process.

---

### Post by snowpine on 2011-06-29
Tell us which model Dell Mini you have before you do anything drastic! Certain models are not well-supported by 10.04...

Even then, don't install right away; spend some time using the new release in "Live" mode and make sure you understand how to get wifi, graphics, sound, etc. working **before** you wipe your existing install and reinstall the new version. :)

---

### Post by Superpeanut on 2011-06-29
Btw... It looks like my netbook is using WAY too much energy to do simple things... like while running htop (which is very nice, thank you seawolf), all I have to do is move around the mouse quickly and both of the the CPU's go up to around 10 to 15%, and once the mouse stops the CPU's drop to between 0% and 4%. Opening Chrome instantly brought both to 100%.

and on that note... I'm also going to go grab that install file.

To answer snowpine, I've got a dell mini 910, that's about 2 years old now.

---

### Post by snowpine on 2011-06-29
That's good, the 910 is not one of the "problem" models. I know because it's the same model I have. :) You should be able to use either Ubuntu 10.04 (the Long-Term Support release) or 11.04 (the newest release) no problem.

You'll need to do a few "tweaks" to get wifi and possibly sound working correctly. The sites I linked to in post #3 above have good how-to's.

If you want to stick with 8.04 and troubleshoot the freezing issue, I'm afraid I can't be much help. :(

---

### Post by snowpine on 2011-06-29
One more possibility I just thought of... is it possible your disk is full? (The Minis have tiny little SSD drives...)

In the terminal (same place you opened htop) try typing:

```
df -h
```

This will tell you the status of your filesystem; you can copy & paste the output here for analysis. :)

---

### Post by Superpeanut on 2011-06-29
Alright, I've started going through how to make a USB with 11.04 on it. Although I've had no issues with 8.04 (well... beyond it not currently working...). Only reason I've stuck with it is... well, I didn't ever try to change it. I really should have been keeping up with Ubuntu more, seeing as how my netbook is running it... Oh well. Live and learn. And even if this doesn't work and it's still freezing, then I'll know it's most likely a hardware issue, not software.

---

### Post by Superpeanut on 2011-06-29
It says I'm using 64% of my space on the SSD... which sure seems like a lot for not having any personal files on the machine.

---

### Post by snowpine on 2011-06-29
> **Superpeanut said:**
> It says I'm using 64% of my space on the SSD... which sure seems like a lot for not having any personal files on the machine.

What's the total size of the SSD? Mine shows up as 7.1g and I'm using 81% of it. :)

Anyway 64% is not the reason your computer is running slow, you can cross that off the checklist. :) I've seen a few people reach 100% and then all hell breaks loose... :(

---

### Post by Superpeanut on 2011-06-29
Well from what I understand of it your computer (or at least windows computers) have the power to use some of your free hard drive space to store temp files to help out your RAM, so if you have a full drive you'll lose the power to run too much at one time.

Oh and mine's a 6.9 it says. Using 4.2, all for the normal system files.

And skype.

---

### Post by snowpine on 2011-06-29
> **Superpeanut said:**
> Well from what I understand of it your computer (or at least windows computers) have the power to use some of your free hard drive space to store temp files to help out your RAM, so if you have a full drive you'll lose the power to run too much at one time.

Oh and mine's a 6.9 it says. Using 4.2, all for the normal system files.

And skype.

What you're describing is called "virtual memory" in Windows and a "swap partition" in Linux. I personally don't have a swap partition on my Dell Mini for a variety of reasons.

Anyway, 4.2gb is totally normal, nothing to worry about. :)

---

### Post by Superpeanut on 2011-06-29
Ok, cool. I've got 11.04 going fine on my netbook now, thanks.

Only question I have left is....

Where in the world is the main menu? I'm using it with the default Unity desktop right now, and I've found where to edit the main menu... But I can't find the menu itself. Does it not actually show up in Unity? Or am I missing it somewhere?

Edit-

Ok, what I'm looking for is the Classic Menu. Is there a simple way to add that to my sidebar, or the menu bar?

---

### Post by snowpine on 2011-06-29
> **Superpeanut said:**
> Ok, cool. I've got 11.04 going fine on my netbook now, thanks.

Only question I have left is....

Where in the world is the main menu? I'm using it with the default Unity desktop right now, and I've found where to edit the main menu... But I can't find the menu itself. Does it not actually show up in Unity? Or am I missing it somewhere?

Edit-

Ok, what I'm looking for is the Classic Menu. Is there a simple way to add that to my sidebar, or the menu bar?

Unity is a little different, it's true. :) 

Easiest way to get a "menu" I've found is just hit the Windows key and start typing the name of the app you're looking for, it is actually a very quick and efficient way to find something.

Alternately, you can log out and choose "Classic Gnome" from the login screen if you prefer. :)

---

### Post by Superpeanut on 2011-06-29
Alrighty, thanks. I'll just use that then instead of trying to get a whole new app just for a menu... now.. to go uncheck the Sync to VBlank option so to get rid of my screensaver of death that I luckily got to find out about the very first time I ever went into screen saver..

---

### Post by JC Cheloven on 2011-06-29
Oops, I come late to what could be my favourite thread of the week :)
I really love my two dell mini9 netbooks with solid disk. I bought one of them with ubuntu preinstalled. I'm afraid people didn't understand the concept of this nice machine.

ALthough I have little to add so far to snowpine's excellent advice, please note that a bug in latest ubuntu versions prevents to load the driver for the wireless card (I mean the broadcom BCM4312). If you can't use the wireless, simply use a wired connection once and instal the missing package:

```
sudo apt-get install bcmwl-kernel-source
```

Also a personal note after having spent some time lately trying out 11.04: I find the "normal" ubuntu version a bit too heavy. I'm intensively trying LUbuntu now (the lighter version of Ubuntu), and I'm much more satisfied.

Best
JC

---

### Post by Superpeanut on 2011-06-29
Well so far the Wireless works fine... Which is kinda funny because I had lost (somehow) the wireless about two days ago when I was running 8.04. And now it's running quite nicely, it actually connects faster than it used to.

What are the differences between 11.04 and Lubuntu? Is it something I should look into before I get settled into this version? It is true that as much as I love the netbook, it's not what you would call the most powerful machine... Although granted, it's not supposed to be. Works great for school though. I can bike to campus with is in my backpack without really weighing me down.

---

### Post by Superpeanut on 2011-06-29
Oops double post

---

### Post by JC Cheloven on 2011-06-29
Glad your wl worked out of the box. Probably yours don't have the same card as mine (you can check out with lspci at terminal).

LUbuntu follows the same version scheme as the other ubuntu flavours (KUbuntu, XUbuntu). All have a version 11.04, a version 10.10, etc. The important bit is that each version has its repository, which is shared by all flavours.

LUbuntu it's not yet an official flavour, but it's supposed to be since next version 11.10. It is based on LXDE, the "light x desktop environment", and it's the lighter ubuntu. I'd seriously consider it for the mini9 (as for the 11.04 times). It also will leave some more disk space for your own use.

---

### Post by Superpeanut on 2011-06-29
Alright, cool thanks. I'll look into before I start messing with 11.04 too much.

---


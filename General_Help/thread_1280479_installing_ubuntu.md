---
title: "installing ubuntu"
date: 2009-10-02
forum: General Help
---

### Post by sal2944 on 2009-10-02
im new to ubuntu. i overheard some guys in my computer class talk about it and decided to download and install 9.04. the installation sites say its easy to download on a windows XP system. when i run ubuntu, the bootscreen stalls for awhile then a screen pops up saying STARTING.......     [ok], then it stops when it gets to "Starting Bluetooth.........". the cursor just blinks. i don't know where to go from there. the screen stalls there. do i need to install an older version?

---

### Post by yeats on 2009-10-02
> **sal2944 said:**
> im new to ubuntu. i overheard some guys in my computer class talk about it and decided to download and install 9.04. the installation sites say its easy to download on a windows XP system. when i run ubuntu, the bootscreen stalls for awhile then a screen pops up saying STARTING.......     [ok], then it stops when it gets to "Starting Bluetooth.........". the cursor just blinks. i don't know where to go from there. the screen stalls there. do i need to install an older version?

Hi and welcome.  You'll need to post a little more about your computer (brand, memory, HD space, processor type) before anyone can recommend a specific solution.  If it's an older or low-memory computer that may explain some of what you're seeing.  There may be file corruption somewhere along the way, too.

Anyway, can you give us a little more to go on?

---

### Post by sal2944 on 2009-10-02
sorry about that. my computer dosen't have a brand, i built it back in 2005. it has a pentuim 4 @ 3.4 GHz, 1 GB Ram, and 150 GB hdd w/ 82 GB free. i thinking i might have to run an older version.

---

### Post by oldfred on 2009-10-02
Your computer specs should be fine. I did get Ubuntu to install on a old portable with only 125k and 6GB HD. It took hours to install and barely ran. I converted to a lightweight distro. Minimum specs now are 256k and it needs a minimum of 4GB but every says the real size should be 10GB to install.

Did you run it as a live CD and check that everything seemed to work ok?

Did you install Wubi or to a partition?

---

### Post by sabre2th on 2009-10-02
If you're able, you can try downloading the ISO again and burning it at 1x (or whatever the slowest speed your burner is capable of).  People generally recommend that you burn your OS CDs at as slow a speed as possible to reduce the chances of errors.  I've run into some goofy problems because of that.

As far as Ubuntu versions... the latest should always work fine, as long as your hardware can handle the load.  I believe Ubuntu has been reported to be capable of running even on old 486 machines and similar.  It should run nicely on your computer.

---

### Post by MonsterDuc on 2009-10-02
I was running into issues as well yesterday, although not with bluetooth.  I burned 3 copies of the iso before I gave up (md5sum all checked out fine and I used different CDs and burners).
Then I downloaded the alternative iso and everything worked fine during install.

---

### Post by jward3010 on 2009-10-02
When you boot off the disk the first menu you'll see is the "Ubuntu" menu with "Try on a computer", "Install Ubuntu" etc. options. You'll notice F6 does special functions. Hit it but don't select any of the options, after you hit F6 simply press ESC and you'll notice the kernel line at the bootom of the screen, it should end with "...splash quiet --" or something. Remove the "splash" and "quiet" and hit enter.

You will boot into a verbose mode (that means you'll see all the info of whats going on, the kernel loading, detecting hardware etc.) and you might notice errors here. If you do report them back here.

---

### Post by sal2944 on 2009-10-05
ok i used wubi and i bought a ubuntu magazine that had the 32 bit version of 9.04 that i installed and it all did the same thing. when i boot from the disk a screen comes up asking to install. so i highlight install ubuntu and press [enter] on install and an ubuntu screen appears with a cursor like line going back in forth. then it starts loading. about an eight of the way it my computer starts making a noise like a helicopter. i wait until it goes out and it loads with the line going across the bar. then a black screen that says "loading........[ok]", "starting.........[ok]" fills the screen. at the bottom of the screen it stops at "starting bluetooth.........._" with the cursor blinking. it just stops there and i can't do anything. i can type stuff but i can't go back to the previous line after i press return. the magazine says its easy to install but i'm here trying to figure out whats going on.

---

### Post by jward3010 on 2009-10-05
> **sal2944 said:**
> when i boot from the disk a screen comes up asking to install. so i highlight install ubuntu and press [enter]
This is where you should stop, when you're on this menu screen hit F6, you'll see a little menu appear mentioning things like "acpioff", "Expert Mode" etc. Hit ESC to clear it. Just above the bottom "F" options you'll notice a long line of text has appeared (this line only appears when you hit F6). It should end with:
```
... splash quiet --
```
Hit backspace until all that stuff is gone and then hit enter. This will boot you into verbose boot where everything the kernel is doing is being displayed to you including errors you might be facing.

---

### Post by sal2944 on 2009-10-06
I tried that with and alternate version and also installed another harddrive to install it on and i got it to install but when it ask me to reboot after installation i rebooted the ubuntu and it did the same thing. i left the computer on all night hoping it would boot but nothing. said some thing about "timed out"

---

### Post by jward3010 on 2009-10-07
Same thing again, when Computer starts up press ESC to edit boot options. In the first option in the menu hit "e" to edit. At the end of the kernel line remove "splash quiet" and watch out for errors as kernel boots. Later I'll try and get a dmesg off you in some way.

---

### Post by sal2944 on 2009-10-07
its telling me "phy0:  device not found". 
"info: task hid2hci:4371 blocked for more than 120 seconds"
""echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message"
i'm reinstalling because i installed "alt" version which i installed on a 2nd drive. it was doing the same thing when i booted so i decided to format the hard drive when i was in windows. i rebooted the computer now i have a grub error 17. i went into bios and set it up to where the second drive was not found. i rebooted, now have an error 21. i'm thinking of giving up on ubuntu. i just need to get into my windows to gets some files and reinstall windows

---

### Post by sal2944 on 2009-10-08
I finally got it to boot. I'm on this site using Mozilla Firefox on Ubuntu. Thanks for the help. I talked to a guy in my class. He had the same problem on his laptop. He said all he did was plug in his ethernet cable into his laptop and booted into Ubuntu. The computer I have connects to the internet wirelessly. I guess that was what I forgot to mention. I plugged in the ethernet from my router and to my amazement it worked. I put in my user name and password and got on. Now I have to figure out how to display on dual monitors.

---

### Post by jward3010 on 2009-10-08
Ah, so now you're getting brave already. Well done getting there. 

The experience you have with Ubuntu is not a common one. I work in IT and a huge amount of different laptops and PC's pass by me, 90% work straight off with Ubuntu (I try almost each one), I mean completely usable units within 3 minutes of powering the machine on. It's a miracle in some ways. Another 45 minutes will yield me with a fully installed machine, updated and relevant codecs and software in place and usually every piece of hardware working. Finished. 

Beat that Vista, XP, whatever else takes an entire day to get set up the way you want and more.

---


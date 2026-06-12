---
title: "Ubuntu 10.04 TLS"
date: 2011-11-21
forum: General Help
---

### Post by Mattish on 2011-11-21
Hi, i saw this was a common problem (kind of) My screen is just blank blinking in black, but id cant see any cursor. It all started with my sudo su + su that did not work in any way, i solved that problem by using my live usb and changed permissions to 0444 or something like that, (solved sudo su + su problem everything was fine at first start) then i installed some updates and now as i described above.

the only command that do works is Ctrl+Alt+Del. I still can edit everything from live usb. (I cant re install my computer since i got 1,5 TB important files.) Please help me!

Is is possible to update to 10.10 with live usb? i cant risk to drop all my files. that's the only backup and can't afford to buy a new drive since prices went up. :cry:

---

### Post by snowpine on 2011-11-21
Welcome to the forums!

1. **Back up** your important files to an external drive. No sane forum member is going to recommend that you skip this step. :)
2. "sudo su + su" is not a recommended or supported command, [read here for more info]("https://help.ubuntu.com/community/RootSudo"). 
3. Which files exactly did you change the permission of? File permissions are a complex topic, each file and folder must have the correct permissions for your Linux system to operate correctly. If you have really changed your permissions to 0444 system-wide then everything is now read-only and probably ruined.
4. I would recommend a full reinstall of Ubuntu after you've completed Step 1.

---

### Post by Mattish on 2011-11-21
[FONT=Verdana]> **snowpine said:**
> Welcome to the forums!

1. [/FONT] [FONT=Verdana]**Back up** your important files to an external drive. No sane forum member is going to recommend that you skip this step. :)
2. "sudo su + su" is not a recommended or supported command, [read here for more info]("https://help.ubuntu.com/community/RootSudo"). 
3. Which files exactly did you change the permission of? File permissions are a complex topic, each file and folder must have the correct permissions for your Linux system to operate correctly. If you have really changed your permissions to 0444 system-wide then everything is now read-only and probably ruined.
4. I would recommend a full reinstall of Ubuntu after you've completed Step 1.
  The thing is that i don't have a external drive and the prices in Sweden are to hig for me to buy one, i rather drop all my files and start over than buy a hdd... 

# sudo su - was not working
#su
Password: - When i enter the correct password it gives me
[/FONT][FONT=Verdana]Authentication failure

so i read on a forum that it was a permission problem as the words "Authentication failure" tells me as well.
And that 04XX something don't remember exactly should solve my problem and it did
[/FONT][FONT=Verdana]The only file is changed permission for was "/usr/bin/sudo" [/FONT]

---

### Post by asifnaz on 2011-11-21
are you using a wubi installation ..?

---

### Post by snowpine on 2011-11-21
> **Mattish said:**
> it was a permission problem as the words "Authentication failure" tells me as well.
And that 04XX something don't remember exactly should solve my problem and it did
[/FONT][FONT=Verdana]The only file is changed permission for was "/usr/bin/sudo" [/FONT]

Excellent, be sure to mark your thread as (solved) and welcome to the forums! :)

---

### Post by Mattish on 2011-11-21
Now i dropped all my files and have a fresh install of ubuntu 10.04 and the problem resists, what can i do? hardware related? :S

---

### Post by Mattish on 2011-11-21
when i changed my permissions it only worked for one start not more... problem is still not solved...

---

### Post by snowpine on 2011-11-21
> **Mattish said:**
> when i changed my permissions it only worked for one start not more... problem is still not solved...

There is no reason to change the permissions of /etc/sudoers. I highly recommend against changing permissions of system files! 

As far as I can tell, the only "problem" is that you are using the garbage command "sudo su + su" instead of [reading the instructions]("https://help.ubuntu.com/community/RootSudo").

---

### Post by Mattish on 2011-11-21
> **snowpine said:**
> There is no reason to change the permissions of /etc/sudoers. I highly recommend against changing permissions of system files! 

As far as I can tell, the only "problem" is that you are using the garbage command "sudo su + su" instead of [reading the instructions]("https://help.ubuntu.com/community/RootSudo").

no, i used "sudo su" to install a lot of things and was tired of witing sudo before everything, so i used sudo su, it worked flawless then it just stopped working, all of a sudden. and after the problem occurred i didn't change any permissions, i just installed stuf such as php5, apache, and some other stuff. then when i installed updates, the update manager wanted me to reboot so i did, turned out it was not such a good idea, it was after restart sudo stopped working, so i read on some forum some were that it was this permission problem that was able to be solved thru live cd/usb and turned out that their guide was working just fine, sudo was working again and then i turned of the computer. The next day it went black screen to screen of and so on... Now i re-installed with 10.04 same as before and problem turns out on first boot, i have checked that the screen is working, thru my laptop. and tried to change screen on the ubuntu pc same problems there (CRT screen, if any help.)

I would never change system files unless i do have problems with it, which i have.

---

### Post by snowpine on 2011-11-21
"sudo su" is not recommended or supported on these forums. If you insist on not following the instructions, and you break your system, nothing I can do to help. Sorry. :(

ps It sounds like you may also be having a video driver problem. I'd suggest starting a new thread with details such as your video card manufacturer and model number.

---


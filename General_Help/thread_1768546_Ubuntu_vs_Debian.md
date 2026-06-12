---
title: "Ubuntu vs Debian"
date: 2011-05-26
forum: General Help
---

### Post by .psd on 2011-05-26
Grew up on Windows since 3.1. Been trying GNU/Linux (Ubuntu 11.04) for 1 week. I like it and have decided to dedicate a machine to GNU/Linux.

I'm looking to set up a desktop home computer with the following:

- Ideally: root account only, none others, no login or passwords ever. Else, the most freedom physically possible to do whatever I want whenever I want. I'm aware of the dangers and consequences.
- Lightweight, everything I need, nothing I don't (not barebones, I still need the basics like firefox, flash, media player, text editor, calculator etc etc, no extras like a calendar app, messaging apps and so on)
- Easy to install
- Stable

I've decided to go with Debian 6, or Ubuntu 10 or 11. I'm leaning toward Debian 6 but am afraid it may not be as easy to install as Ubuntu (With Ubuntu the first time I only needed to activate a proprietary driver and place the libflashthingy into a protected folder, though I had to do neither the second time). So that puts Ubuntu back on the table, except I don't want all the bloat (what I consider bloat) like Unity, an office suite, ubuntu one, evolution etc etc etc

What are your feelings on the matter, advice to somewhat of a new convert, and what would you do or be thinking about if you were in my shoes. Also feel free to provide helpful links for the complete newb.

---

### Post by idoitprone on 2011-05-26
> **.psd said:**
> 

- Ideally: root account only, none others, no login or passwords ever. Else, the most freedom physically possible to do whatever I want whenever I want. I'm aware of the dangers and consequences.


It is one thing you are offline, it is another thing if you are. The problem with circumventing linux permissions is that you browser can mess up the system with out you know it. Programs such as chromium would not allow you to start the browser as root. Also, if you want a dedicated root account, Ubuntu is not your choice; Ubuntu disable root on default. One more thing, you can edit your display manager to auto login

Windows stop allowing admin account with complete unsupervised control ever since Vista UAC.

---

### Post by spcwingo on 2011-05-26
Puppy (based on Ubuntu 10.04) is set up out of the box with single user (root) only.  It is what I started Linux on.  It kind of broke me in to the idea of Linux without "locked-down" security.  If you decide to go with Puppy, after a while you will know why it's not recommended to run this way (accidentally deleting files that was really needed by the system, etc.).  Not to dog Puppy (pun not intended) as it is a fantastic lite distro.  Good luck with whatever you decide to go with.

---

### Post by dFlyer on 2011-05-27
> **.psd said:**
> Grew up on Windows since 3.1. Been trying GNU/Linux (Ubuntu 11.04) for 1 week. I like it and have decided to dedicate a machine to GNU/Linux.

I'm looking to set up a desktop home computer with the following:

- Ideally: root account only, none others, no login or passwords ever. Else, the most freedom physically possible to do whatever I want whenever I want. I'm aware of the dangers and consequences.
- Lightweight, everything I need, nothing I don't (not barebones, I still need the basics like firefox, flash, media player, text editor, calculator etc etc, no extras like a calendar app, messaging apps and so on)
- Easy to install
- Stable

I've decided to go with Debian 6, or Ubuntu 10 or 11. I'm leaning toward Debian 6 but am afraid it may not be as easy to install as Ubuntu (With Ubuntu the first time I only needed to activate a proprietary driver and place the libflashthingy into a protected folder, though I had to do neither the second time). So that puts Ubuntu back on the table, except I don't want all the bloat (what I consider bloat) like Unity, an office suite, ubuntu one, evolution etc etc etc

What are your feelings on the matter, advice to somewhat of a new convert, and what would you do or be thinking about if you were in my shoes. Also feel free to provide helpful links for the complete newb.

I haven't used debian since version 3.1. I really like it over all the other linux distro I used. The main problem back then was working around proprietary drivers. Don't know if that still applies today. When I moved to ubuntu at 6.06, I've never looked back to any other distro. I do have a desktop that I play around with other distro, but that has no proprietary drivers.

What ever you decide to do remember to have fun and take it slow. When problems do come up just ask for help.

---

### Post by oldfred on 2011-05-27
How big is your hard drive? You can install both and the only price is time.

The price of testing is about an hour of install time and as long as you want to try it to learn about it. I have several installs of Ubuntu in 20-25GB partitions with my data (not /home) in other partitions.

---

### Post by 4Orbs on 2011-05-27
Xubuntu 10.10, then remove the few things that you consider bloat. Debian may be lighter, but Xubuntu will treat you like a king (or queen).

Trust me. And don't upgrade to 11.04 for a good while.

---

### Post by .psd on 2011-05-27
This community seems unique in the tendency to recommend alternative solutions. While I understand you guys are clever, and I appreciate all relevant info, please at least offer an on-topic answer in addition to the various off-topic opinions. I thought I worded the OP well, I guess I'm looking more for comments on a more specific matter. Please check out the OP again! Thanks in advance! :D

---

### Post by 4Orbs on 2011-05-27
O.K. Point by point:
Root account only - This (in my humble opinion) becomes irrelevant once you understand how to use sudo or gksudo in the terminal. You'll quickly realize that you don't save time or frustration by having root-only usage. And you can set your account (from the users and groups settings) to login without password.

Bloat - Other than a few unwanted applications and services (for example, Bluetooth and IM clients); any fat in Xubuntu serves to improve usability and convenience for you.

Easy Install - Xubuntu takes about 15 minutes to install on my machine. Another hour or two to tweak and get the proprietary driver, multimedia, flash, java, etc. all working perfectly or nearly so. Just follow the [Comprehensive Multimedia How-to]("http://ubuntuforums.org/showthread.php?t=766683") on these forums.

I'm not bashing Debian... it's just not as user-friendly as X/K/Ubuntu (for example; Debian says - Warning! You are not on the sudoers list. This incident will be reported!) Who needs that sort of threat when you are the owner and only user of your computer.

---

### Post by linuxinstalledfromhdd on 2011-05-27
> **.psd said:**
> Grew up on Windows since 3.1. Been trying GNU/Linux (Ubuntu 11.04) for 1 week. I like it and have decided to dedicate a machine to GNU/Linux.

I'm looking to set up a desktop home computer with the following:

- Ideally: root account only, none others, no login or passwords ever. Else, the most freedom physically possible to do whatever I want whenever I want. I'm aware of the dangers and consequences.
- Lightweight, everything I need, nothing I don't (not barebones, I still need the basics like firefox, flash, media player, text editor, calculator etc etc, no extras like a calendar app, messaging apps and so on)
- Easy to install
- Stable

I've decided to go with Debian 6, or Ubuntu 10 or 11. I'm leaning toward Debian 6 but am afraid it may not be as easy to install as Ubuntu (With Ubuntu the first time I only needed to activate a proprietary driver and place the libflashthingy into a protected folder, though I had to do neither the second time). So that puts Ubuntu back on the table, except I don't want all the bloat (what I consider bloat) like Unity, an office suite, ubuntu one, evolution etc etc etc

What are your feelings on the matter, advice to somewhat of a new convert, and what would you do or be thinking about if you were in my shoes. Also feel free to provide helpful links for the complete newb.

Honestly, I'm not going to try to dissuade you from trying out Debian, since that is where Ubuntu originally came from. You sound like you want a Debian disto that has most of the basics pre-installed, or relatively easy to install yourself, once you have a base system up-and-running.  So my recommendation is the one that I use other than Ubuntu, and that is Crunchbang Statler XFCE. It's pure Debian. It has the basics. And they have a forum help area that is very straight forward, and a very "no nonsense" kind of support group.  If you act arrogant at all with them, or rude with them, they probably will refuse to help you and you will have to hire someone to help you.

Now onto your other question..  As for running a system as a super user, you should post that question to Crunchbang forums, and after you have it running, they can walk you through the process exactly, because that is something they would need to help you with, not Ubuntu forums. Sorry.

If you have any questions about Debian in general, I'm happy to help, but you would be better off posting to a support group that deals with Debian specifically.  Crunchbang is a very lite and tidy OS.  I'm sure it will suit your needs terrifically.

---

### Post by Ozymandias_117 on 2011-05-27
Just a few things to consider:

1. (Root account only) One thing you can do if you want to be inbetween running only on a root account, and having to enter your password alot, you can modify your sudoers file so that sudo doesn't ask you to verify your password. (Please note I've never actually DONE this, so I'm not certain how programs calling gksudo would work, I just know that sudo can be set up that way)

2-3. Of all the great things Ubuntu has going for it, lightweight is NOT one of them.  Debian is better, but if you install the Gnome package, it will still come with some bloat.  Honestly, this just depends on how much of a learning curve you want; if you go with Ubuntu, you'll have bloat but it won't take much work. Debian has less bloat, but it also does less hand holding. Really, either one of these distros shouldn't be too hard to get up and running in a reasonable amount of time.

4. Debian is more stable than Ubuntu, but it's also much less up to date (Well, if you're running Stable).  If you run Debian testing, it's as up to date as Ubuntu and seems about the same in stability.

---

### Post by .psd on 2011-05-27
root aside, how can I install 11.04 minus unity, banshee, ubuntu one, evolution, and a few others. The minimal install cd isn't an option because it's way too complicated and I'm completely n00b. One of the main deciding factors is ease of install and use (hence always root) because I don't have lots of time to invest in learning.

---

### Post by linuxinstalledfromhdd on 2011-05-27
You can uninstall any program you don't want from the Ubuntu Software Center.

---

### Post by .psd on 2011-05-27
> **linuxinstalledfromhdd said:**
> You can uninstall any program you don't want from the Ubuntu Software Center.
And break half the system... I'd prefer to do it as clean as possible from the start (do it right the first time, that's how I was raised), plus I'm fresh installing anyways and trying to gather info beforehand to make it all go smoothly.

---

### Post by linuxinstalledfromhdd on 2011-05-27
No, you won't break your system by uninstalling software from the Ubuntu Software Manager.  If you tried that with Synaptic Package Manager then yes you would break your system probably, if you aren't careful about what you are removing. 

Make sure you are in Classic Gnome, if you are going to remove Unity. 

I'm going to tell you right now too, you aren't going to have a thin system by just removing software like you would if you use a minimal installation disc or alternative installation disc and install a system from the command line. I don't want to mislead you into believing that your system will be "thin" just by removing a few applications or the Unity environment.  A truly thin system would be something like Crunchbang or Madbox or "thin" specific distro.

---

### Post by .psd on 2011-05-27
Fair enough, but I'm not necessarily trying to get the lightest system possible, just the lightest Ubuntu or Debian that's also new. How would I (as certified newb) go about installing 11.04 from an install disc (iso or whatever) with all its awesome automation and everything working OOTB, but without these programs or any of their dependencies or anything having to do with them that isn't system-critical.

unity (newest stable gnome instead)
libreoffice
tomboy notes
transmission
games
ubuntu one
empathy
onboard
banshee
printing
gwibbler
orca magnifier
movie player
[ no banshee or movie player assumes VLC can handle both, otherwise rhythmbox and keep movie player ]
simple scan
sound recorder
evolution
pitivi

---

### Post by linuxinstalledfromhdd on 2011-05-27
Use your existing installation, and run this command from terminal:

sudo apt-get remove <nameofpackage> 

Or you can open up Ubuntu Software Center and search for each title and remove them that way. 

If you want to reinstall your entire system to remove these packages, that's what you will need to do first before removing any software.  :)

---


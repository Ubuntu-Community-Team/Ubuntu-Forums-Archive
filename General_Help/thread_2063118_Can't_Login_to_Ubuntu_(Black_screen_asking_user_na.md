---
title: "Can't Login to Ubuntu (Black screen asking user name and password)"
date: 2012-09-26
forum: General Help
---

### Post by PrinceNo1 on 2012-09-26
This happened after i installed the latest updates (from update manager)  yesterday. I don't remember installing anything else than that. I use dual boot with windows home premium x64 + Ubuntu 12.04 with gnome 3.4 desktop environment. I installed gnome last week and i was enjoying the best experience i really ever had in linux with this set up. When i try to load Ubuntu, it shows standard Ubuntu loading screen and then a black command prompt comes up (with my computer's name and something like 'tty1' at the end) asking me my user name and password. I enter my user name and pass but it never accepts. always prompts 'wrong user name/pass'. What's wrong? how can i save my ubuntu?

---

### Post by danaross on 2012-09-26
This happened to me too last night. I was able to enter my user name and password but I had no way to continue. I typed in Firefox and got back something saying the the x driver wasn't loaded or something like that. Same thing when I typed in Unity and Chrome and Grub and Grub2.

I hope someone has a solution.

---

### Post by danaross on 2012-09-26
This happened to me too last night. I was able to enter my user name and password but I had no way to continue. I typed in Firefox and got back something saying the the x driver wasn't loaded or something like that. Same thing when I typed in Unity and Chrome and Grub and Grub2.

I hope someone has a solution.

---

### Post by PrinceNo1 on 2012-09-26
i wonder if there is something like 'auto system recovery'. Should i re-install using the CD or anyone has a work-around about this?

---

### Post by PrinceNo1 on 2012-09-26
ok now i can login in that black screen (capital letter issues oh yea my bad) but now it still asks me to enter a command. I entered "startx" and it says "stopping this, checking that etc" and just halts in that screen without any error messages at all. Waited a couple of minutes and nothing happens

edit: i started the computer with boot repair disk and it created a detailed report here: [http://paste.debian.net/193325/](http://paste.debian.net/193325/)

---

### Post by stepking2 on 2012-09-26
The same thing happened to me also, but the wierd thing is that I can't use any of the other kernels too. It's just shows a wizard to detect displays and then it trys to start x, but just hangs on stopping that, starting that process.

---

### Post by steeldriver on 2012-09-26
what graphics cards do you all have? maybe a recent driver upgrade broke something? do you see anything in /var/log/Xorg.0.log

```
tail  /var/log/Xorg.0.log
```or

```
grep '(EE)'  /var/log/Xorg.0.log
```

---

### Post by PrinceNo1 on 2012-09-26
I am on a laptop which has a AMD 5650M graphics card. Last week i uninstalled the default graphics driver and installed 12.8 driver with Catalyst Control Centre but i had absolutely zero issues about that. I was really enjoying my Gnome 3.I'm pretty certain that this issue happened after my update yesterday

---

### Post by PrinceNo1 on 2012-09-26
steeldriver thank you for the response. 
That command begining with "tail" returned "AMD FireGL Kernel Module" and some more information i don't remember.
And the command begining with "grep" returned something like: [COLOR=Red](EE)[/COLOR], NI (not implemented)

EE was in red color. 

Also is there any possibility to save these messages or the screen so i can share here?

---

### Post by lemonoid on 2012-09-26
I've had this happened to me, right when I upgraded to 12.04, on my initial reboot. I would love to see a way to fix this, if you fix it, because I was told that it could have been a corrupt download or installation of the upgrade files, and I ended up re-downloading and installing Ubuntu. You need your  xdriver working properly to be able to open windows and view windows, not to mention your desktop for the most part. I will keep a watch on this, and if I come across anything I'll let you know.

---

### Post by steeldriver on 2012-09-26
> **PrinceNo1 said:**
> steeldriver thank you for the response. 
That command begining with "tail" returned "AMD FireGL Kernel Module" and some more information i don't remember.
And the command begining with "grep" returned something like: [COLOR=Red](EE)[/COLOR], NI (not implemented)

EE was in red color. 

Also is there any possibility to save these messages or the screen so i can share here?

you can redirect the output to a file e.g.

```
grep '(EE)'  /var/log/Xorg.0.log > file.txt
```however based on what you already posted I don't think there's anything of note (you are just seeing the Xorg log header line - no actual errors)

If you installed the ATI 12.8 driver from a downloaded .run file and you still have it accessible (in your home dir or wherever) then I would be tempted to try re-running that as a first shot

---

### Post by HiImTye on 2012-09-27
I would give this a try. either
```
sudo aticonfig --initial
```or 
```
sudo amdconfig --initial
```
and then reboot

if that doesn't work then try reinstalling the driver:
```
sudo apt-get purge fglrx fglrx-amdcccle; sudo apt-get install fglrx fglrx-amdcccle
```
and then reboot

---

### Post by @nne on 2012-09-27
Same problem here too. I'm running [Ubuntu Quantal Quetzal Gnome Shell remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10Alpha2"). Yesterday's updates installed the very last version of Gnome-shell, the 3.6.0, and today I have a black screen. The cursor whirls and nothing happens.

I can access to the tty, so I uninstalled gnome-shell 3.6 but nothing changed, so I put the package back.

I'm not using proprietary drivers for my devices. I wish the devs are reading this forum... :)

---

### Post by PrinceNo1 on 2012-09-27
I unnstalled gdm and gnome using the commands (thinking these can be the problem)
```
sudo apt-get autoremove gdm
```and 
```
sudo apt-get autoremove gnome
```then installed them again. and then tried startx and it locked up again so now i screwed up badly cause i no longer see even the command screen during login any more :) it just locks up at the ubuntu loading screen. Oh well, i think it is time for a fresh install

edit: for some reason i didn't see the last 3 messages even though i refreshed the page several times. Ok thank you again steeldriver, i will give it a try after [HiImTye]("http://ubuntuforums.org/member.php?u=843901")'s method. And [HiImTye]("http://ubuntuforums.org/member.php?u=843901") thank you, too. I'll write back here what result i get

---

### Post by PrinceNo1 on 2012-09-27
aticonfig command worked but didn't solve the issue. re-installing the driver did not work cause it says that driver is not installed. 
Steeldriver i suppose i got that run file somewhere but i guess it is easier to just download and install 12.8 driver over the net. How to do that?

---

### Post by steeldriver on 2012-09-27
I'm leery of advising you to go that route because I've had my own share of troubles with direct installs of the proprietary drivers - maybe HilmTye's method would work if you manually uninstalled the 12.8 first?

IIRC there are 2 modes to run the AMD/ATI proprietary installer - there's a 'package install' where you run it to create a deb file and the use dpkg to install that. In that case the system should know about the driver and HilmTye's method should have worked as-is

However if you just ran the installer with no arguments it does its own thing (hence the system thinks fglrx is not installed) - however I think it puts an uninstaller script somewhere in /etc/ati that you can run and THEN try to install the repo version of fglrx, i.e.

```
sudo /etc/ati/uninstall.sh  # <--- may not be what it's actually called

sudo apt-get install fglrx fglrx-amdcccle
```If you *really* want to go ahead and re-install the 12.8 proprietary version then you can probably wget it from the website, i.e.

```
wget http://www2.ati.com/drivers/linux/amd-driver-installer-12-8-x86.x86_64.zip
```Good luck

---

### Post by PrinceNo1 on 2012-09-27
Ok thanks much. I realise it is much better to make a clean install cause even if i recover my system this way, it won't give any confidence :)

---

### Post by @nne on 2012-09-28
I solved my problem by uninstalling and re-installing update-manager. The problem was that the manager hadn't completely updated the system. After an apt-get update and an apt-get upgrade, I was able to boot normally.

Someone else solved his problem by using apt-get update and apt-get upgrade only. Sorry, I should have posted this before but I forgot...

---

### Post by PrinceNo1 on 2012-09-29
> **@nne said:**
> I solved my problem by uninstalling and re-installing update-manager. The problem was that the manager hadn't completely updated the system. After an apt-get update and an apt-get upgrade, I was able to boot normally.

Someone else solved his problem by using apt-get update and apt-get upgrade only. Sorry, I should have posted this before but I forgot...
how do you uninstall and reinstall the update manager?

---

### Post by @nne on 2012-09-30
> **PrinceNo1 said:**
> how do you uninstall and reinstall the update manager?
When you have the black screen, push Ctrl+Alt+F1; it will get you to a tty, a console. Login. If you have figures in your password, don't use the num keypad, it won't work, use shift+#. Once you're logged in, you can use the normal way to install and remove any package :

```
sudo apt-get remove --purge update-manager

sudo apt-get install update-manager
```

Before doing this, I suggest that you try:

```
sudo apt-get update
```

and 

```
sudo apt-get upgrade
```

and install the upgrades if you get some. :)

---

### Post by danaross on 2012-09-30
Thank you for this. I did already do a live boot and reinstall my system. I like your solution better though. To do it you would have to plug in to ethernet for internet access.

---


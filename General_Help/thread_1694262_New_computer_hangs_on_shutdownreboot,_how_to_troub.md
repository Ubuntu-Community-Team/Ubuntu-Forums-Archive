---
title: "New computer hangs on shutdown/reboot, how to troubleshoot?"
date: 2011-02-24
forum: General Help
---

### Post by torbengb on 2011-02-24
I have bought a new desktop; it's an Acer Revo R3700 nettop with Intel D525 CPU and Nvidia ION2 GPU. I've just installed 10.10 32-bit desktop edition. **The system is working perfectly but it freezes during shutdown/reboot/suspend/hibernate**: 

All windows and the menu bar disappear but the desktop wallpaper remains. It doesn't even show the shutdown screen (the one with the animated dots) where I could hit ESC and watch the shutdown console output. The system is fully updated using Update Manager. 

[LIST]
[*]How can I determine what is causing the freeze? 
[*]Is there a log I can investigate? 
[*]How can I fix this?
[/LIST]
I see no obvious cause of the freeze. The only USB attachment is a mouse/keyboard; I don't have any external storage attached; and I don't have any programs running (the machine freezes even when doing shutdown right from the login screen).

What I've tried so far: 
[LIST=1]
[*]MemTest competed in 1 hour without errors. 
[*]Booting with kernel 2.6.35.22 rather than 2.6.35.25 didn't help. Those are the two choices I have in GRUB.
[*]Disabling the Nvidia drivers didn't help. 
[*]Based on other questions that suggest some ACPI settings, I've tried **sudo shutdown -h now** to see whether the shutdown console text display offers any hints, but the system doesn't even get that far - it still freezes while the screen shown the desktop background image, without any toolbars. Only **sudo shutdown --force** works, but that's not a solution. 
[*]Editing the grub menu to add **acpi=off** to the kernel didn't help.
[*]Adding **noapic** to the grub entry had no discernible effect. 
[*]Adding **nolapic** instead did something (I had removed the quiet option) - the system managed to continue further with the shutdown, right until the line **Checking for running unattended-upgrades:** which were the last characters on the screen. 
[*]I've also checked the system BIOS, especially regarding power options, but didn't see anything out of the ordinary. Switching the BIOS standby setting from S3 to S1 didn't help. The standby setting can't be disabled, and there are no other ACPI-related settings AFAIK. 
[*]BIOS reset didn't help. I'm not surprised; I hadn't changed anything. 
[*]I tried going to a virtual console (CtrlAltF1) and from there did a **shutdown -h now** and it froze there too.
[*]Booting from Live CD (USB stick in fact) didn't help; it freezes the same way. 
[*]Booting from Live CD, with **acpi=off noapic nolapic** didn't help either. Neither did just **nolapic**. I guess this means that *the problem is not some custom setting in my install*, but some sort of basic issue?
[/LIST]
As you can see, I've already tried a lot of things, based on helpful input from other forums. I haven't solved it yet, so I'm now also asking here in the hope that fresh eyes can see something others have missed. I'm new to Linux, but capable of following instructions :)

I dearly hope that a solution exists. It would be catastrophic to not be able to suspend, or even shutdown; that would mean having to ditch Linux and move back to Windows again, which I'd really hate to do.

---

### Post by pmlxuser on 2011-02-24
did you test your disk for errors?? i would try another disk or distro all together and see how things work out..

---

### Post by zenwalker on 2011-02-24
dmesg command shall show you whats happening in your system before any panic could happen. But i wonder how you can see it since shutdown is freezing. 

Well what you could do is, when the shutdown happens, (logs updated till freeze happens), just do a hard reset and then pop in the live cd and chroot into the / paritition and then see the contents of /var/log/dmesg file.

---

### Post by timgood on 2011-02-24
The problem is with the wireless adapter. I have the same model and the wrong driver is loaded which prevents shutdown. To fix it you need to do this:

Open a terminal and type: ```
sudo modprobe -rf rt2860sta
```

Followed by: ```
sudo modprobe rt2860sta
```

Then you need to blacklist the wrong driver: ```
echo blacklist rt2800pci | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Once you have rebooted (you will need to do a hard power off for the last time!) you will find you can reboot properly. Thanks to Linuxexperte for this fix.

Hope this helps.

---

### Post by torbengb on 2011-02-24
@timgood, this sounds very promising! I'll try that tonight at home and report back afterwards. Thank you!

@zenwalker, I'll try your suggestion if timgood's tip doesn't resolve the problem. Thanks!

@pmlxuser, I didn't test the disk, but it's brand new. I don't want to replace the disk because it's built into a new nettop pc that I don't want to crack open because I might want to return it if this isn't solvable. I did try two separate Live CD's (using USB stick).

I'll report back.

---

### Post by torbengb on 2011-02-24
@timgood: Amazing! Three lines of terminal input and less than two minutes of work (including testing!!) and this problem that has been bothering me for a week is just gone! May I offer you a virtual beer?!

---

### Post by Alan.Brown on 2011-02-24
I have just bought and set up an HP-200-5220a with Ubuntu 10.10 and openSuSE 11.3 and have been getting the same problem on shutdown/reboot on both versions of Linux.   I have also had freezing at random times about once or twice an hour for no apparent reason (maybe related to mouse usage).   

None of the logs indicate any error situation - I guess if the system freezes then nothing is written to a log anyway.

I have had no problem with Windows 7.

I will try the above suggestions and see what happens.

Alan

---

### Post by Alan.Brown on 2011-02-24
I can now shutdown/reboot Ubuntu OK.   I was able to shut down openSuSE OK before.   I will have to run the system for a few hours to see if the sporadic freezing has been fixed - I will get back to you on this later.

Thanks for the suggestion.

Alan

---

### Post by timgood on 2011-02-25
> **torbengb said:**
> @timgood: Amazing! Three lines of terminal input and less than two minutes of work (including testing!!) and this problem that has been bothering me for a week is just gone! May I offer you a virtual beer?!


Mmmmn! Austrian beer! Nice.

---

### Post by Alan.Brown on 2011-02-25
I have used the computer extensively under both Ubuntu and openSuSE and have not had any further sporadic freezing so the problem has definitely been fixed.   There is no problem with shutdown and reboot under Ubuntu now.

Thanks timgood.

Alan

---

### Post by torbengb on 2011-03-03
> **timgood said:**
> The problem is with the wireless adapter. I have the same model and the wrong driver is loaded which prevents shutdown. To fix it you need to do this . . .

Timgood, would you mind educating me a little? I'd like to understand why this solution worked. 

I've understood that Ubuntu loads the wrong driver by default, and it's clear that wrong drivers may cause problems like this. But what does your fix do? It looks as if you remove the driver, then **add the same one** again, then blacklist **a different one** -- but I'm just guessing and I don't get why this would solve the problem. Can you explain to a Linux beginner? 

Also, how did you know what drivers to add/remove/blacklist? How did you determine **rt2860sta **and **rt2800pci**, respectively?

---

### Post by timgood on 2011-03-03
The fix was devised by Linuxexperte and his original post can be seen [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103").

Following his instructions I can surmise that:

```
lsmod | grep rt
```

gives a list of modules with 'rt' in them loaded. He noticed that the both the rt2800pci (wrong module for radio card) and the rt2860sta (correct module) were being loaded at boot and that one was interfering with the other, causing the shutdown problem we both experienced.

His next step is more problematic. He says do this:

```
sudo modprobe rf rt2800pci
``` which gives an error message. I believe this is just a misprint for:

```
sudo modprobe -rf rt2800pci
``` which is the code to remove the module. However on my machine this command caused the dreaded freeze, so I left this out next time I tried.

He then gives the code to remove the correct driver (rt2860sta) and then re-insert it. I have no idea why he does this, but he does state that on his machine it immediately caused the network to come back up. I had no way to test this on my machine because removal of the rt2800pci module freezes the 3700. So I did what he suggested, removed the module and then re-inserted it, blacklisted the driver, hard booted and then it worked. I did try to just blacklist the driver without removing and re-installing it, but seem to remember that I had a 'tainted kernel' message which required a full re-install. This of course, might just have been a nasty co-incidence, but I didn't want to risk it again. YMMV.

By the way, you may want to mark this thread as 'solved'.

---

### Post by torbengb on 2011-03-03
Thanks for the explanation! And thanks for the nudge to mark as solved; I wasn't aware of that feature. Done :-)

---

### Post by eilhart on 2011-03-06
Wow! Such an easy solution. Linuxexperte's first two commands didn't seem to do anything but after the third command I saw the driver was blacklisted in terminal. Then I tried shutting down which resulted in hanging again after that *poof* the problem is gone. Now it can freely sleep, reboot, shutdown etc.
 
I'm running Ubuntu Netbook Remix 10.10 on my LG X130 netbook.

---

### Post by heed396 on 2011-04-25
Finally solved my problem using this solution. Wish i had looked sooner rather than struggling along like a mong. It also solved my switching on and off the wireless card problem which was freezing my machine.
 
thanks timgood.

---

### Post by msambenny on 2011-05-04
Thank you Timgood....shutdown and reboot works fine )

---

### Post by justerson on 2011-05-10
> **torbengb said:**
> @timgood: Amazing! Three lines of terminal input and less than two minutes of work (including testing!!) and this problem that has been bothering me for a week is just gone! May I offer you a virtual beer?!

TIMGOOD YOU ROCK!!! I'll send you a case of virtual beer for this fix. Days of trolling forums and Google, and this blacklist rt2800 fixed my shutdown issues. Everyone else said it was the video drivers, but it's the wireless driver causing the problems.

This shutdown issue appeared when I upgraded to 11.04 so I reinstalled 10.10 and found this fix. Now I might be able to re-upgrade and blacklist and have it fixed in 11.04 as well.

---

### Post by ontwowheels on 2011-05-14
TIMGOOD, you rock the doublewide....worked perfectly on a new install I was having a problem with.

---

### Post by gringo22 on 2011-07-05
thank you i have been plagued by this problem and nothing i had tried worked until now thank you :D

---

### Post by saltydog on 2012-02-26
I have the same symptoms, but I don't have any wireless card!

If I type

```
sudo halt -p
```

the system shuts down,

if I type 

```
sudo shutdown -h now
```

the system freezes on the message "Will now halt"...

---

### Post by jimbudler on 2012-05-25
> **timgood said:**
> The problem is with the wireless adapter. I have the same model and the wrong driver is loaded which prevents shutdown. To fix it you need to do this:

Open a terminal and type: ```
sudo modprobe -rf rt2860sta
```

Followed by: ```
sudo modprobe rt2860sta
```

Then you need to blacklist the wrong driver: ```
echo blacklist rt2800pci | sudo tee -a /etc/modprobe.d/blacklist.conf
```

Once you have rebooted (you will need to do a hard power off for the last time!) you will find you can reboot properly. Thanks to Linuxexperte for this fix.

Hope this helps.

This was helpful in that blacklisting the rt2800pci prevented my shutdown and reboot hangs. However I don't appear to have any other driver for the rt3090, and so have no wireless.

Having no wireless is currently not a problem since I'm currently hooked up by wire. If I wanted to move my machine it could become a problem.

Being able to reboot cleanly is far more important.

Thanks, Jim

---

### Post by crondcrond on 2012-07-20
Hi,
I also have the same problem. It NOT get solved by the wireless module, modprobe solution.

Before I do the modprobe solution, I got the messages ,
[I]stoping mount file system on boot
acpid:exiting
checking for running unattended upgrades 
[/I]
after I made the modprobe change, I got

[I]could not write bytes:Broken pipe
could not write bytes:Broken pipe
could not write bytes:Broken pipe
could not write bytes:Broken pipe
checking for running unattended upgrades [/I]

I am running,  3.2.0-26-generic-pae
Due to the force shutdown I am doing, I already lost my custom changes in the grub menu [ def time out, background etc ] ...

Looking for a solution ...
Thanks,

---


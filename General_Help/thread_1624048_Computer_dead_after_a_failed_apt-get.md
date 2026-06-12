---
title: "Computer dead after a failed apt-get"
date: 2010-11-17
forum: General Help
---

### Post by piffany on 2010-11-17
[COLOR="gray"]Hi, I'm a new user with about a year of Linux experience. I encountered a serious problem and have nowhere else to turn to. Please share your expertise. Thank you.

Yesterday I was running some python code, and I wanted to RAR some result data. I did a sudo apt-get install rar, but the installation got stuck so I killed it with ctrl-C. Since that might result in a broken package, I tried opening synaptic with sudo synaptic but it wouldn't start because apparently apt-get is still running in the background. I tried to kill the process with kill $(grep apt-get) but it didn't work. Then I tried turning off my computer but it got stuck at a loading screen saying something about an incomplete install. Finally I just pressed the reset button, but instead of restarting normally, it beeped 2-3 times and nothing would show up on the screen. I repeatedly turned it off, wait a while, then turn it on, but nothing works. I tried unplugging everything (mouse, keyboard, internet, etc) except the monitor, but that didn't help. I tried hooking it up to another working monitor, but still got no improvement.

Any suggestions? The cause seems to be software-related but it's behaving like a hardware problem. By the way, the computer is dual-booted with Windows XP and Ubuntu but Windows wouldn't start either. Nothing at all shows up on the screen.

Edit: I tried booting from both USB and CD. Neither works. Also I think my motherboard is P5KPL-VM, if it helps at all. This computer is about 5 years old, and I recently reformatted due to problems I had before. It's been running fine since the reformatting, until now.
[/COLOR]

Update!!!!!!!!!

I just turned on the computer again to record what the beeps are like, and for whatever reason, things went back to normal. So now I'm back in Ubuntu and to make sure this doesn't happen again, I opened up synaptic to try to fix the problem with the rar package. It says it's installed but since the installation didn't actually complete yesterday, I wanted to remove it and reinstall again. When I tried applying the removal, it didn't work and a dialog popped up saying

"E: rar: Package is in a very bad inconsistent state-you should reinstall it before attempting a removal."

Well okay, so I went back but the reinstall option isn't available. I can only mark it for update, removal, or complete removal. And rar isn't actually considered a broken package. Any suggestions what to do next?

Final update:
Problem fixed with 'sudo apt-get update' then 'sudo apt-get install -f'

---

### Post by indytim on 2010-11-17
Boot to a LiveCD.  If you boot successfully, most likely it is not a hardware problem.  If you can't get the LiveCD to boot, probably facing a hardware "incident".

-IndyTim / DataMan

---

### Post by Swagman on 2010-11-17
Sounds like a co-incidence

2 - 3 beeps... long beeps or short beeps.

It sounds like a graphics card issue... UNPLUG mains and try re-inserting graphics card & RAM

---

### Post by piffany on 2010-11-17
> **indytim said:**
> Boot to a LiveCD.  If you boot successfully, most likely it is not a hardware problem.  If you can't get the LiveCD to boot, probably facing a hardware "incident".

-IndyTim / DataMan

Yeah I tried booting Ubuntu from both USB and CD. Didn't work...

---

### Post by sikander3786 on 2010-11-17
> but instead of restarting normally, it beeped 2-3 times 

You don't even see the Bios screen, right? Then cd-boot will be out of question.

It sounds like a RAM specific problem to me.

If you've more than 1 modules, try them one by one.

If you can borrow or another working module is available, you can try that.

I don't think if broken packages or apt-get has to do anything to that. It is just co-incidently a hardware failure at the same moment in my opinion.

---

### Post by piffany on 2010-11-17
> **sikander3786 said:**
> You don't even see the Bios screen, right? Then cd-boot will be out of question.

It sounds like a RAM specific problem to me.

If you've more than 1 modules, try them one by one.

If you can borrow or another working module is available, you can try that.

I don't think if broken packages or apt-get has to do anything to that. It is just co-incidently a hardware failure at the same moment in my opinion.

For some reason beyond my comprehension, the hardware failure is fixed, but now I have a broken package problem.

---

### Post by krismatth3 on 2010-11-17
I doubt the hardware failure is "fixed." It's more likely intermittent and quite possibly the direct cause of your software troubles. If you can't trust the hardware, you can't trust the software.

---

### Post by sikander3786 on 2010-11-17
> **piffany said:**
> For some reason beyond my comprehension, the hardware failure is fixed, but now I have a broken package problem.
How was it solved?

For broken packages, go to Terminal and post the output of

```
sudo apt-get update
```

```
sudo apt-get install -f
```

So we actually know about the offensive packages.

---

### Post by piffany on 2010-11-17
[LEFT]How the dead computer problem was solved, I have no idea. I just turned it on one time and it booted.

As for the broken packages here are the outputs from sudo apt-get update and sudo apt-get install -f

```

piffany@piffany-old-PC:~$ sudo apt-get update
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Hit http://ca.archive.ubuntu.com maverick Release.gpg               
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Get:1 http://extras.ubuntu.com maverick Release.gpg [65B]
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_CA
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_CA
Get:2 http://ca.archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_CA      
Hit http://extras.ubuntu.com maverick Release  
Hit http://security.ubuntu.com maverick-security Release             
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Hit http://extras.ubuntu.com maverick/main Sources                   
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick Release
Hit http://security.ubuntu.com maverick-security/main Sources                  
Get:3 http://ca.archive.ubuntu.com maverick-updates Release [31.4kB]           
Hit http://extras.ubuntu.com maverick/main i386 Packages                     
Hit http://security.ubuntu.com maverick-security/restricted Sources          
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com maverick/main Sources
Hit http://ca.archive.ubuntu.com maverick/restricted Sources
Hit http://ca.archive.ubuntu.com maverick/universe Sources
Hit http://ca.archive.ubuntu.com maverick/multiverse Sources
Hit http://ca.archive.ubuntu.com maverick/main i386 Packages
Hit http://ca.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://ca.archive.ubuntu.com maverick/universe i386 Packages
Hit http://ca.archive.ubuntu.com maverick/multiverse i386 Packages
Get:4 http://ca.archive.ubuntu.com maverick-updates/main Sources [39.1kB]
Get:5 http://ca.archive.ubuntu.com maverick-updates/restricted Sources [14B]
Get:6 http://ca.archive.ubuntu.com maverick-updates/universe Sources [11.8kB]
Get:7 http://ca.archive.ubuntu.com maverick-updates/multiverse Sources [651B]
Get:8 http://ca.archive.ubuntu.com maverick-updates/main i386 Packages [100kB]
Get:9 http://ca.archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Get:10 http://ca.archive.ubuntu.com maverick-updates/universe i386 Packages [38.0kB]
Get:11 http://ca.archive.ubuntu.com maverick-updates/multiverse i386 Packages [1,963B]
Fetched 223kB in 1s (132kB/s)                       
Reading package lists... Done
piffany@piffany-old-PC:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt3-mt libaudio2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  rar
The following packages will be upgraded:
  rar
1 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
1 not fully installed or removed.
Need to get 0B/557kB of archives.
After this operation, 1,192kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package rar.
(Reading database ... 
dpkg: warning: files list file for package `rar' missing, assuming package has no files currently installed.
(Reading database ... 126372 files and directories currently installed.)
Preparing to replace rar 2:3.9.3-1 (using .../rar_2%3a3.9.3-1_i386.deb) ...
Unpacking replacement rar ...
Processing triggers for man-db ...
Setting up rar (2:3.9.3-1) ...

```[/LEFT]

---

### Post by sikander3786 on 2010-11-17
```
sudo dpkg --configure -a
```

If it doesn't fix,

```
sudo apt-get remove --purge rar
```

If still not fixed,

```
sudo dpkg -r rar
```

---

### Post by piffany on 2010-11-17
Actually the problem was solved with the previous two lines. I already edited my original post ("Final update...") to show this. Thanks for all your help! :)

---

### Post by sikander3786 on 2010-11-17
> **piffany said:**
> Actually the problem was solved with the previous two lines. I already edited my original post ("Final update...") to show this. Thanks for all your help! :)
Ohh. I didn't notice that.

Glad it is sorted out :-)

Please mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of the page.

Happy Ubuntu-ing!

---


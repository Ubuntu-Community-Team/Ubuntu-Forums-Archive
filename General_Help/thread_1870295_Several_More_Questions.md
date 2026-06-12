---
title: "Several More Questions"
date: 2011-10-27
forum: General Help
---

### Post by Mercdya on 2011-10-27
This is a repost of a reply I made to an already open thread could not figure out how to make a new post until just now so below is the Original Post and I'm hoping since it's a new thread it'll get views.

I also have several questions I can not figure out how to start a new  thread on this Forum so if anyone could help with that I'd be greatful. 
I am dual booting Ubuntu 11.10 with Windows 7 as the main OS using wubie  on a Intel Core 2 Processor with 4 GB of Ram and it's a laptop. I have  already had Ubuntu as the Main and only OS It seems to run just as fast  as it does now that I am dual booting it which is awesome. However this  same problem occurred no matter how I install it. I play a game called  Evony only recently switched to Ubuntu. On Windows7 with Internet  Explorer or Firefox I am able to Open 12 tabs simultaneously in my  browser and run the game on each tab without lag. Firefox on Ubuntu  however only allows me to open about 5-7 tabs before slowing down to  being useless or crashing. What Gives??? Haven't tried it through  Chromium That would be my next option just wondering if someone could  point me in the right direction of getting Firefox to run properly or a  browser that would be more willing to allow this sort of thing.

Important if you want to keep this Windows user I like to run my  computers clean and fast I would be greatful for anything that tweaks  the OS to run faster and any information on what to shut down that runs  in the background a list of files safe to shut down in my System Monitor  would be great. 

Mostly I just like computers to run clean so any other methods of  cleaning up this OS are greatly appreciated not afraid to run the  terminal either so send those commands. 

Last Question sorry this is so long but looking for the equivalent of  DeepFreeze (Windows Program) For Ubuntu 11.10 Found one but I believe it  only works on 11.04 called Ofris I think please let me know as I might  recommend this OS to customers I am a PC technician and this OS is  SWEET!!! Awesome Job Linux LOVE the Customization it's amazing.

Signed,
I'm a PC
First Time Ubuntu User (or Linux in General)

---

### Post by HermanAB on 2011-10-27
Instead of deepfreeze, make a Virtual Machine with Virtualbox and use snapshots.

---

### Post by decoherence on 2011-10-27
replied in the original...

[http://ubuntuforums.org/showpost.php?p=11398150&postcount=16](http://ubuntuforums.org/showpost.php?p=11398150&postcount=16)

---

### Post by oldos2er on 2011-10-27
So many Windows users ask about cleaning, and I'm not really sure what they mean by that other than the obvious things e.g. browser caches, etc. Linux is not Windows; there's no registry in the Windows' sense of the word. Ubuntu's system temp folder (/tmp) is cleared on each reboot, so nothing to do there. Some cruft will accumulate in a user's home folder if one installs and removes a lot of programs, but most dotfile folders (i.e. hidden folders containing configuration data) are relatively small in size (KB), and won't occupy RAM unless a given program is run.

To clear APT's cache, run ```
sudo apt-get clean
```

Suggestions on how to free up hard disk space here: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

Ubuntu uses upstart to control services, and if you're an end user like me, it is not the easiest thing to understand. See [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

---

### Post by oldtimer7777 on 2011-10-27
Windows users had to buy software like CCleaner to clean their systems out.

It took me a while to find out what app in Ubuntu is comparable to CCleaner in Linux.. The name of the equivalent is Bleachbit.

sudo apt-get install bleachbit
sudo bleachbit

---

### Post by 3Miro on 2011-10-27
Evony seems like a Flash game. If it is, then I am surprised you managed to get two tabs opened. Adobe's version of flash under Linux is mostly garbage, it works, but it is ultra slow. Other than yelling at Adobe, there is nothing else that you can do.

---

### Post by Mercdya on 2011-10-27
Awesome Bleachbit works exactly what I was looking for great find Thank you.

---


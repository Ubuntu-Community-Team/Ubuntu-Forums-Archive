---
title: "libpng, lucid and my canon printer (problems)"
date: 2010-05-08
forum: General Help
---

### Post by Duncan J Murray on 2010-05-08
Dear all,

Having installed and enjoying Lucid Lynx, it's now the time for me to install my Canon IP2500 printer, something which is tricky, but has been doable in jaunty and karmic following these instructions:

[http://translate.google.co.uk/translate?prev=hp&hl=en&js=n&u=http://wiki.ubuntuusers.de/Canon-Drucker&sl=de&tl=en&history_state0=](http://translate.google.co.uk/translate?prev=hp&hl=en&js=n&u=http://wiki.ubuntuusers.de/Canon-Drucker&sl=de&tl=en&history_state0=)

In lucid, however, I am meeting a brick wall with libpng.  If I try to install it with sudo apt-get install libpng3, it informs me that it is already installed.  However, when I look in /usr/lib I cannot find any files with 'png' in it at all!

This is a real problem, as the printer driver needs some sort of libpng to work.

Any ideas where this has gone?

All best and thanks in advance,

Duncan.

---

### Post by Duncan J Murray on 2010-05-08
hmm, managed to find libpng.so.12 in /lib.  then linked libpng3 over to this file. however, this doesn't make the printer work :(

on top of that, I can't get the printer working on another laptop running karmic now!

tempted to throw in the towel and either buy turboprint, or even cheaper, a linux-compatible printer.

anyone with any better luck?

duncan

---

### Post by osairis ali on 2010-05-14
I have same problem.... I have canon MP250 series which works good on jaunty both printing and scanning... but it can't work on lucid... nothing happened when I try to print file from evince... and nothing happened too when I try to scan document.... this printer is "all-in-one device" I've installed all the printer driver from canon website... both scangearmp and cnijfilter.... but the same bad.... nothing happened too... I don't know what else to do next... 


need some help from seniors.... 

thanks before....


Ali Akbar H.

---

### Post by Jason Argonaut on 2010-05-16
Ali, refer to this link:

[http://ubuntuforums.org/showthread.php?t=1313992](http://ubuntuforums.org/showthread.php?t=1313992)

The prob might revolve around x86/amd64 under lucid lynx.

---

### Post by whiteman on 2010-12-18
I am sim,ply amazed at all of tyhese people with their canons who are ABLE TO SEE THEM. I have installed 9.10 and 10.04 both unsuccesfuly for my canon mp470. I have three printers and only the HPs show up under printer setup. The drivers are no problem. They are there. Every canon driver u can thiink of, BUT hiw do you set it up if u cant see the darn thing? Only Janty works. I have trid setting up and upgrading to 9.0 then 10.04 all upgrades. I have tried formatting hd and then dong clean installs. NOTHING MAKES IT VISIBLE. I am at my wits end. I have been using jaunty for months now bwecause of this, but nothing is supported anymore. I have even entered my ip address like this 192.168.0.199:631......NOTHING. NADA. Or sometimes it will setup what OI call a shadow. Its lighter than the other one, but it doesnt do anything. There is noway to make the driver "stick" to the printer. Then 9.1 had all of the failsafe, Gnome issues. The add remove thig doesnt work unless you login as guest. Are these improvemnts? Give me jaunty anyday. I know Lynx has improvemnts but I have been unable to enjoy them. I am reinstalling Lynx for the 5th time today. Also it would be better if I could do a truly clean install, but every install keeps some of the old configs and yer back where u started from. SO I deleted evbrything I could befiore I rebooted. Any ideas? (Get a mac) Got one.

---


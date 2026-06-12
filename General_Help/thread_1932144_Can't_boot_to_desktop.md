---
title: "Can't boot to desktop"
date: 2012-02-26
forum: General Help
---

### Post by bludshot on 2012-02-26
I did a fresh install of Lubuntu on an empty laptop and then I was doing various things (installing and configuring software) etc over a period of days, but then next time I turned on the computer it didn't boot to the desktop but instead got stuck on a black screen that said:

Checking for running unattended upgrades

It would stay on the screen forever and I couldn't get into the desktop.

So I booted to recovery shell and removed the unattended upgrades with apt-get (after figuring out how to make the file system not read only)

Then I turned on the computer again and it said Cannot write bytes broken pipe.

So I booted to recovery shell and I did dpkg-reconfigure lxde (based on some googling I did that said that should fix it).

After that I don't see the broken pipe error anymore, instead I get a black screen, then for a split second I see the Lubuntu loading screen and then a black screen forever and it won't boot properly.

I was told on IRC to try using grub to boot with nomodeset as this might fix the problem. So I rebooted and hit SHIFT a bunch of times to get to the grub menu. But the grub menu did not come up. Instead, it said:

Checking for running unattended-upgrades"python: can't open file '/usr/share/unattended-upgrades/unattended-upgrade-shutdown': [Errrno 2] No such file or directory  

(And it just stays on that and won't load the desktop)

I don't know what to do?

---

### Post by Rodney9 on 2012-02-27
I'm no expert, you could try at the black screen alt/ctrl f2 or f3.
This should get you to a command line and you need to log-in.
Then I would run  > sudo apt-get update && sudo apt-get upgrade

Beyond that I don't know, except re-install.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---


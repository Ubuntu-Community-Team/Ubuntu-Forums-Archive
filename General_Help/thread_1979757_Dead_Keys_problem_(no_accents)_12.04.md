---
title: "Dead Keys problem (no accents) 12.04"
date: 2012-05-14
forum: General Help
---

### Post by Angelos72 on 2012-05-14
I have tried to use lxkeymap and all lubuntu tools in order to setup the us and greek keyboards, without success. So finally I used the following command

> setxkbmap -option grp:ctrl_shift_toggle "us,gr"

Which I thought did the trick, until I realized that I could not accent the letters (which is done by pressing a dead key and then the letter that needs to be accented.) In fact the dead keys do nothing (even after I press another key after the dead one).

I figured it might be that I did not select the correct Greek variant, so I tried:

> setxkbmap us,gr -variant ,extended -option grp:ctrl_shift_toggle -option grp_led:scroll


Nothing changed.

It is notable that I can accent the letters normally in Open Office.

I would appreciate any help or any idea or any possible explanation about this problem.

---

### Post by panoz on 2012-05-24
I second that. Can't find any solution yet.

Any other way to choose and change layouts on lubuntu than lxkeymap?

---

### Post by felixwong on 2012-05-26
Here's a solution I came up with.  It turns the caps key into a compose key.  You don't even have to change the keyboard layout from US to anything else.

In a terminal shell, type:
sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart
[enter your admin password, and leafpad editor comes up]

Add the following line to the end of the file autostart:
setxkbmap -option compose:caps

Voila.  Once you reboot the computer, the caps key is now a compose key, and you can type accent marks.  For example, to type é, press [caps key], then ['], then [e].  Or for ¿, press [caps key], then [shift+?] twice.  Or for ç, press [caps key], then [,], then [c].

Now a rant:
It took me TWO HOURS to figure out this solution.  All because lxkeymap doesn't work in Lubuntu 12.04, even after uninstalling/reinstalling lxkeymap several times.  lxkeymap worked in Lubuntu 11.10.

This is why I will still not recommend Linux to all but the most computer-savy people with loads of patience and nothing better to do.  It can be, quite frankly, completely non-intuitive and utterly frustrating.  How is someone supposed to pull all these command lines right out of their *ss?  TWO HOURS of Google searches and trial and error to come up with my own solution is not reasonable.

All that after I had to spend hours installing Lubuntu 12.04 from scratch because trying to upgrade from Lubuntu 11.10 on my Dell Mini 9 was completely unsuccessful and resulted in a nonbootable computer.

I'd never wasted so much time on these things with any version of Windows or MacOS and if I wasn't so cheap with low-$ hardware and software, I wouldn't be in this position.

---


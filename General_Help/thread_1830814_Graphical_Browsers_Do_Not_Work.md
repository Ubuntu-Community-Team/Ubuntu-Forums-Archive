---
title: "Graphical Browsers Do Not Work"
date: 2011-08-22
forum: General Help
---

### Post by &#32 Greg on 2011-08-22
A few weeks ago, I acquired a new Thinkpad t420, and decided to install Ubuntu on it (I'm normally an Arch person). Everything was working perfectly until I happened to try to get onto a network (this week) and it wouldn't connect. I eventually found that the issue was I needed to set swcrypto=1 on iwlagn. (Incidentally, does anyone know how to make it do this on bootup, rather than modprobing?). Shortly after that, I discovered another problem. None of my web browsers (including newly installed ones) with the exception of elinks work.

They will come up, and I can browse the web for a time, but then they will inevitably crash. In the case of Firefox, it crashes and brings up the bug screen. In Chromium, it freezes. Midori and Epiphany close with a Segfault, according to the terminal I run them from, and Conkeror closes itself out without any messages in the terminal. I've tried uninstalling all my browsers, reinstalling them, getting rid of Java (there was a message at one point mentioning IcedTea, but that didn't help), powercycling... and I'm out of ideas. Anyone know what I should do?

---

### Post by pqwoerituytrueiwoq on 2011-08-22
i know a work around for the mod probe
you can add the command at the end of /etc/gdm/Init/Default before the exit line
as for the browser freezing try installing adblock, flash block, and or no-script

---

### Post by &#32 Greg on 2011-08-22
Thank you for your advice. Your solution for the modprobe issue doesn't seem to work. I believe that there should be a place somewhere to configure modules- in Arch that was done in rc.conf. 

As far as your other suggestion goes, I am fairly confident that ads are not the source of my problem; I actually do have adblock installed on some browsers but the sites that it crashes on are arbitrary, and they will not necessarily cause a crash the next time.

---

### Post by &#32 Greg on 2011-08-25
I found a solution to my modprobe issue; browsers still crash haphazardly, however. Does anyone have any ideas?

---

### Post by pqwoerituytrueiwoq on 2011-08-26
care to share your solution?
maybe the browsers think your gpu can do hardware acceleration when it can't
about:config in firefox see pic
are these sites using a lot of adobe flash?

this location may be useful for models but idk
```
nautilus /lib/modules/`uname -r`/kernel/
```
i had spent a while looking for a way to pick and chose modules but failed

---


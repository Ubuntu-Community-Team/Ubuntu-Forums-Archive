---
title: "I'm a n00b &amp; Screwed up - All my files gone, desktop, firefox addons, home folder"
date: 2009-09-28
forum: General Help
---

### Post by iamaYs on 2009-09-28
Hello,

I am new to Ubuntu installing it only a few days ago and I love it. I downloaded all the apps that I wanted, my wallpaper, firefox addons and Linux kicks azz.

I'm a uber n00b and have been having some difficulties with the terminal commands. I installed LAMP successfully, but haven't tried updating the nameservers on my domain names to point them to my www directories. I gaveup when I tried installing Mailman.

Anyway, today I was trying to install Full Tilt Poker through Wine and was having trouble getting it to work. I uninstalled wine and installed an earlier version and it still didn't work.

Then, I came across this website: [http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html](http://www.nyutech.com/2009/03/how-to-install-and-completely-remove.html)

and followed their instructions for completely removing wine:

```

sudo apt-get remove wine
rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

```When I entered the 2nd and 3rd commands they both said something along the lines of can't remove home directory or something... oh ****, I just realized what I did I think. I put a space between $HOME/ and .wine because on their website it looks like there is a space dammit.

What happened was, when I minimized my browser all my desktop files and wallpaper were gone. Then I opened my home folder and the contents were gone. And then all my firefox stuff was gone and I couldnt' open Synaptic.

Well, I restarted and it looked like a fresh install of Ubuntu. I'm not too worried because I didn't lose much, only some Video Seminars I downloaded that is about a Gig.

But anyway, if anyone could give me some advice that would be appreciated. Comments welcome. I'm new to this and I want to know what is the best setup for a 32 bit processor and Ubuntu. What programs should I install and how do I setup my webservers better. Any posts or resources that you could point me to would be helpful too. Why is it so difficult to install Mailman?

Thanks! I look forward to getting better at Ubuntu. I've used windows since 3.1 and worked on Macs for the past few years. I really think that Ubuntu will take over in a few years if it keeps it up. Ubuntu is the shizzle

---

### Post by fluffman86 on 2009-09-28
1. Always read commands carefully before copy/pasting into a terminal. 
2. If you're not sure what the commands say, you can copy/paste into a terminal simply by highlighting a line, then middle-clicking in the terminal to paste.

---

### Post by iamaYs on 2009-09-28
Thank you! That's exactly what I needed but I just couldn't think of it. Every time I would try to copy and paste into the terminal it would show a ^V so I just thought you couldn't do it. Thanks again! This will save me from trying to guess what a command is in the future

---


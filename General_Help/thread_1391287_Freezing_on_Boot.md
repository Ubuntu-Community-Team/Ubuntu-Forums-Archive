---
title: "Freezing on Boot"
date: 2010-01-26
forum: General Help
---

### Post by Engvar on 2010-01-26
Ok, here's the deal. I've had ubuntu for a few months now, I'm no wiz with computers, but I was hoping that this would help me learn. I am, but now I've run into a problem.
 
I wanted to use a couple effects on my computer in a presentation for one of my classes, so I needed to hook up my laptop to the projector at the college. I searched for a command to do this, and found one.
 
I went here:
[http://www.alterego7.com/2008/04/getting-projectors-to-work-in-ubuntu.html](http://www.alterego7.com/2008/04/getting-projectors-to-work-in-ubuntu.html)
saw that a few people said that it worked, so I figured I had it made. I punched in the command...
 
sudo dpkg-reconfigure xserver-xorg
 
reset, and it came up on the projector. Boot looked normal, but partway through, I get a line of little ubuntu logos at the top, colors all screwed up, and it freezes. The logos will vanish then appear again every few seconds, but I can't do anything.
 
Now I can't figure out how to get on my computer, all my classwork is on there, and I just can't fix it...
 
Any ideas?
Thanks...

---

### Post by Engvar on 2010-01-26
Bumping this, any help is greatly appreciated. Hopefully will be able to get it working before the report is due on thursday.

---

### Post by vinnywright on 2010-01-26
did you half to add a driver for your vid card when you first installed?

if so you will half to do it agin.

if not boot to recovery moad and do the fix x option .........or comand line and do > sudo dpkg-reconfigure -phigh xserver-xorg (withought the projector conected)

if ubuntu is the onley OS and you never see the grub screen wile booting hit esc wile booting for grub.........or hold down shift wile booting if grub2...............to get the grub boot screen whar the recovery moad will be.

VINNY

---

### Post by Engvar on 2010-01-28
Havn't been on, I just redid the report. Thanks for the help though. I did have to install a driver for my vid card, so hopefully this will work. I'll try it out, and see what happens.
 
If nothing else, it turns out I have a friend that is a Linux wiz, and it just never came up. He said that if all else fails, we'll just put my hard drive in a different comp, get my files, put it back in, and reinstall.
 
I've got nasty packed schedule on weekends... so I'll repost when probably monday or tuesday when I get a chance to do this.

---


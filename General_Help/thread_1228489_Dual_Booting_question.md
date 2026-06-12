---
title: "Dual Booting question"
date: 2009-08-01
forum: General Help
---

### Post by Nater43 on 2009-08-01
Hello. 

I was wondering if anyone could help me out with this problem. I have Windows 7 on my internal drive, and Ubuntu 9.04 on an external HD. I have GRUB on the external. When the GRUB menu comes up, I see Ubuntu, and all related Ubuntu things (ex. Safe Mode). I also see Windows Vista...my question is why? And when I try to load "Vista" hoping it would just boot Windows 7, I get an error. My question is: How do I get Vista off that menu, and 7 on to that menu?

---

### Post by stlsaint on 2009-08-01
is vista the os that came on your system?

---

### Post by pedro3005 on 2009-08-01
Edit /boot/grub/menu.lst  to get vista off the list (ALT F2 then gksu gedit /boot/grub/menu.lst). The win7 question i don't know :(

---

### Post by celljak on 2009-08-01
Sounds Like your wanting to edit grub

gksudo gedit /boot/grub/menu.lst

Go in there and edit the windows listing to the proper partition.
I may be wrong but that should be a start.


If you can't figure it out you can also paste your settings here and see what we can do.

---

### Post by Bucky Ball on 2009-08-01
You could call that partition 'the cow jumped over the moon' and it wouldn't matter. In other words Vista, XP, 7; irrelevent. What is relevant is the instruction that come after that in the boot menu and yours are obviously wrong. 

In a terminal in Ubuntu paste:
```

nano /boot/grub/menu.lst
```This will take you to the file that controls all of this. Have a look around in there. At the bottom you will find your windows entry.

Now, you don't supply the error number (please do) but what is probably happening is the part that says:

```
(hd0,0)
```... Or whatever, under the windows entry is wrong. If your Windows 7 is on the first partition of the first hard drive (hd0,0) is right. If not, this instruction is pointing to the wrong partition. Have a look around and get back to us with a bit more detail if you could (under windows entry what is (hd?,?) and error number). Should be no problem fixing it if it is that simple (usually is).

Incidentally, the instruction above will not let you change that file, you need to add 'sudo' to the beginning of it to do that. Dangerous. Therefore, always back it up with something along these lines:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.**bkup**
```... Or something to your liking, using or replacing 'bkup' with what you want (I use the date). Once backed up, feel free to experiment and see how you go. Change the 'XP' to 'Windows 7' or whatever you want to call it. Experiment with (hd?,?) and see if you can figure out which partition it should be pointing at.

:)


(hd0,1) = first disk, second partition
(hd1,0) = second disk, first partition

... and so on ... Good Luck.

---

### Post by Nater43 on 2009-08-01
Well, thanks to you guys, I got that problem fixed. Now, I'm having another problem. I can't manage to set up an internet connection. I set it up, and when I'm done, it says "never" next to it. I'm not quite sure what that means, if anything. How do I get it to connect?

---

### Post by Bucky Ball on 2009-08-01
You would be best to post a new, separate thread about your networking issue as the title of this one has nothing to do with it (therefore people that could help won't look here). Type of connection, wireless card, router or whatever is relevant. 

Post a link to the new thread here and I'll join in and help if I can. You will get more help by doing it that way and others will find it easier to find a fix under the new title rather than buried here.

Glad to hear it is working out thus far and welcome ... :)

---

### Post by Nater43 on 2009-08-01
[http://ubuntuforums.org/showthread.php?p=7714498#post7714498](http://ubuntuforums.org/showthread.php?p=7714498#post7714498)

---


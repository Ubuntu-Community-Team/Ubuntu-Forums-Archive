---
title: "Troubleshooting Freezes"
date: 2010-03-08
forum: General Help
---

### Post by tigerking615 on 2010-03-08
Hey,

My computer has problems with freezing. Usually what happens is X stops responding (ctrl+alt+backspace doesn't work), and my laptop goes completely quiet (almost like it's off). I can usually move the mouse around but nothing really responds. I have to do a hard reboot by holding the power button. My first thought was that it might be a hardware issue, but I've never had this problem on Windows. I read [this page](https://wiki.ubuntu.com/X/Troubleshooting/Freeze), but I don't get how this Apport thing works. I enabled it, but it doesn't seem to collect data from all my crashes. I've had this problem for a long time, but the log only shows stuff from a crash yesterday (that one was completely different from the usual problem). I'm looking at "/var/log/apport.log.1".

Is there any other way to get some sort of error message or log that would tell me what happens each time there's a problen? Or am I looking at a completely wrong file?

I'm pretty much beginner-intermediate with Ubuntu. I'm using 9.10 installed through Wubi. I have not yet filed a bug report on Launchpad because I don't have any sort of error message or something like that. 

Let me know if you need any more information and I'll be happy to provide that.

---

### Post by woodmaster on 2010-03-09
This helped me with that.
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by tigerking615 on 2010-03-10
Uhh... are you sure you posted the right link? That one really didn't have anything to do with my problem :/

---

### Post by trubble on 2010-03-10
I'm having the EXACT same issue as the OP - these freezes happen no matter what's running so I can't pin it down to a particular program.

The only thing that can be done is pressing the RESET button to reload.

My machine runs 24-7 and it can run for days without crashing or 2-3 times per day.

Very strange -- and this is running the x64 version with 4gig of ram.

---

### Post by alfplayer on 2010-03-10
If this happened to me what I'd do is go to a tty pressing Ctrl + Alt + F1 and try to use the console. If the console works fine and the "top" command doesn't show any process hogging the CPU it might be a problem with X. And, if it is a problem with X you can follow that link.

---

### Post by tigerking615 on 2010-03-12
It has happened twice in the last day, and Ctrl+Alt+F1 didn't do anything. I had to hard reboot as usual.

---

### Post by buseness on 2010-03-13
I've been having the exacted same problem. I have pinned it down to the fact that Ubuntu can not run the proper drivers for the chip-set in your motherboard. In my case it is the Intel I845E, which is a very popular hardware among computers. In your case and my case because the proper drivers cannot be installed then the chip-board and (for me) "Video Card" does not function the way it should. This was a neat looking program but I will have to purchase a copy of Windows XP so I can get back to work. Its also to bad I was really excited about running this operating system do to my work with graphics.

---


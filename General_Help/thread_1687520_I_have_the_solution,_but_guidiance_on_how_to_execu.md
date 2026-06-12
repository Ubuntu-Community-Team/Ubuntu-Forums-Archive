---
title: "I have the solution, but guidiance on how to execute would be helpful"
date: 2011-02-14
forum: General Help
---

### Post by Fjas on 2011-02-14
I have a Lenovo B560 ubuntu 10.04 and the headphone-jack isn't working. I have been able to google my may to this solution:

> 
 						Hi!
I've got the same probs with my G560. Try this in e.g. /etc/modprobe.d/sound.conf:
[INDENT]options snd-hda-intel model=ideapad

[/INDENT]
With the ideapad-model the headphone jack should be working as expected.
Bye!
 					
 				 			 		 		 			
....but i dont know much about linux, so it would be nice if someone could write an "beginners step-by-step' manual. 

Thnx in advance. :)

---

### Post by An Sanct on 2011-02-14
Try from terminal:
```
sudo cp /etc/modprobe.d/sound.conf /etc/modprobe.d/sound.conf.bak
sudo gedit /etc/modprobe.d/sound.conf
```
the first line will make a backup of that file, the second will open a text editor, there find the parameters you are looking for.

When you find it copy and paste the whole line (make a duplicate) and put a "**#**" character in front of the original (to comment it).

PS. I didn't find such a file, but there might be differences between our setups.

---

### Post by ajgreeny on 2011-02-14
Assuming that google answer is correct:

1.  Run ```
gksudo gedit /etc/modprobe.d/sound.conf
```in terminal.

2.  In the text editor that pops up, probably empty, add the text shown.

3.  Save the file, and then try your sound through headphone jack again.  It may need a reboot, but I am not sure about that.

If it does not work, to get back to where you were before, run the same command and delete the text yo added, or just delete the file with ```
sudo rm /etc/modprobe.d/sound.conf
```

---

### Post by mikewhatever on 2011-02-14
Where is that solution from? Usually, such options are appended to /etc/modprob.d/alsa-base.conf.

---

### Post by Fjas on 2011-02-14
> **mikewhatever said:**
> Where is that solution from? Usually, such options are appended to /etc/modprob.d/alsa-base.conf.

[https://bbs.archlinux.org/viewtopic.php?id=103470](https://bbs.archlinux.org/viewtopic.php?id=103470)
------------------------------------------------------------------------

Thank you. Sound is now up n running. :)

---

### Post by An Sanct on 2011-02-14
Great, to hear that. Please mark the thread as [solved], so, that other have the benefit of the correct information.

---


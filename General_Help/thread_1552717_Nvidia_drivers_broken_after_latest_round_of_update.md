---
title: "Nvidia drivers broken after latest round of updates (Lucid)"
date: 2010-08-14
forum: General Help
---

### Post by bakaeigo on 2010-08-14
After installing updates today and rebooting, I found that I could only run X in "basic mode," and that none of desktop effects made possible by my Nvidia card could be enabled. I tried running nvidia-xconfig to reconfigure my Xorg, but it didn't help. Any ideas?

---

### Post by bakaeigo on 2010-08-14
These updates seem to have brought on a slew of other problems, too. Some applications now do not play sound, others have started segfaulting on startup.... contemplating just reinstalling a fresh copy

---

### Post by worksofcraft on 2010-08-14
I just ran update manager and brought my system fully up to date and rebooted. I am not seeing any of the problems you mention.

Attached is a snapshot of my Nvidia settings.

How do they compare to yours?

---

### Post by bakaeigo on 2010-08-14
When I open Nvidia settings, I get this dialog:

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

I have run sudo nvidia-xconfig and rebooted, but to no avail -- When I do that I am presented with a screen vertically shifted down about 100 pixels with horizontal stripes of noise taking up that top portion of the screen, and I am forced to have X load the "default" settings again.

---

### Post by worksofcraft on 2010-08-14
I think there are two different things to look at.

System->Administration->Hardware Drivers

it searches for a while for available drivers and then I have selected

NVIDIA accelerated graphics driver (version current) [recommended]

after selecting that you may have to click on "Activate"

Then there is also:

System->Administration->NVIDIA X Server Settings

and that should give you the display I posted earlier.

---

### Post by bakaeigo on 2010-08-14
As I said before, Nvidia X Server Settings gives me an error message telling me I am not using an Nvidia X driver. I've attached how this looks.

Also, when I go into System > Administration > Hardware Drivers, the recommended driver is already installed and activated. Un- and re-installing this has had no effect.

---

### Post by nickread on 2010-08-15
I can confirm all of the same symptoms that you're receiving bakaeigo.  Nvidia driver stopped working after the last kernel update.

---

### Post by worksofcraft on 2010-08-15
It's wierd it works OK for me and not for you. However per chance I just stumbled on another thread about this where there were several solutions suggested.

Check it out:

[http://ubuntuforums.org/showthread.php?t=1466150](http://ubuntuforums.org/showthread.php?t=1466150)

---

### Post by tomverweij on 2010-08-17
Hi 

Seems i have same symptoms.
Had Lucid running for months without problems on my Dell E6500 (using grub with also XP partition). Before that Karmic, upgrade went reasonably fine.
Compiz worked, no CPU melting xorg, all ok. But.....

Couple of days ago I decided to get last round of updates, cause i experienced some unwanted hibernate behaviour. Bad move.
AFter update message "low graphics mode bladiebla" 

And now for 2 nights in a row trying to get my system back to normal.

I've tried lots of stuff but seem to miss something. PAin is that now running X without nvidia makes xorg run the CPU really hot and still being very slow.
Not nice when you are reading page after page and rebooting every next attempt.

I decided to not give up and learn.

Tried sofar:
- removing all nvidia stuff with apt-get
- reinstall nvidia with apt-get
- installing nvidia with or with nouveau stuff
- blacklisting nouveau
- reinstall jockey and pick the listed 173 nvidia (that seems to be 195 ?)
- get a fresh NVIDIA*.run and install from shell (so not within X)
- inspect xorg.conf and all backups. Trying X with or without xorg.conf.

Please walk with me and ask the questions.
Unfortunately i read a lot of threads but i can't seem to understand what the hell happened and how to fix.
I feel i'm innocent :-)

Thx in advance

Tom

---

### Post by tomverweij on 2010-08-19
Guess what,

SOLVED !:popcorn:
Turned out that I was booting into the wrong kernel all the time.
I never got around understanding that I was running the "old" Grub, whereas the updates became available under grub2, that I had never upgraded to. 
Reading [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) helped me out.

Once I got to pick 32.24 instead of the 31.19 kernel, nvidia was immediately fine.
So I guess i will only now experience Lucid instead of Karmic, allthough I thought I was running it for months...

Oh well, another lesson learned.

Cheers
Tom

---


---
title: "ubuntu 9.04 not booting properly."
date: 2009-09-02
forum: General Help
---

### Post by jainankush15 on 2009-09-02
I am real new at Linux and loaded Ubuntu 9.04 as a dual boot on my older machine with vista. It had been working great all week. I was just getting 
somewhat used to it. I was using it last nite, playing music, videos, just seeing what all was working that was imported from My Documents in vista.

I loaded some apts that looked interesting, (I don't remember what they all were) but all was working great.

Today, when i got home from work, go to turn the computer on and by default it supposed to boot into Ubuntu. I get the splash screen, the lines slides all 
the way over, but before it launches, I get a garbled screen that kinda flashes slowly 3 times, then locks an another totally garbled screen. (a few times, the flashing screen 
would show a partial "[Windows[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://www.bleepingcomputer.com/forums/topic227424.html#") is now shutting down" screen, then the locked garbled screen you could see several little "ubuntus" at the top, and blue Windows looking
on the bottom half.)

I can boot into Windows vista just fine tho!

I tried changing the moniter cable, shutting down the Windows computer completely before restarting. I booted into the Ubuntu Recovery screen, tried doing a few of those 
"fixes", nothing is working. I even ran a virus scan in vista to make sure that wasn't causing any boot problems, it came up clean.

Any ideas out there?

Thanks ahead of time!

ankush

---

### Post by P4man on 2009-09-02
that sounds ... weird!

After it finishes booting, despite the graphical corruption (showing a partial windows shut down screen ? LOL? ), see if you can access a terminal, by pressing control + alt +F1

If you get a prompt, we can try and figure out what happened and/or restore your ubuntu.

---

### Post by jainankush15 on 2009-09-03
> **P4man said:**
> that sounds ... weird!

After it finishes booting, despite the graphical corruption (showing a partial windows shut down screen ? LOL? ), see if you can access a terminal, by pressing control + alt +F1

If you get a prompt, we can try and figure out what happened and/or restore your ubuntu.
no i can't access terminal pressing ctrl+alt+f1, the all i'm having control on is to restart the system pressing ctrl+alt+del.
can you plz tell me the procedure to uninstall ubuntu, i installed it on to a new partition in my hdd.(DUAL BOOT WITH VISTA)

---

### Post by christopherbalz on 2009-09-13
You can get to the terminal prompt on Jaunty by following these instructions: 

[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

In earlier Ubuntu versions, this procedure was not necessary.  However, for usability reasons (inadvertent terminal sessions), ctrl-alt-backspace was removed in Jaunty.  

You will likely need to boot into recovery mode to do this if your machine will not boot into a regular X session.

---


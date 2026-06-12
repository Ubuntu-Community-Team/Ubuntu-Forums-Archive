---
title: "The BusyBox initramfs message"
date: 2010-10-07
forum: General Help
---

### Post by tkokkinos on 2010-10-07
Greetings,

I am a relative newbie and have tried other distros (Mandriva/KDE) and finally settled on Ubuntu 10.4.  I have it on a spare Dell Dimension 3000 and it really works great (had to add memory to 1Gb; it would not install properly).

Everything has been working fine for a month or so.  I was working on the machine last night, left to watch TV for a hour, came back and everything was frozen.  I could not get any  response from mouse, keyboard, chanting/waving bones and smoking sage over it, etc.  I just shut if off.

Today, I turned it on and got the message above (BusyBox). I typed help and tried some of the commands (not really knowing what I was doing). I rebooted several times to the same effect.  I did some Internet research to no avail and finally read the boot messages above.  I saw /dev/sda1 would not mount and instantly thought hardware fault.

The bottom line is that I used a boot CD I got off the net from [http://www.ultimatebootcd.com](http://www.ultimatebootcd.com) to boot onto the machine.  It turns out that I ran the diagnostics for my Western Digital hard drive; it found some errors, said they were repairable so I said "why not?" and hit YES.

I rebooted, my Ubuntu came up fine and works exactly like it did before the problem.  Evidently, that fixed my problem, very easily.

I do not know if others have tried this approach but the lengthy, nerdy (don't be offended) command line fixes were incomprehensible to me.  Luckily for me, this worked.  Maybe it's worth a try for others who experience the same situation.

---

### Post by quixote on 2010-10-09
Hey, thanks for letting people know.  It's always good to hear about fixes that bring machines back from useless!

(As the thread starter, you can mark this solved, which will also help people looking for answers.)

---


---
title: "Cannot shutdown"
date: 2010-09-25
forum: General Help
---

### Post by Blue_Mercury on 2010-09-25
I cannot shut down my computer anymore.
I am running an Inspiron 1100 and the problem appeared as soon as I upgraded to Ubuntu 10.04.
When I select shut down, the computer powers down and I can even hear the fan switch off. Then about 1 second later it powers back up.
When I select restart it does not power down, it just goes straight back into the BIOS.

Some people have said that upgrading the BIOS solved this problem.
I tried to upgrade my BIOS in order to fix the problem but unfortunately this is an older computer and my BIOS is already the newest version. So that did nothing.

Also, commands such as sudo poweroff and sudo shutdown -P now result in the same reboot process I described above.

I dual boot with XP and that seems to be the only way to get my computer to shut down without manually cutting the power.

---

### Post by io5cml4z on 2010-09-25
I used to have this problem with my old Windows 98 PC. Reformatting fixed the problem (Try that if nothing else works and you don't mind backing up all your files and data). Try going into the console and using
 > sudo shutdown -0 -h*Warning*: I did not test this, but there's no reason why it shouldn't work or screw up your PC, but still use at your own risk.

---

### Post by Blue_Mercury on 2010-11-06
I would prefer not to have to format my computer again.
I have found that I can shut the computer off by pressing the power button in the Grub menu, its still irritating but not enough to make me format my computer right now.

The command you gave me gives me this error:

shutdown: invalid option: -0
Try `shutdown --help' for more information.

---

### Post by evilsoup on 2010-11-06
Try 

sudo shutdown -h now

---

### Post by TBerk on 2010-11-07
> **evilsoup said:**
> Try 

sudo shutdown -h now


I too have this same trouble. (In fact I had it before too, but truthfully cant recall if it was as far back as 8.04 or since then...) 

The move from 10.04 to 10.10 beta, rc, and now full release has triggered the following behavior:

- Selecting SHUTDOWN from a pull-down menu, having a timer, and or having any given program do a Shutdown upon completion of task produces what looks like the normal shut down routine, once the screen goes completely black and you'd expect the power supply to kill the A/C it restarts and begins a startup routine.

The only way to completely shut the system off is to push the power button during that window of opportunity when the OS isn't loaded.

The sudo command, while a nice try, just initiates a shutdown, it won't help to keep it down.

Something ATX Power Supply related is wrong here. 

Keep in mind; this isn't "I can't Shutdown my Computer" as in shutdown does nothing; this is "My computer just RESTARTS when I try and Shutdown...".


TBerk
PS- I have two BIOS settings related to power management; something '1' & '3' but I'd have to reboot to get the exact wording. Tried either one; no difference but had helped in the past.

---

### Post by TBerk on 2010-11-07
OK, so I started paying more attention to this and I can relate the following;

- What I half remembered from the BIOS settings had to do with waking from power save/sleep mode, namely; 

>  
ACPI Suspend State = S1 or S3


btw, I tried both; made no difference in sustaining a full shutdown.  I also toggled the "Rapid BIOS Boot" option (It just means I was going to watch the memory count up during POST), no avail.

One last thing to add- one time last week I corrupted my boot files during this "press the Power Button while it restarts..." operation and lost the ability to boot from the Hard Drive. I was able to recover w/ the help of a LiveCD but I don't get my GRUB2 Menu anymore, it just boots right to the Plymouth (?) login screen.

Last night I tried:

```

$ sudo update-grub 

and

$ sudo grub-install /dev/sda

```

No effective difference.

TBerk

PS- I ran the following line in Terminal;

```
$ sudo update-grub**2**
``` 

And I regained my GRUB 'menu'.

This didn't change my 'wont shutdown, it restarts instead' trouble.

---

### Post by TBerk on 2010-11-07
Semi Interesting tidbit; 

I have the following entries on my GRUB2 menu; 

- 2.6.35-22
- 2.6.32-25  and
- 2.6.32.21

I choose the last one and while the login screen 'froze' in that it didn't respond to my mouse (well, trackball) nor my keyboard (couldn't login basically) a press of the Power Button worked as expected; the system timed out w/a 60 sec countdown and fully shutdown.

Hmmm...


TBerk

---

### Post by Blue_Mercury on 2010-11-07
As expected 
sudo shutdown -h now
didn't work.

I am considering reverting back to ubuntu 8.1 (Ibex) as this computer isn't getting any faster and I didn't run into any major problems with that distro.

---

### Post by TBerk on 2011-03-23
Thread Resurrection.

Anyone have anything new to add/try/advise?

I've been living w/ this for the last few months, almost half a year.

When its time to shut down, I cant just choose it from the Menu and walk away, I have to baby-sit the computer and push the power button at the right moment.

Otherwise it just reboots.



TBerk

---

### Post by Blue_Mercury on 2011-03-24
I gave up trying to fix this problem, but if you have any suggestions I would like to hear them.

I got a 'new' old crappy computer.
I am now running an AMD Athlon 64 3000+
However it has the exact same problem, I just hold the power button and try to time it with the actual shutdown process.

This is irritating but nobody seems to care enough to fix it.
I found this problem happens on 10.04 and 10.10

At some point I am going to get an actual new desktop and put an older version of Ubuntu on this one.

---

### Post by Blue_Mercury on 2011-05-08
BUMP

I am still dealing with this problem, its annoying and performing a hard shutdown on my computer daily is probably a bad thing.

Currently running an AMD 64 3000+  This problem exists on Ubuntu 9, 10, and 11

Does anyone have any ideas on why old computers will not shut down with new versions of Ubuntu?

---

### Post by TBerk on 2011-06-13
Bumpitty-bump, bump, bump.


Well, heres some 'new' news:

11.04 made t he trouble go away, only it would also fubar my 'Additional Drivers'. 

I've devolved back to 10.10 for now.


TBerk

---


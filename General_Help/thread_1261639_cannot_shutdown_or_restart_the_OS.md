---
title: "cannot shutdown or restart the OS"
date: 2009-09-09
forum: General Help
---

### Post by ChipWolf on 2009-09-09
My notebook runs Ubuntu 9.04 32bit, recently i cannot shutdown or restart the OS ,every time the screen stoped at the process "Asking all remaining processes to terminate..." then do nothing , I HAVE TO CUT OFF THE POWER, what a thing!

---

### Post by BslBryan on 2009-09-09
Usually if you wait for a while, it will eventually end all processes.  

However, if you do not have any time for that, open up a terminal via Applications --> Accessories --> Terminal and type 
```
sudo reboot now
```

or
```
sudo shutdown -h now
```

And that should force a reboot or power down. :-)

---

### Post by ChipWolf on 2009-09-09
> **BslBryan said:**
> Usually if you wait for a while, it will eventually end all processes. 
 
However, if you do not have any time for that, open up a terminal via Applications --> Accessories --> Terminal and type 
```
sudo reboot now
```
 
or
```
sudo shutdown -h now
```
 
And that should force a reboot or power down. :-)
 i don't think it need sometime to end all processes, it stoped there, once i had waited for  a long time but it still was ending all processes. there must be someting wrong.

---

### Post by BslBryan on 2009-09-09
What are your computer's specifications?

---

### Post by ChipWolf on 2009-09-09
> **BslBryan said:**
> What are your computer's specifications?
my notebook type: acer 5520g
ubuntu 9.04 32bit up to date.

---

### Post by P4man on 2009-09-09
You're not alone it seems:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298754](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298754)

Keep an eye on that thread for a fix, or wait for 9.10 :s

---

### Post by ChipWolf on 2009-09-09
> **P4man said:**
> You're not alone it seems:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298754](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/298754)

Keep an eye on that thread for a fix, or wait for 9.10 :s
bad luck man, i will wait 9.10.(Imagining that every day i was forced to press the power button a little longer time to cut off the system power, it does damage to my Notebook. can somebody make a fix quickly?)

---

### Post by jocko on 2009-09-09
> **ChipWolf said:**
> bad luck man, i will wait 9.10.(Imagining that every day i was forced to press the power button a little longer time to cut off the system power, it does damage to my Notebook. can somebody make a fix quickly?)
Instead of using the power button, try pressing these key combinations (in this order, and wait a few seconds between each to let it finish):
Alt+SysRq+r ## makes the kernel grab the keyboard
Alt+SysRq+e ## Ends all tasks
Alt+SysRq+i ## Kills any remaining tasks
Alt+SysRq+s ## Syncs the file systems (finishes any write operations)
Alt+SysRq+u ## Unmounts the file systems (and remounts / as read-only)

Finally, to power down the system:
Alt+SysRq+o
Or, to reboot:
Alt+SysRq+b

If you do this instead of using the power button, your file systems should be perfectly safe from damage.
To remember the key combinations:
**R**aising **E**lephants **I**s **S**o **U**tterly **O**rdinary (power **o**ff)
Or:
**R**aising **E**lephants **I**s **S**o **U**tterly **B**oring (re**b**oot)

---

### Post by P4man on 2009-09-09
> **ChipWolf said:**
> bad luck man, i will wait 9.10.(Imagining that every day i was forced to press the power button a little longer time to cut off the system power, it does damage to my Notebook. can somebody make a fix quickly?)

It won't damage your machine at all. It might cause problems with the filesystem if its not unmounted properly, but afaict, it does close most things orderly.

Some of those ppl also report pressing a few keys (any keys, even shift) a few times does make it shut down. Perhaps worth a try.

---


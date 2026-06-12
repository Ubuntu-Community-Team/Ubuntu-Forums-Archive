---
title: "Error file not found, error you need to load the kernel first"
date: 2010-07-28
forum: General Help
---

### Post by ktechman on 2010-07-28
I experienced an issue this morning on my triple boot (Lucid 64, Windows XP, Lucid 32-pae) after the latest kernel update the machine rebooted fine so I removed the old kernel through Synaptic and then restarted, I received two error messages, > Error: file not found 
Error: you need to load the kernel first

I looked around the forums and found a few instances some were related to Wubi and some where saying it had to do with how grub is numbering the hd entries.  My solution was to boot into the 64-bit working kernel and run 
> sudo update-grub

and all was solved. I have run into other similar issues with my laptop which runs (Lucid 64, Windows Vista, Hardy 32 and Lucid 32) where grub moved another kernel from the top of the list to the bottom and when I tried to boot into the kernel that was moved to the bottom of the list the desktop froze.  I also repaired this with an update to grub from the Lucid 64 kernel.

---

### Post by cherrick on 2011-02-24
MY GOOD MAN!!!!

I have been tweaking and stumbling around for 3 days trying to get this up and running:

sudo update-grub 

sudo update-grub                      

sudo update-grub                      

THANK YOU SO VERY MUCH!
:guitar: (YOU ROCK!)

---


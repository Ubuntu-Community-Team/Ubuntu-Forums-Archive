---
title: "Fujitsu Seimens - Amilo won't boot"
date: 2011-08-29
forum: General Help
---

### Post by F.G. on 2011-08-29
hello everyone,

my dad's laptop is a Fujitsu Seimens Amilo.  it's quite an old one, with only half a gig of ram and several previous owners (including myself).
until recently it dual booted with ubuntu 10.04 and Windows XP. so i just tried to boot it into Windows. it got to the windows logo and restarted.
so i thought i'd reinstall XP and install Meerkat or Ocelot to dual boot with it.
I put the recovery disk in reinstalled windows on the same partition it had been installed on previously.
then tried 'restart' (as is the normal procedure).
now the machine hangs at the initial: 

'Fujitsu Seimens - <F2> BIOS Setup / <F12> Boot Menu'
screen.  

i don't suppose that anyone knows a way to fix this, as i now can't run a live disk/usb?
my thoughts were to take out the HD and format it with another computer / set it up as a bootable medium.  but i assume that this probably wont fix the real problem, which is that i now can't get it to boot anything.

thanks for any help.

---

### Post by daniel227 on 2011-10-17
i'm just having the same problem - i installed ubuntu and now my "new" amilo a1645 doesn't start anymore, hangs on the very first screen, no booting from cd, nothing. it does react to ctrl+alt+del (restart).

only when i remove the hard drive can i even boot from cd.

i'm checking amilo forums right now.
i even updated the bios from 1.02c to 1.05c which seems to be the last for this machine, but it changes nothing.

i'll do some more checking, but for now i bump this, mayb someone can help?
thx.

---

### Post by daniel227 on 2011-10-18
hello f.g.,

are you still working on this?
my solution is this:
(how i got there is a long and painful story)

first you need a cd or sth other than hard drive to boot from, which contains some form of linux. i happened to have a rescue linux cd, but the installation disk might work also.

take out the hard disk.

boot the linux (it should work now).
as soon as the boot-up process is past the bios, but before linux gets loaded, plug in the hd (in my case it was easy because the cd presents me with a grub-like menu waiting for my input).

at a root prompt, type this:

dd if=/dev/zero of=/dev/hda bs=2000 count=1

this erases the first bit of the hd completely, it means you can't access the data on it anymore, which basically means it's lost. the data, not the hd.

after that you should be able to boot again with the hd in.
i'm at this point right now, reinstalling linux. we will see if i'm able to boot when it's installed.

greets,

daniel

---

### Post by F.G. on 2011-10-18
Hi daniel227,   thanks for your reply to this thread, I haven't actually tried to figure out the Amilo issue for a while (the computer has just been shelved for now).  in due course I'll have a go with your solution, and hopefully it will work. I hope you managed to get your machine fixed (mine's pretty old, so its no great loss if I can't fix it). good luck, and I would be interested to know the results.    f.g.

---

### Post by daniel227 on 2011-10-18
hello f.g.,

yes it worked.

i restarted a couple of times just to make sure, but it's really ok now, natty narwal installed.
when i first installed, i deleted and created partitions by hand (and mayb did sth wrong) and the bios (amiloforums say it's buggy) didn't like it and just jammed.

kinda my fault, but the bios shouldn't react to that.

i hope this helps.

d.

---


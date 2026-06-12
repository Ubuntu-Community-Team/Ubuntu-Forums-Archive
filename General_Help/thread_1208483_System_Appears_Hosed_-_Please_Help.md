---
title: "System Appears Hosed - Please Help"
date: 2009-07-09
forum: General Help
---

### Post by TrophyNinjaShrub on 2009-07-09
Short version:
Basic utilities (ln, grep, more) stopped working, error along the lines of:
Cannot execute binary file /bin/ln
Tried re-installing them.
Package manager has errors, but some started working again.
Tried rebooting.
Computer no longer boots.

(on Hardy, amd64 in case that matters)

Long version:
Ok, so I was trying to build codelite from source. It wasn't finding the include files for wxWidgets (turns out that wasn't the real problem anyhow...) so I decided to give it a symbolic link to help it out.
After I started typing the ln command I wanted to go search and make sure I was linking to the right place. So I did a highlight, copy of the command. Found the correct path, and then did a paste hoping to finish it.
I had accidentally also copied the end-of-line. It executed ln with both paths unfinished (yeah, I don't always type things left-to-right) - meaning they referred to existing directories.
Inside the one directory (the one named as a link) there appeared to be a new, broken link. I tried deleting the link. Tried the command again. This is when I discovered ln no longer worked.

When I say the package manager had errors... it looked like it was trying to use gzip, which sort of makes sense. But gzip not only was throwing error return codes - it was spitting out nonsense. The package manager appeared to be attempting to execute some of this gobbledygook.
The package manager in question is usually Synaptec, but I also tried GDebi... and I think dpkg. Don't they all just refer to the same library or some such anyway?

Tried re-installing gzip. Annoying thing was, gzip not only got called during its own installation (and thus it failed for that reason) it appeared to still be attempting coreutils! This is after ln came back online, but of course coreutils was still failing.

Starting the computer now begins as normal, but then it goes into some messages I don't recall seeing before. They're referring to various daemons - for each one it [mentions some file that cannot be created because it exists, and then chowns it] for a few files. Right after it chowned something or other for the system log daemon (forgive my forgetfulness of names - I'm new to Linux) it just hangs there.

I guess my next step is to get some sort of boot disk? I'm pretty sure this computer attempts to boot from USB before the hard drive and I have a memory stick with me now(at work). So let me know if you know where I should find one.

And then I'll do something to try to clean up the system? I'd rather not have to re-install the OS. I've never (successfully) installed any OS. But I definitely don't want to wipe the hard drive clean - I want my personal files.

Also, is there something I can do to prevent this from happening again? I didn't think ln -s was all that dangerous!

---

### Post by sdowney717 on 2009-07-09
yes, you can run your compiles and play around in a Virtual Machine such as virtualbox or VMWare server. That way if you destroy your "system" all you have done is destroy the virtual image.

as far as getting your system back, it might be best to just reinstall the OS.

---

### Post by TrophyNinjaShrub on 2009-07-09
What would be the easiest way to reinstall the OS, seeing as I don't have the CD or a CD burner available?

As for the VM - that's true, it would make things safer. I tried VirtualBox for Checkpoint VPN so I could run all the crap they wanted me to run as root without worry, not worry about what the virus protection was going to do, etc..

The problem with a VM is that in order to get it to do anything meaningful I have to give it nearly half the memory of my computer. It's not a very powerful computer. Obviously this hugely bogs it down, and makes just about every program annoyingly slow, and/or crashing. Since compilation is such a big part of what I do with my computer doing it in a VM would mean I'd be in sluggish hell just about all the time. I do appreciate the suggestion, though.

---


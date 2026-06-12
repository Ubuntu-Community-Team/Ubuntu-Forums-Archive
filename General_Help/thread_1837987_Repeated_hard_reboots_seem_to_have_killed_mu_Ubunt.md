---
title: "Repeated hard reboots seem to have killed mu Ubuntu...?"
date: 2011-09-02
forum: General Help
---

### Post by t0p on 2011-09-02
I have recently had problems trying to retrieve files from a broken external HDD.  I downloaded an .iso for Parted Magic, but it wouldn't start, just froze at 

```

Loading /pmagic/bzImage

```

Anyway, because of the repeated freezes, I have turned the computer off then on again using the power button, which I know isn't a good idea but I saw no other option.  As the file system is ext4 I thought it'd be okay.

But it seems that *something* has harmed something somewhere, because when I try to turn the computer on normally now I get a BusyBox screen.  It says:

```

No init found.  Try passing init=bootarg.
BusyBox v1.13.3 (Ubuntu 1:1.13-3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands

```

I am posting this thanks to an Ubuntu 9.10 Live CD I had lying around.  But I want to get back to my regular Lucid system.  Is it the repeated hard reboots that has done this to my computer?  What can I do to resume usual service?  Thanks.

---

### Post by t0p on 2011-09-02
Hoho!  Sorry about that, all the probs I've been having lately just sent me into a tailspin of panic.  After posting the previous message, I did some googling (like I should have done in the first place) and found all I had to do was run a simple **fsck**.  Did that, mended my file system, and now I'm back to using Lucid (though I'm still no closer to retrieving the data from the broken external HDD.

So, the moral of the story is simple: Google Is Your Friend.  That's a message I wish everyone else would take on board, then I get into a little problem and start running round like a little baby!  Google Is *My* Friend!  I really got to beat that into my own head.

---


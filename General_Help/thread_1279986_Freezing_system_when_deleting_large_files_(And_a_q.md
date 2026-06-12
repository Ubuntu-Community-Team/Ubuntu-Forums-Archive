---
title: "Freezing system when deleting large files (And a question about Gnome-do)"
date: 2009-10-01
forum: General Help
---

### Post by solwic on 2009-10-01
I've noticed that since I installed Ubuntu 9.04 using the ext4 file system, every time I try to delete a file larger than 500mb or so, the system locks up tight.  I assumed it was ext4; the problem doesn't exist with ext3.

But I've never ran 9.04 with ext3, and last night I stumbled across something odd.  In an effort to free up some disk space, I was using the CLI to ditch some big directories, and realized I could wipe out 1GB or more at a time, twice as quickly as with the GUI, and with no freezing.  I even created a 10GB TrueCrypt file, then deleted it, just to test the theory.  It worked like a charm.

Which makes me wonder:  is this an ext4 issue, or a bug in 9.04.  I know 9.04 has bugs; Brasero quit working with this latest version, and you can't load the home folder from Gnome-do anymore...but it never occurred to me that the delete file GUI was busted up as well.

Anybody else having these problems?  I mean, it's not a big deal now that I know the CLI bypasses whatever malfunction causes the freezing, but I'm curious.

Also, does anybody know how to edit the shortcuts that Gnome-do uses?  I added the "-notrayicon" option to my Opera browser link in the Accessories -> Internet menu, and it works, but I use Gnome-do almost 100% of the time, and I can't figure out how to add the option in Gnome-do.

Thanks.

---

### Post by Woody1987 on 2009-10-01
First issue:

i also use 9.04 with ext4 and have never had my system freeze when deleting large files all though it does slow down alot when i delete 2 or more large files.

---

### Post by solwic on 2009-10-01
> **Woody1987 said:**
> First issue:

i also use 9.04 with ext4 and have never had my system freeze when deleting large files all though it does slow down alot when i delete 2 or more large files.

Huh.  I have 9.04 with ext4 on three different computers in the house (three different types/makes/years), and all three have the issue.  None of them had it until the upgrade to 9.04 and ext4.

---

### Post by Giblet5 on 2009-10-01
Unless you have a very good reason to suspect that your / filesystem is corrupted, system freezes are (almost) always a hardware problem.

Are you overclocking your CPU or RAM?

Have you run memtest86 from the Grub menu (for at least two hours)?

There are a LOT of people running 9.04 and freezing isn't an issue, except where dodgy hardware is involved.

If you have a Windows partition, it's Very Very Smart to download Prime95 and run the test mode. If you have *any* problems with the CPU, its cache, or RAM, it will tell you all about it.

And, just because it's been working for six months, that doesn't mean it's working now. Even out-of-the-box, Big-Name, PCs are unlikely to have perfectly correct timing and, when they don't, freezing is the kind of thing you expect it to do.

---

### Post by solwic on 2009-10-01
> **Giblet5 said:**
> Unless you have a very good reason to suspect that your / filesystem is corrupted, system freezes are (almost) always a hardware problem.

Are you overclocking your CPU or RAM?

Have you run memtest86 from the Grub menu (for at least two hours)?

There are a LOT of people running 9.04 and freezing isn't an issue, except where dodgy hardware is involved.

If you have a Windows partition, it's Very Very Smart to download Prime95 and run the test mode. If you have *any* problems with the CPU, its cache, or RAM, it will tell you all about it.

And, just because it's been working for six months, that doesn't mean it's working now. Even out-of-the-box, Big-Name, PCs are unlikely to have perfectly correct timing and, when they don't, freezing is the kind of thing you expect it to do.

Thanks for the insight.  I find it highly suspect that three computers - two desktops and a lappy, all different ages - develop hardware issues at the same time; a time which, also, coincides with the installation of a new OS and a new filesystem.  

No overclocking, no Windows partition, and no malfunctioning hardware.  I'm tempted to reinstall 8.10 with ext3 just to verify what I already know is true:  the system won't crash when deleting big files.  Also, if it was hardware related, the CLI would cause the crash, too.  But it doesn't.  Running "rm -rf file" will take out 10GB files without a hiccup; the same tasking using the GUI freezes the system.

But that's all beside the point; I'm not trying to fix the problem because I've already done that (using the CLI, which is faster and more efficient anyway).  I was just curious if anybody else was having the issue, or if this is something that would get passed off as hardware related until three or four versions down the road when the bug is fixed.  

But I digress.  Thanks for the input.  :biggrin:

---

### Post by Giblet5 on 2009-10-01
I just finished creating 5 50G files deleting them and posting this from a 9.04 box with ext4 filesystems.

This is a Q6600 overclocked to 3.40GHz, Seagate drives with 32MB cache.

Assuming your hardware is 100%, it's not reproducible with the available information. Maybe it's an issue with swap space?


Just did the same test on a 9.10 box and another 9.04 box, both w/ext4.

I suspect hardware. Your mileage will vary.

I'll sell ya this one for ... a MILLION dollars! ;)

---

### Post by solwic on 2009-10-01
> **Giblet5 said:**
> I just finished creating 5 50G files deleting them and posting this from a 9.04 box with ext4 filesystems.

This is a Q6600 overclocked to 3.40GHz, Seagate drives with 32MB cache.

Assuming your hardware is 100%, it's not reproducible with the available information. Maybe it's an issue with swap space?


Just did the same test on a 9.10 box and another 9.04 box, both w/ext4.

I suspect hardware. Your mileage will vary.

I'll sell ya this one for ... a MILLION dollars! ;)

Heh.  I don't know what it is.  It's not hardware, I know that.  Unless I've experienced the craziest case of bad luck and coincidence in the history of the universe.  Besides, the CLI doesn't crash the system, only the GUI delete.  

Doesn't matter, though.  I'm using the CLI more and more these days anyhow, so I'll just write this one off as "unsolved".  

Could be swap though, I guess, though nothing is different.  Using the same 3gb for swap that I always do.

Ah well.  Thanks again.  :)

---


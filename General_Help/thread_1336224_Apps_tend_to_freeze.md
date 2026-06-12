---
title: "Apps tend to freeze"
date: 2009-11-24
forum: General Help
---

### Post by JugglinPhil on 2009-11-24
Recently several apps tend to freeze when handling bigger files. Those applications include Nautlius and Gimp; when I export a Gimp project to a .jpg that's about 200MB big, nautlius freezes usually as soon as I attempt to display the folder the picture is in, if previews are switched off it doesn't freeze until I actually choose to open the file.
Gimp also freezes sometimes, especially when saving as or opening .psd files, which is rather annoying.
Are there any settings that need to be changed in order for Ubuntu to be able to handle those files properly?
Thanks

---

### Post by akakingess on 2009-11-24
Have you tried something like Gnome Commander instead of Nautilus to see if you get the same result? Also, you should do a RAM memory check (preferably from within the BIOS) to check and see if you have a block that has gone bad.  Just a couple of suggestions to try.

---

### Post by prem1er on 2009-11-24
> **akakingess said:**
> Have you tried something like Gnome Commander instead of Nautilus to see if you get the same result? Also, you should do a RAM memory check (preferably from within the BIOS) to check and see if you have a block that has gone bad.  Just a couple of suggestions to try.

+1. Also, you might want to try opening the applications you are having trouble with from the terminal. Try and cause it to crash and see if an error is reported in the terminal. If so post it back here.

---

### Post by akakingess on 2009-11-24
> **prem1er said:**
> +1. Also, you might want to try opening the applications you are having trouble with from the terminal. Try and cause it to crash and see if an error is reported in the terminal. If so post it back here.

Thanks, that is actually probably even a better suggestion as launching from the terminal should tell us via logging, what exactly the program was doing when it crashed.

---

### Post by JugglinPhil on 2009-11-24
They don't crash they only freeze so there's no terminal output other than 'Killed' once I've force quit it.

---

### Post by Giblet5 on 2009-11-24
Are you low on free disk space? How much swap space do you have?

Running at less than 10% free disk space can cause a logarithmic increase in disk thrashing during file-writes (can look like a freeze, but a LOT of patience will result in eventual success).

10% free = Great
5% free = Noticeable degradation
2% free = OMG, kill me now
1% free = Just do those fourier transforms on paper - it's faster

---

### Post by JugglinPhil on 2009-11-24
> **Giblet5 said:**
> Are you low on free disk space? How much swap space do you have?

Running at less than 10% free disk space can cause a logarithmic increase in disk thrashing during file-writes (can look like a freeze, but a LOT of patience will result in eventual success).

10% free = Great
5% free = Noticeable degradation
2% free = OMG, kill me now
1% free = Just do those fourier transforms on paper - it's faster
I've got almost 50% free space because I keep all my multimedia on an external drive. If you mean the swap partition, it's 5.55 GB.

---

### Post by Giblet5 on 2009-11-24
Well, that's not it.

How stable is your system? Can you run memtest (from Grub menu) for four hours w/o errors?

A timing glitch on the second bank of RAM can cause intermittent problems during heavy lifting.

Have you examined ~/.xsession-errors? /var/log/messages?

---

### Post by JugglinPhil on 2009-11-24
> **Giblet5 said:**
> 

Have you examined ~/.xsession-errors? /var/log/messages?
No I haven't, what should I look out for?

---

### Post by akakingess on 2009-11-25
> **Giblet5 said:**
> Well, that's not it.

How stable is your system? Can you run memtest (from Grub menu) for four hours w/o errors?

A timing glitch on the second bank of RAM can cause intermittent problems during heavy lifting.

Have you examined ~/.xsession-errors? /var/log/messages?

+1 on the mem test, I really think that's what you are looking for since file size/intermittent issue is the problem.

---

### Post by JugglinPhil on 2009-11-25
I'll give it a shot.

---

### Post by dddanmar on 2009-11-25
Have a look at the output of the following as well, both before getting to your scenario, and then while it is happening:

top (cpu% & mem%) 
free -m (used & free)

Depending on the results we might be able to figure if its a system issue or the applications.

Also, what filesystem is on the drive you are storing your images, ntfs shared with Windows? If so, do the same operation on your ext3/4 drive and see what happens maybe?

+1memtest86

---

### Post by akakingess on 2009-11-25
> **dddanmar said:**
> Have a look at the output of the following as well, both before getting to your scenario, and then while it is happening:

top (cpu% & mem%) 
free -m (used & free)

Depending on the results we might be able to figure if its a system issue or the applications.

Also, what filesystem is on the drive you are storing your images, ntfs shared with Windows? If so, do the same operation on your ext3/4 drive and see what happens maybe?

+1memtest86
 
Also, htop is sometimes easier to read/make out. Basically the same app just with some colors added to help differentiate what you are looking at.  Just a suggestion, but also pay attention to the PID # of whatever might be taking up more resources than needed, you can use that to kill the 'process' as well.

---

### Post by akakingess on 2009-11-26
Any luck on the memtest or looking at "top"?

---

### Post by JugglinPhil on 2009-11-26
Haven't come around to do it yet, quite busy at the moment. The files I'm working on now aren't that big anyway so the problem doesn't occur, but as soon as I get some more time I'll try it.

---


---
title: "Memory corruption"
date: 2011-04-15
forum: General Help
---

### Post by thegeomaster on 2011-04-15
Hi all,
recently, my 14-year-old cousin and his parents visited me. He liked computers a lot, so I gave him my laptop which was dual-booting &#8212; Windows XP and Maverick.
He seemingly ignored my suggestion to boot into WinXP but I decided there was no harm in it, I just assumed he'd use the computer for surfing the Internet. I typed in my password and gave him the laptop while I was in the other room. What I didn't know is that he was pretty experienced with working with Linux before.
Once, he asked me what would happen if you added some random data at the end of the RAM. I said that, if there was unused space in memory and you overwrote it &#8212; probably no harm would be done, as long as nothing was referencing the overwritten memory part.
Around 15 minutes later, he called me and said that the system wasn't responding.
Since there were a lot of suspicious daemons running in background (some of them didn't quite like my hardware), I thought it must've been connected to them, so walked to him and looked at the screen, just to discover the GNOME terminal opened and the following command being executed:
```
sudo cat /dev/urandom >/dev/mem
```Horrified, when I realized what he had done, I hit Ctrl+C as fast as I could, and then tried typing sudo halt. The terminal got stuck there, so I closed it to try shutting it down from the GUI. Needless to say, Gnome hung too, so I tried navigating to one of the ttys. The keyboard seemed to stop responding and I was unable to do it, so, given the state of the system and the inability to do a soft shutdown, I hit the power button and hoped for the best.
It turns out that he thought that the redirection would just append to the end of the file rather than trying to overwrite it, and he assumed that the memory wasn't full (which, I think, wasn't the case).
When I tried to boot to Ubuntu again, I was greeted by a part of the stack trace (I didn't see where it came from since it overflowed the screen), and the following text:
```

Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= bootarg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```And I'm given an access to a shell.
The filesystem looks in a miserable state. From what I can see, /sbin/ and /bin/ only contain a handful of items, /var/ contains only lock, /usr/ and /home/ are gone, and init does not exist.
When I try to shutdown the system, the kernel panics, gives me a blank stare and stops responding.
From what I can see, the only thing I can do now is to just reformat the partitions and reinstall Ubuntu. But I'd like to know if there's any way to just get my data back, at least some part of it, like my home folder.

Lesson learned: Never, EVER let your "technically savvy" cousin use your computer. EVER.

TL;DR: sudo cat /dev/urandom >/dev/mem was executed, the system stopped responding and the filesystem was in a chaotic state afterwards. Is there a way to get at least some of the data back?

Thanks in advance,
Geomaster

---

### Post by WorMzy on 2011-04-15
Your data is fine, what you're seeing is the [initial ramdisk]("http://en.wikipedia.org/wiki/Initrd").

Firstly, I suggest that you boot a liveCD and run fsck on the partition.

See if you can boot after that has completed.

Also, why was your cousin able to use sudo? You may want to consider changing your password if a 14 year old can guess it.

---

### Post by blind2314 on 2011-04-15
^ Do what the man says :)
 
Also, no offense, but he's not very technically "savvy" if he didn't even realize what he was truly doing ("omg I'm a hax04 because I watch t3h TV and see all the l337 stuff they do" doesn't count).

---

### Post by seawolf167 on 2011-04-15
Aye, run fsck as suggested above, move your data to an external drive, then do a complete reinstall.

If you want to let him borrow it again, setup a separate user account and give it very limited permissions - no sudo/root permissions or the password for it either!

Also, you can make backups with [Clonezilla ]("http://www.clonezilla.org")and if it happens again all you have to do is reimage back onto the hdd and everything will be back to exactly how it was when your imaged the drive.

---

### Post by thegeomaster on 2011-04-15
> **WorMzy said:**
> Your data is fine, what you're seeing is the [initial ramdisk]("http://en.wikipedia.org/wiki/Initrd").

Firstly, I suggest that you boot a liveCD and run fsck on the partition.

See if you can boot after that has completed.

Well, I'm still kinda new to Ubuntu and Linux in general. I had no idea that it was an intermediate file system :)
> **WorMzy said:**
> 
Also, why was your cousin able to use sudo? You may want to consider  changing your password if a 14 year old can guess it.
That's what bugged me the most. My password is 10 characters long and includes uppercase, lowercase, numbers and two punctuation marks :) But still he was able to sudo. Is there any way one can bypass it?
> **blind2314 said:**
> 
Also, no offense, but he's not very technically "savvy" if he didn't even realize what he was truly doing ("omg I'm a hax04 because I watch t3h TV and see all the l337 stuff they do" doesn't count).
I forgot to put "technically savvy" under quotes in the original post :D
> **seawolf167 said:**
> 
If you want to let him borrow it again, setup a separate user account and give it very limited permissions - no sudo/root permissions or the password for it either!

Also, you can make backups with [Clonezilla ]("http://www.clonezilla.org")and if it happens again all you have to do is reimage back onto the hdd and everything will be back to exactly how it was when your imaged the drive.
It was stupid of me to give him the primary account, but I thought, "he would be here for 30 minutes, what could a 14-year-old possibly do?".
I didn't make any backups since I didn't put a lot of important data there, but there were still some things I wanted to rescue.

Everyone, thanks for the suggestions, I'll boot from a flash drive and run fsck.

---

### Post by seawolf167 on 2011-04-15
With physical access to a disk, security is almost non-existent unless you have encrypted the contents.

Not saying that he did any of these in particular becuase I'm not sure what he did; but you can reset your root password with a LiveCD, browse, delete, rename folders/files with a LiveCD, if you left a root-authenticated terminal open he could have used that, etc.

At least you learned who to trust, right? Lol (oh... and to make backups :P)

---


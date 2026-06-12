---
title: "Can't get back into Vista"
date: 2009-12-07
forum: General Help
---

### Post by j-power on 2009-12-07
I have a problem I can't find even a hint of a solution for.

Yesterday I was deleting a partition from within Vista and, to my extreme regret, deleted my old Ubuntu partition, rather than the data partition I intended to. Later I rebooted the system and got... nothing but a GRUB error. I eventually figured what I'd done wrong and reinstalled Ubuntu from my USB backup, and GRUB now lists everything it used to.

Unfortunately when I try to boot into Vista it goes to the Windows logo with the scrolling bar, then dumps to a blue screen for less than a second, and finally reboots. When I go into system repair mode it doesn't list any Windows installs, I can't boot into safe mode, and when I try to use system restore it tells me there are no restore points.

This is beyond my expertise to repair and simply wiping out the data on the windows partition is not an option. If there's a way to reinstall Vista without losing things then that's fine, but I'd prefer a more elegant solution.

---

### Post by lisati on 2009-12-07
It sounds like you might need to get hold of a Windows disk suitable for your machine to fix Vista - if you have a recovery partition and made a backup DVD using software that came on your system, that would be ideal. You'll need to use the "repair" option, not the install option. You'll then need to restore grub/grub2 to make your Ubuntu install accessible again. 

If you need any help with any of the above, feel free to ask questions. If I'm unable to help with further questions, others might be able to offer suggestions.

---

### Post by j-power on 2009-12-07
I have Ubuntu installed now. I'm posting this from within Ubuntu and I can even mount the windows partition and see all my existing data, so I suppose I could just back everything up (though that's a lot of music and photos to backup), but ideally I want a method to just repair Vista.

Like I said in my original post I have my Vista disk, but using it to perform repairs is failing. It doesn't even seem to recognize that Vista is installed.

---

### Post by fluffman86 on 2009-12-07
Boot to grub, select vista, and immediately start pressing F8 repeatedly.  You should probably have one hand on Enter, and the other on F8 to be fast enough.

Once you get the Windows options screen, you should see an option to disable reboot on error or system failure or something like that.  Select it, and you'll be able to get the info from the BSoD, which you can look up to hopefully fix your problem.

---

### Post by j-power on 2009-12-07
> **fluffman86 said:**
> Boot to grub, select vista, and immediately start pressing F8 repeatedly.  You should probably have one hand on Enter, and the other on F8 to be fast enough.

Once you get the Windows options screen, you should see an option to disable reboot on error or system failure or something like that.  Select it, and you'll be able to get the info from the BSoD, which you can look up to hopefully fix your problem.

I can't seem to get into safe mode this way. It ignores my key presses and still blue screens. How frustrating. What's the point of an error message if it's not on the screen long enough to be read?

EDIT: well I was able to get to the option screen and finally got the error code 0x00000024 which google tells me is bad news. Attempts to boot into safe mode result in the same bsod.

---

### Post by john newbuntu on 2009-12-07
Using your vista (or maybe even an XP) CD, boot to the command prompt.  Now, If you are able to get to this point, assuming that the C: drive was where you installed Vista, run the command:
[B]chkdsk c: /r
[/B]see if that fixes your problems.

---

### Post by j-power on 2009-12-07
Chkdsk found no problems. I really don't think it's a hardware problem. I'm really confused since GRUB worked fine until I reinstalled it with Ubuntu.

---

### Post by Tumblweed on 2010-01-01
I'm having a similar problem I had vista on my system installed ubuntu but let the installer partition the drive now every time I try to boot to windows it has to do a system restore to boot. any advice as to where to start to find the problem? btw both seem to run fine once booted.

---

### Post by Mark Phelps on 2010-01-01
Tumbleweed:

You already have a thread dealing with your problem -- which is very different from this problem, so please don't hijack this thread.

---


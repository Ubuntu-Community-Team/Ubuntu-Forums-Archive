---
title: "hibernation and swap usage"
date: 2012-03-05
forum: General Help
---

### Post by dresnu on 2012-03-05
I'm running ubuntu 11.10 on a dell laptop and after 3-4 hibernation cycles (switch off-resume) I can no longer hibernate because there is not enough free memory in the swap partition. I have seen quite few threads and posts regarding this issue and the most common suggestion seems to be to enlarge the swapfile in order to be able to hibernate multiple times though I don't think this might solve the problem.

The issue I'm experiencing is that after each resume the swap is not cleared and so at the next hibernation phase more used space gets accumulated which at last ends up feeling the swapfile and giving the "not enough free space on swap" error at the n-th hibernations. I understand that by making the swap partition bigger there would be more space but I believe that I would still reach a point where there is no more free space after a given number of hibernation.

What I would like to know from this thread, and have not found an answer anywhere else, is to understand if this behavior (accumulating used swap space after the hibernation) is normal and common to other users too. If that is not a bug then it means infinite (or at least more than 5 in my case) hibernations are impossible to achieve in ubuntu.

---

### Post by An Sanct on 2012-03-05
It is normal to use 2* ram size for hibernation swap space, but it has to be freed after exiting hibernation.

In other words, your swap is not being correctly freed after the machine reenters a working stadium. Check the logs and see what is happening, it has to be there somewhere (your post is not clear enough to make an assumption...).

---

### Post by dresnu on 2012-03-05
Thx, which logs do you suggest monitoring?

As for the swap=2*ram size I had read about this rule of thumb but I didn't take it into account when installing(some years ago swap space used to be a fraction of the ram :-).
I thought I'd try to solve this issue without changing the swap size yet, because as you point out it seems to be leakage problem.

---

### Post by An Sanct on 2012-03-05
I have my logs cleared out at every boot (this is the way I see fit for me ;)) but there is a nice readme in the man pages, the online version being [here]("http://manpages.ubuntu.com/manpages/hardy/man8/pm-action.8.html"), where a "PM_LOGFILE" option is discussed, this being the log, where Power Management (PM) writes to. Check that through.

PS. now disks are huge :) enjoy more swap space and keep in mind, that for hibernation purposes it has to be in one piece - ie. one single 2*ram piece of swap space. Hibernation basically unloads your ram into swap, just to load it back up on "startup" and give you the feeling, you never un-powered the machine.

---

### Post by dresnu on 2012-03-13
Thanks An Sanct for the link to the documentation.

I expanded the swap partition to 8GB but that didn't solve the problem. As I was expecting after a given number of hibernation cycles the swap was filled anyway and I couldn't hibernate anymore.

I solved by changing the suspension agent to uswsusp ([https://help.ubuntu.com/community/PowerManagement/Hiberate]("https://help.ubuntu.com/community/PowerManagement/Hiberate")) as kernel level suspension was creating the issue for me.

Now my swap space gets freed after waking up (as it should be) and also uswsusp seems to be a more advanced solution anyway.

---


---
title: "need a hand- Randomly stopped booting"
date: 2006-04-18
forum: General Help
---

### Post by DrewThePirate on 2006-04-18
Hi everyone. Well, here I am on a Windows system for the first time in months, asking you guys for help. I've looked around without much success for an answer to my problem. Here it is:

I'm using Ubuntu 5.10 on a standard Dell "Space Saver" type of box. I've never had any problems like this before, and I've been using Linux for five or six months now. Last night everything was working great. Limewire gave me an error saying it didin't have permission to write to /Shared, where it has always had permission to write. That was the first sign of trouble, but I didn't really think anything of it. I was more concerned about the fact that Firefox wouldn't load, but I think that may have been an unrelated problem. To fix it, I figured I would just reboot my system.

That may have been a mistake. I wasn't really paying attention, but the next thing I know, my computer is in some sort of terminal mode. I don't know enough to actually understand why, so guess what? I just rebooted again. I guess I used Windows long enough to think that rebooting fixes anything.

Well, now my computer boots as far as the Ubuntu loading screen. It passes "Loading Modules" and "Initializing /dev."

Then it hangs on "Mounting Root File System."

I assume this is bad.

I left it there all night, so I don't think it's going anywhere. I am by no means a Linux expert, and I really don't have any idea what could possibly have happened. I havn't changed anything important recently, in fact, I think the only time I've sudoed was to move a file to my web server. I don't understand what could have happened.

Any and all help on this one is appreciated. Reinstalling Ubuntu is not out of the question, as there isn't anything really important stored on my system that I don't have backed up. I just want to understand what went wrong, in my never-ending quest to learn more about Linux.

Thanks a lot.

---

### Post by fmo on 2006-04-18
If you haven't updated your kernel (or applied a kernel security update) I suggest that you use a live boot cd to access your system and run a "fsck" to check the state of your Ubuntu partitions.

---


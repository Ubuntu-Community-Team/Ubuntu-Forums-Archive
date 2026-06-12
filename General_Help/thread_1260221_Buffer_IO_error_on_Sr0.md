---
title: "Buffer I/O error on Sr0"
date: 2009-09-07
forum: General Help
---

### Post by Admiral Yi on 2009-09-07
Hello,
Recently I have found i'm unable to play Audio CDs on Ubuntu 8.10. When I look at the disk in nautilus it shows the audio tracks there, but it wont play them. Rhythmbox just tells me theres no tracks to play. Then I noticed that when I was starting up the first thing that happened was a load of errors saying 'buffer I/O failure on dev Sr0' (I can get you an exact transcript if you want, but I dont think the exact errors are that important).

My first though was that it was a hardware problem. But I booted up my windows partition and the CD worked perfectly. Can anyone tell me how to fix this?

---

### Post by P4man on 2009-09-07
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266951](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266951)

from that thread, a few things you could try: update your kernel. 
Or add "all_generic_ide" as kernel parameter. If you're not sure how:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

should that solve it, read the section below to permanently apply that parameter;

---

### Post by Admiral Yi on 2009-09-07
Thanks for that, I will try that a bit later and see what happens. If anyone else know anything, please post.

EDIT: Nope, didn't work. How would I go about updating the kernel? Is there a newer kernel in 9.04? If there is then maybe now is a good time to upgrade.

---

### Post by P4man on 2009-09-07
new kernels are automatically installed with the rest of the updates. not sure what the latest stable kernel of jaunty is, I think 2.6.28-15? Not sure (im on Karmic alpha here). Find out what you have by typing:

```
uname -a 
```

If you did all updates, you should have the latest stable kernel though.

---

### Post by Admiral Yi on 2009-09-07
That could be why, I never install updates (very lazy of me I know). Ill install them, see if that helps.

---

### Post by Admiral Yi on 2009-09-08
I've installed the updates,and its (half) solved the problem. Before, a load of the rros ame up before it started booting, and then again later during the boot. Now, the first set of errors are gone, but the next set (which I belive come up under 'loading devices' or something similar. Sorry I can't be more exact, it went by a bit fast) are still there.

Any more ideas on how to fix this once and for all?

---

### Post by P4man on 2009-09-08
go to system > administration > log file viewer

you can scroll back and copy/paste the error messages here.

---

### Post by Admiral Yi on 2009-09-09
I have attached a picture of the error messages in the logs. The selected line and above are all the messages I see at boot. I don't see the other ones, but evidently they're the same problem.

---

### Post by P4man on 2009-09-09
File a bug report, or add your report to this thread:
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/419124](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/419124)

And change the status to "confirmed"

---

### Post by Admiral Yi on 2009-09-09
Will do! Thanks for all your help.

---


---
title: "Ubuno Completely Locks. HELP!"
date: 2009-09-27
forum: General Help
---

### Post by baudday on 2009-09-27
I have a serious issue. This happened for the first time the other night. I had left my computer alone for a while and when I came back to shut it down everything was completely locked up. The mouse wouldn't move, the keyboard doesn't work, nothing. So I did a hard reset and it's been doing it ever since. 

Sometimes it will do it while it's still on the loading screen, sometimes while switching from the loading to the login, in which case it's just black. Sometimes it will freeze as i'm typing in my login. Sometimes I get all the way logged in and then it freezes. I've actually been able to login and watch an entire movie before it froze, but then soon thereafter it froze.

I tried loading a previous kernel, and that seemed to work. I'm able to log in and use the computer without interruption. It's just when I try to load the most recent kernel that it freezes up. I'm at a loss for what to do, and can't seem to find any threads with this specific problem. Any help is appreciated.

---

### Post by baudday on 2009-09-27
Wow i apologize about the title. I'm typing on a laptop and didn't even double check that. haha

---

### Post by baudday on 2009-09-27
I'm aware I said Ubuno instead of Ubuntu, it was a typo. Please, I really need help on this!

---

### Post by baudday on 2009-09-27
NO ONE has ANYTHING on this? Like what could possibly cause this? NOTHING?

---

### Post by baudday on 2009-09-28
Well this sucks

---

### Post by P4man on 2009-09-28
File a bug report, and meanwhile keep using the older kernel ?

---

### Post by yeeeev on 2009-09-28
Can you post the output of /var/log/kern.log from a recent freeze?

I had the same issue this morning (once for now. Hope it stays that way), and similarities between the logs might be interesting.

---

### Post by Topsiho on 2009-09-28
Might be a memory stick giving up. You could try checking the memory using one of the options on a LiveCD.

Topsiho

---

### Post by baudday on 2009-09-28
```
Sep 27 15:27:48 Tank kernel: [   17.664039] end_request: I/O error, dev sr0, sector 0
Sep 27 15:27:48 Tank kernel: [   17.664046] Buffer I/O error on device sr0, logical block 0
Sep 27 15:27:48 Tank kernel: [   17.664050] Buffer I/O error on device sr0, logical block 1
Sep 27 15:27:48 Tank kernel: [   17.664053] Buffer I/O error on device sr0, logical block 2
Sep 27 15:27:48 Tank kernel: [   17.664056] Buffer I/O error on device sr0, logical block 3
Sep 27 15:27:48 Tank kernel: [   17.664058] Buffer I/O error on device sr0, logical block 4
Sep 27 15:27:48 Tank kernel: [   17.664061] Buffer I/O error on device sr0, logical block 5
Sep 27 15:27:48 Tank kernel: [   17.664063] Buffer I/O error on device sr0, logical block 6
Sep 27 15:27:48 Tank kernel: [   17.664065] Buffer I/O error on device sr0, logical block 7
Sep 27 15:27:48 Tank kernel: [   17.665639] end_request: I/O error, dev sr0, sector 0
Sep 27 15:27:48 Tank kernel: [   17.665642] Buffer I/O error on device sr0, logical block 0
Sep 27 15:27:48 Tank kernel: [   17.667734] end_request: I/O error, dev sr0, sector 4
Sep 27 15:27:48 Tank kernel: [   17.667738] Buffer I/O error on device sr0, logical block 1
```

That block is showing up a lot, and since it's my Inputs that are messing up, I think that could be the issue.

---

### Post by grturner on 2009-09-28
well from the look of it, sr0 is having Buffer input output errors. but /dev/sr0 should be an optical drive. Something is wrong with your CDROM drive or the new kernel is not meshing well with it. If you wanted to confirm that, If possible remove/disconnect the optical drive and reboot into the new kernel and see if it works.

---

### Post by baudday on 2009-09-28
will try that and report back. thanks

---

### Post by baudday on 2009-09-28
Haven't tried the CDROM suggestion yet, but just a bit of further info. When I try to enter recovery mode I sometimes get this error:

<1> BUG: unable to handle kernel paging request at 89c389e4.

Sometimes it gets past that point and gets into the recovery menu where I'm able to do everything until I try to "Resume normal boot." When I select that, I get that same error again. Any thoughts?

---

### Post by baudday on 2009-09-28
Happy to report I'm writing this message from the latest version of the kernel. Looks like when I upgraded something messed up with the fglrx drivers. I reinstalled them and now everything is working. Hopefully it doesn't lock up on me again soon. For now I'll leave this open just to be sure and then if it really is fixed, I'll come back and mark this thread as [SOLVED].

---


---
title: "error message: &quot;****FILE SYSTEM MOUNTED IN THE FUTURE****&quot;"
date: 2009-10-10
forum: General Help
---

### Post by Miki800 on 2009-10-10
I mounted with andLinux the wubi image I have of a newly installed ubuntu to checkout if grub is failing with a good reason, turns out the grub is fine (continuing from this thread: [http://ubuntuforums.org/showthread.php?t=1288013](http://ubuntuforums.org/showthread.php?t=1288013)).

anyways kde installation destroyed somehow (doesn't seem so, but facts says otherwise) my good grub configuration so I had to be prompt to a manual grub initiation.

after successfully doing so the booting process stopped violently and got some sort of error message saying that the file system is corrupt (wth?)
and told me to run manual fsck, I did that and then I got a message that sounds something like the title.

well... IT IS TRUE! (as I stated at the beginning here) the file system (wubi image) really was mounted somewhere in the future of after last time mounted by that ubuntu itself - which was last time it booted successfully.

but why the heck that should be a problem?
how would I fix it?

I ran fsck from the console I got, it identified an error asked me to fix it I said yes and it did, I ran fsck again and got no error messages.

before, when I first got auto-logged to that console I saw this message:
"""
rm: cannot remove '/forcefsck': ReadOnly bla bla bla...
A maintence shall will now be started
CONTROL-D will terminate this and re-try.
"""

so I thought I fixed the file system which somehow got corrupt
and pressed CONTROL-D only to repeat the exact same error discovery over and over again (I'm fixing it, trying to fix again to see it was fixed, pressing CTRL-D and it happens again and again)

this is pissy, how the heck am I suppose to fix that file system if the fsck fs-fixin-utility screws up by falsely telling me it got it fixed?



I tried running fsck on it from andLinux under XP again hoping this time will be the last but I believe it will only happen again, please help


oh and please help me restore grub too (link to the grub issue thread in the beginning of this thread)



damn threads are disappearing from the first page too fast, this forum is too bloated with unanswered requests and no one gets help that way

---


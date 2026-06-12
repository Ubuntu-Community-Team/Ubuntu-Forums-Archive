---
title: "Boot time message takes ~25 secs, may not boot at all"
date: 2011-07-20
forum: General Help
---

### Post by michaelg9 on 2011-07-20
Hello,
I have Kubuntu maverick with KDE 4.5, with kernel 2.6.35.
I have a little problem at boot time, after I select to boot ubuntu from grub menu, I get a black screen with the blinking cursor and it stays there for ~25 seconds. Then I get the normal logging screen
I'm trying to see if it's something I can solve, as it's taking valuable boot time, so I enabled boot logging described [here]("http://ubuntuforums.org/showthread.php?t=49925") but the boot log doesn't show anything. I've done everything instructed there though...
I'm thinking that it may be waiting for my cd drive to respond, as it's problematic, but I'm not sure. I've tried to find its module and blacklist it, but I can't find it in the loaded modules (I don't know if it's there but I just can't recognize the name, as there are some strange names when I list modules, that I don't understand what they are).
Just to add, there are some times that it will stay there and won't boot, so I have to reboot with Ctrl + ALT + Del
If anyone can help me I'd be greatful
Thank you very much:)

---

### Post by michaelg9 on 2011-07-21
Update:
I extracted the error from dmesg:
[drm:init_ring_common] *ERROR* render ring head not reset to zero ctl 00000000 head 02001000 tail 00000000 start 02001000
It seems to be a common error, searching for a solution at the moment, but if anyone knows it already I'd like to hear it

Update 2:
Ok, it seems that there are many cases of this problem, but I didn't find an  fix... It's a pitty because I think without it, my computer would boot extremely fast...
If anyone knows something I can try to solve it, it would be great
Thanks

---

### Post by michaelg9 on 2011-07-23
Upgrading to natty Resolved the issue... Guess it's a kernel problem...

---


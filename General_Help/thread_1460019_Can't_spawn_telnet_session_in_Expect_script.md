---
title: "Can't spawn telnet session in Expect script"
date: 2010-04-22
forum: General Help
---

### Post by jbankstonga on 2010-04-22
Greetings.

I am not new to Linux, just to Ubuntu. I am moving my migration forward and am trying to get my expect scripts tested and found one that no longer works. Quite simply, it spawns a telnet session to a router.

#!/usr/bin/expect 
set env(TERM) vt100 
set timeout 3 
set send_human {.1 .3 1 .05 2} 
set timeout -1 
# 
spawn telnet 10.254.3.232 

and that's it. The result of the script is that the command to spawn simply shows up on the screen like it is a puts command. On my older openSUSE system, it worked fine. I am running Ubuntu v9.10 desktop, and expect and its libs are patched to the latest rev, expect is 5.43.0.

Any thoughts on what might be wrong?

Thanks for any replies.

-Jeff

---

### Post by woody22075 on 2010-05-27
i am experiencing the same problem as well.  any thoughts?

m.

---


---
title: "Massive Memory Problems"
date: 2009-10-12
forum: General Help
---

### Post by /usr/bin/hacked? on 2009-10-12
When I first start up my computer, my ram only has a little used, and the swap has 0% usage. After it has been on for a while, however, it starts to eat through my swap. I have a fair amount of swap available, and it uses almost all of it. I do not know what is causing this. I am usually running compiz, firefox, thunderbird, rythymbox, pidgin, xchat, skype, chrome (once in a while), xmms (long live xmms!), and conky. all at the same time. This was never a problem for me in 8.10, as I could have all these programs open for a week straight and never go above 60% ram usage, and 0% swap usage, and my computer would feel responsive and fast. Now it's slow and sluggish and I think it has to do with the swap thing. I've included a pic of top, system monitor (memory in green and swap in purple, up at the top of the pic), and conky. I can get any other info you may need to help me fix this.
Thank you very much!

---

### Post by mechro on 2009-10-12
I would try running without compiz enabled and see what happens.

---

### Post by Johnny B on 2009-10-12
display swappiness
> sudo cat /proc/sys/vm/swappiness
change swappiness (temporary)
> sudo sysctl -w vm.swappiness=10
change swappiness (permanent)
> sudo gedit /etc/sysctl.conf
change **vm.swappiness=**

---

### Post by lensman3 on 2009-10-12
What does the "free" command say?

---

### Post by Giblet5 on 2009-10-12
That's a lot of swap in use...

I'd do ```
top -u $LOGNAME
```

Then hit 'shift-M' to sort by memory hogs.

Firefox is notorious for running away with RAM. It's using 857MB to type this whining and moaning you see here...

Is there something there that shouldn't be?

Are you pinning a mysql index in RAM?

---

### Post by zer0x on 2009-10-12
Hi,

Could you post the output of 'free -m'?

Cheers,
zer0x

---


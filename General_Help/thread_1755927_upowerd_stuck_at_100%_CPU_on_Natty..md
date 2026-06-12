---
title: "upowerd stuck at 100% CPU on Natty."
date: 2011-05-11
forum: General Help
---

### Post by pieroxy on 2011-05-11
Hi there,

I upgraded to Natty last week. Everything went fine and now, for about one hour, the upowerd process is eating up one core. 100% CPU stuck...

I have a quad core, so this is not a showstopper, but I'd still like it to go away. I could reboot for sure, but I guess it'll come back at some point.

Any idea?

---

### Post by BarakNaveh on 2011-05-28
Same issue here, Ideas?

---

### Post by veltzer on 2011-08-25
Same here. updated to latest ubuntu natty and upowerd is bugging me. Please also provide a workaround for this. I usually kill upowerd and it helps but then it pops to life again (possible some auto spawn thingy by dbus or something). I also cannot remove upowerd since many system components depend on it. Please provide a workaround for disabling it too...

---

### Post by IT Support on 2011-08-25
I had same problem with natty and i  downgrade it, 
now i am heppy linuxoid with "Lucid" :guitar:

---

### Post by pieroxy on 2011-09-05
This issue hasn't popped up  for quite some time now. Any update from my fellow 11.04 users?

---

### Post by OwlBoy on 2011-09-09
I am also having this issue on Natty 11.04

I ended up running

```

sudo killall upowerd

```

---

### Post by Canned on 2011-09-24
Same problem here. :( (Natty 11.04)
Is it possible to prevent it from turning on 
permanently? I really start to regret that I upgraded from LTS. :(
Has this been oficially reported as a bug? We need to let developers know about it.
I know this process has something to do with power management, but
since we can kill it without any consequences, then we can go without it
altogether as well, huh?

---

### Post by LMendy on 2011-10-26
I'm having this issue on Ubuntu 11.10. Any other ideas besides just killing it?

---

### Post by pieroxy on 2011-10-29
Well. I just killed it and it popped up back. After a couple of times, it went away and I haven't seen the problem in a few month now.

---

### Post by mzoet2004 on 2011-12-01
[SIZE=2][FONT=Arial]I'm having the same issue (Ubuntu 11.04 - the Natty Narwhal ) - what's strange is that I have vmware workstation running a W7 host so I can sync my iphone.  If I don't connect my phone it appears that upowerd is quite.  If I connect my phone I see upowerd spike as well as iphone-set-info.  I've killed them both and will continue to monitor this issue.  I would not be surprised if it stays calm until I connect my phone again to re-sync...[/FONT][/SIZE]

---

### Post by NimoTh on 2012-05-06
The iPhone seems to be the issue. I am also on 11.04 (still) and have the same problem. Luckily, I don't really care because it's not my iPhone, so I usually don't connect it to my laptop.

---


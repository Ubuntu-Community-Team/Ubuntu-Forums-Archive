---
title: "why does swapping occur while 600MB cached"
date: 2011-04-12
forum: General Help
---

### Post by DLGandalf on 2011-04-12
While the title says a lot.

I have heavy swapping going top and free are indicating a lot free memory in cached form. Why does the kernel not use this memory instead of killing my desktop by swapping like crazy.

---

### Post by jmszr on 2011-04-12
DLGandalf,

About 2/3 of the way down: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) there is a section on "swappiness" and how to set it. 
It recommends setting it at 10.

Hope that helps.

---

### Post by oldos2er on 2011-04-12
How much RAM do you have?

You can reduce swappiness by adding the line ```
vm.swappiness=10
``` to /etc/sysctl.conf and either reboot or run **sudo sysctl -p**

More info here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by 3Miro on 2011-04-12
If you are currently using the files in the cache, then you are getting speed improvement for keeping it in RAM. If you are not currently using an opened program, you don't really lose form putting it in swap. 

Swappiness is a delicate balance that cannot have "one-size-fit-all" solution. If the default behavior is causing trouble, change it.

---

### Post by DLGandalf on 2011-04-12
I knew about the swappiness parameter and have experimented with it a lot, yet it seems to have nill effect.

I have 2GB of ram which I think should be plenty. I just think it's weird that pegging the memory results in an consistent cached value of 500+ MB. while my desktop with 4GB would just use the cached memory and then starts swapping.

---

### Post by 3Miro on 2011-04-12
This is on a laptop? The swap could be there because of "hibernate" option. Also, I think there was something about different swappiness depending on whether or not you are on AC or Battery. RAM takes power, Swap doesn't.

Are you sure the swappiness is causing trouble. I had problems on my laptop with Video, RAM, HDD, CPU, then it turned out that the machine was just weak.

---

### Post by DLGandalf on 2011-04-12
memory uses power indeed, used or not used, so that's not the issue.
I'm pretty sure it's actual swapping as my waiting time and used swapsize are growing during the opening or repainting of windows.

using 400MB of swap while having 500MB cached is ridiculous, but if no-one has a clue, I might have to ask the mailinglist guru's.

---


---
title: "Memory leak?"
date: 2009-07-06
forum: General Help
---

### Post by AnotherDave on 2009-07-06
Something is wrong, I'm going to call it a memory leak. It happens when I'm browsing. After about three hours, the cursor goes into thick Jell-o mode and memory use goes hyperbolic.

At first I thought it was my Opera browser, but it also happens with Firefox. It started soon after the new kernel updates.

Jaunty on 64 bit Athlon.

---

### Post by DeMus on 2009-07-07
> **AnotherDave said:**
> Something is wrong, I'm going to call it a memory leak. It happens when I'm browsing. After about three hours, the cursor goes into thick Jell-o mode and memory use goes hyperbolic.

At first I thought it was my Opera browser, but it also happens with Firefox. It started soon after the new kernel updates.

Jaunty on 64 bit Athlon.

Does it happen on more than one site, or just on one?

---

### Post by lovinglinux on 2009-07-07
I'm sorry, I guess I was tired and didn't noticed your are talking about memory and not CPU usage

---

### Post by AnotherDave on 2009-07-07
It seems to be a general problem, not specific to any site, and Flash was not being used. I can't even say that it was caused by the browser, although the six or seven times it's happend I have been browsing. 

For no good reason, the cursor just slows down, and my system goes catatonic. Wish I had more info to report!

---

### Post by lovinglinux on 2009-07-07
I'm sorry, I guess I was tired and didn't noticed your are talking about memory and not CPU usage

---

### Post by darthmob on 2009-07-07
try to use top or htop to find out what program is causing the problem. are you running openbox by chance?

---

### Post by lovinglinux on 2009-07-07
I'm sorry, I guess I was tired and didn't noticed your are talking about memory and not CPU usage.

Run the command **top** in the terminal and check how much resident memory Firefox is using. Something between 90 and 150 Mb is normal, but if it starts to use 400 - 600 Mb, then there is something wrong. I think the culprit is probably an extension. This was also happening to me a few days ago and the problem was FasterFox extension.

Check problematic extensions [here](http://kb.mozillazine.org/Problematic_extensions). Also visit the "Extension Optimization" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) for instructions on how to pinpoint the culprit.

Sometimes, when the memory cache is fully used, I also feel performance degradation, but this is not a Firefox issue. Most people will argue that memory not used is wasted memory, but I do use a command to clean up the memory cache and speed up things a little bit. The command is below:

```
sudo echo "Starting" && sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```

This command will not clean up resident memory used by Firefox, just the memory cache.

Another thing that might help is optimizing Firefox databases. Check the "Database Optimization" section of my tutorial for instructions.

---

### Post by Megrimn on 2009-07-07
> **lovinglinux said:**
> I'm sorry, I guess I was tired and didn't noticed your are talking about memory and not CPU usage.

Run the command **top** in the terminal and check how much resident memory Firefox is using. Something between 90 and 150 Mb is normal, but if it starts to use 400 - 600 Mb, then there is something wrong. I think the culprit is probably an extension. This was also happening to me a few days ago and the problem was FasterFox extension.

Check problematic extensions [here](http://kb.mozillazine.org/Problematic_extensions%3Cbr%20/%3E). Also visit the "Extension Optimization" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567) for instructions on how to pinpoint the culprit.

Sometimes, when the memory cache is fully used, I also feel performance degradation, but this is not a Firefox issue. Most people will argue that memory not used is wasted memory, but I do use a command to clean up the memory cache and speed up things a little bit. The command is below:

```
sudo echo "Starting" && sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```

Another thing that might help is optimizing Firefox databases. Check the "Database Optimization" section of my tutorial for instructions.

for some reason, the 'mozillazine' link includes a </br> on the end of it, and thus does not go to the correct page.  delete the '</br>' to go to the page.

---

### Post by lovinglinux on 2009-07-07
> **Megrimn said:**
> for some reason, the 'mozillazine' link includes a </br> on the end of it, and thus does not go to the correct page.  delete the '</br>' to go to the page.

Thank you. Fixed.

---

### Post by AnotherDave on 2009-07-07
Thanks for the comments. Twice I was able to bring up System Monitor which I have set up to view all processes. I saw no unusual CPU activity and I saw no process dominating. There was CPU power indicated in reserve.
 
What I did see was memory use ramping up, until it went to swap. Swap filled up about halfway, then memory came back down, and I was able to shutdown the browser, which brought things back to normal. This was just ordinary browsing, no Flash, and no extensions I can recall.

Again, this started happening after the recent kernel upgrades. I uninstalled Compiz recently too. This has happened with both Opera and with Firefox, so I don't think this is browser-specific. 

Hope somebody can use this info.

---

### Post by AnotherDave on 2009-07-12
It just happened again. Machine has been up for three days, with a normal 20% memory load, browsing with Opera when I clicked on a link and the machine became unresponsive. 

It took about five minutes to get the System Monitor to come up. What it showed was about 25% CPU and 100% memory, no paging this time. I brought up the terminal, entered 'top', and boom! everything popped back to normal.

Hope this info helps someone.

---


---
title: "GParted progress bar stuck"
date: 2010-08-19
forum: General Help
---

### Post by Ruairi on 2010-08-19
I removed my Ubuntu 10.04 partition from my hard disk with GParted because it didn't install properly and there were no solutions available. After I removed it, I set it up to extend my Vista partition into the unallocated space. It's been going for three hours so far (which I expected) but the progress bar is now stuck. The timer's stopped and everything; it's not increasing infinitely like when your internet cuts out when downloading something, it's just stopped. Here's a screenshot: [http://img716.imageshack.us/img716/606/screenshotqw.png](http://img716.imageshack.us/img716/606/screenshotqw.png)

I know to resist the allure of the Cancel button, but I don't really know what to do here. It's been sitting here for about half an hour with no sign of budging.

Any solutions or ideas of what the hell's going on are appreciated.

Cheers,
Ruairi

---

### Post by Ruairi on 2010-08-19
Update: it's still stuck. Hasn't budged an inch. Also, I can't access Vista from Computer, so it's still trying to do something with it. I do have my essentials backed up on an external hard disk, so it's not a matter of life and death, it's just an annoyance.

---

### Post by aeiah on 2010-08-19
open a terminal and see what ```
dmesg
``` tells you. if you cancel you'll most likely find the partition is corrupted, but if its crashed it'll be your only choice. you should be able to fix it though but you may find it easier to reinstall depending on your situation.

---

### Post by Mark Phelps on 2010-08-19
Sorry ... but it's a really BAD idea to use GParted to mess with Vista partitions. You run the risk of filesystem corruption if you do that.  And, if you turned off or cancelled before completion, that is pretty much a certainty.

At this point, you would need to boot into Win7 and run chkdsk to attempt to repair the filesystem.  If you have a Vista installation DVD, you can boot using that, select Command Line and use that.

If you don't have a Vista installation DVD, you're in really difficulty.  The site below has torrent links to where you can download Vista Repair CD images that you can use on another machine to create a burn a repair CD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by marco_polo99 on 2010-10-17
Slightly different problem--When I start Gparted it pops the window up, you can see is starting to scan drives then the window and program shuts down.  I'm running 10.10 on a Asus 1015PE Netbook

I tried completely removing Gparted and reinstalling, rebooting, I tried calling it from the terminal screen, etc., and always the same--it opens, starts to scans then disappears.

---

### Post by Mark Phelps on 2010-10-17
The original post dealt with problems trying to resize a Vista NTFS partition using GParted.

This doesn't sound like YOUR problem.

So, if that is the case, please do NOT hijackn this post for a different problem; instead, start your own post. You stand a better chance of getting replies for your problem that way.

---


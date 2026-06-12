---
title: "tried to upgrade ubuntu...can't start computuer now! Please Help!"
date: 2012-05-30
forum: General Help
---

### Post by thunderhouse on 2012-05-30
I tried to upgrade my version of unbuntu to 10.10. I had an old version on there for the past year. Now when I turn on my computer I get the following message:

**gnu grub version 1.98+20100804 -5ubuntu3.3**

4 options are given in a box below. 

I tried all 4 of the options given, none work. All say "The disk drive for / is not ready yet or now present. Continue to wait; or press S to skip mounting or M for manuel recovery."


I have no idea what to do.....PLEASE HELP!

---

### Post by raja.genupula on 2012-05-30
S (SKIP) takes you to the desktop , because i am also having the same issue but i am not caring it . 

if you hold the system like that message , what its giving to you ??

---

### Post by thunderhouse on 2012-05-31
if I hit S (skip) it says: 
 
mountall: Plymouth command failed
mountall: Disconnected from Plymouth

---

### Post by synapsys on 2012-05-31
This looks like a similar issue, although I can't guarantee its effectivenes:

[http://ubuntu.igameilive.com/2010/07/how-to-fix-plymouth-command-failed.html](http://ubuntu.igameilive.com/2010/07/how-to-fix-plymouth-command-failed.html)

You can always re-install. If you've got your / and /home on separate partitions, you can quickly re-install without borking your /home partition. I've found that with Ubuntu it's always better to install a fresh new version rather than to upgrade an existing one.

---

### Post by elliotn on 2012-05-31
i think its better to reinstall, backup your Home folder n other staff

---

### Post by elliotn on 2012-05-31
i always find upgrading with the alternate CD being the best way that over the net... CD upgrade is painless

---

### Post by raja.genupula on 2012-05-31
> **thunderhouse said:**
> if I hit S (skip) it says: 
 
mountall: Plymouth command failed
mountall: Disconnected from Plymouth

you have to see this 

[http://askubuntu.com/questions/132742/mountall-disconnected-from-plymouth](http://askubuntu.com/questions/132742/mountall-disconnected-from-plymouth)

---

### Post by thunderhouse on 2012-05-31
Thank you all for the suggestions. I re-downloaded ubuntu onto a flash drive. If I reinstall, will I loose the things on my hard drive? Unfortunately, I never got around to backing it up : (

---

### Post by Cheesemill on 2012-05-31
Also bear in mind that 10.10 has reached end of life and is no longer supported or receiving updates. You would be better of installing 12.04 as it is still supported for the next 5 years.

---

### Post by wilee-nilee on 2012-05-31
> **thunderhouse said:**
> Thank you all for the suggestions. I re-downloaded ubuntu onto a flash drive. If I reinstall, will I loose the things on my hard drive? Unfortunately, I never got around to backing it up : (

Yes it will overwrite 10.10 unless you use a new partition, but that live cd will allow you to access the 10.10 to pull out what you need.

---


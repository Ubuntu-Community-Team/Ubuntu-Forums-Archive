---
title: "OpenOffice.org Quickstarter Prevents Shutdown"
date: 2010-06-18
forum: General Help
---

### Post by Ubuntist on 2010-06-18
Since installing Lucid, I find that the shutdown button doesn't work (does nothing) if the OpenOffice.org quickstarter is running.  To shutdown I either have to kill the quickstarter or run shutdown manually from a terminal window.  Hibernation doesn't work either, although suspension does.

Anybody know how to solve this problem, aside from not running Oo.o quickstart in the first place?

---

### Post by wilee-nilee on 2010-06-18
I don't like the quick starter, I use this method to get it to load faster.
[http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)
Without the quick start and java.

---

### Post by ajgreeny on 2010-06-18
I have to agree with willee-nillee, unfortunately.

I always used to use quickstarter in the panel, and in previous versions of OOo it made a big difference in the speed of start up of OOo.  Now, however, with OOo 3.2, it is really not worth the hassle of the shutdown problem to save about 2 seconds, and that 2 seconds is usually only for the first, cold start of OOo.

As a sort of a workround I now have a launcher in my panel for the /usr/bin/ooffice executable, which goes to the main start screen of OOo; it's a bit of a compromise, but makes life just a little bit simpler for me.

---

### Post by wilee-nilee on 2010-06-18
> **ajgreeny said:**
> I have to agree with willee-nillee, unfortunately.


Don't you just hate when that happens.:lolflag:

---

### Post by ajgreeny on 2010-06-18
> **wilee-nilee said:**
> Don't you just hate when that happens.:lolflag:
I refuse to answer that on the grounds that I may incriminate myself!

As you probably realise, I meant "unfortunately" because I always found the quickstarter very useful, and now can't use it.  Very unfortunate!

Cheers willee-nillee!  See you around.

---

### Post by Ubuntist on 2010-06-20
Would it be possible to insert a line into .logout (or some other script file) that would kill the OO.o quickstarter?

---

### Post by ajgreeny on 2010-06-20
That would be nice wouldn't it, but I fear it seems impossible in Ubuntu 9.10 and 10.04 as you can not (as far as I'm aware) edit the shutdown command as you could in versions up to 9.04 using the **System -Administration-Login Screen** dialog. The configuration for this is now almost useless, but maybe in future it will be possible.

But of course, perhaps in 10.10 we will not need it, and quickstarter will not conflict with shutdown.

---

### Post by ahamedck on 2011-05-28
Hi all, 
I had also the same problem when i installed the synapse and it was quiet irritating to shut down the system. There was only one option by opening a terminal and putting 
$sudo init 0

now i found another solution.  steps are 
1. simply activate the synapse (by either from the menu Applications--> Accessories--> synapse, or putting an icon in the panel and clicking on it or by entering the key strokes for activating the synapse through key board--- the original key stroke was Ctl+space bar which i have changed to Ctl+.  (ie. period))
2. enter the keys shut in the synapse mini window . It will fill up the various search results in its sub window below.
3. just select the command you require - its all.

Happy synapse

Ahamed

---


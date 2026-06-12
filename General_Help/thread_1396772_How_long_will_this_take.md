---
title: "How long will this take?"
date: 2010-02-02
forum: General Help
---

### Post by Drools on 2010-02-02
I recently purchased 2 USB 1.5TB hard drives for my Popcorn hour. I want to clone the master drive to the slave drive using gparted on the Ubuntu livecd. I went through the motions, select source partition ---> copy, select destination partition ---> paste. Answer all the warning and click the green arrow (apply button).
How long should I expect this operation to take? I do not see a progress bar so I'm not sure it is even working?
 
Is it possible I did something wrong? Can I cancel the operation?
 
Thanks for the help guys.

---

### Post by jamesisin on 2010-02-02
It could take quite a while, especially from the live CD (since it's running entirely in RAM) which is much more dependent upon local resources.

Why are you using this particular method?  You could run several different operations from within an installed Ubuntu which would backup the data (and you needn't necessarily mirror the partition).

---

### Post by underquark on 2010-02-02
It's definitely a go-out-to-the-pub job.

---

### Post by 2hot6ft2 on 2010-02-02
> **Drools said:**
> I recently purchased 2 USB 1.5TB hard drives for my Popcorn hour. I want to clone the master drive to the slave drive using gparted on the Ubuntu livecd. I went through the motions, select source partition ---> copy, select destination partition ---> paste. Answer all the warning and click the green arrow (apply button).
How long should I expect this operation to take? I do not see a progress bar so I'm not sure it is even working?
 
Is it possible I did something wrong? Can I cancel the operation?
 
Thanks for the help guys.
Since you say 2 USB drives I'm wondering where the master/slave part comes in. But anyway I cloned my Laptops 250GB drive over to a 500GB drive using the dd command and it took about 8 hours. That's with 3GB of RAM using the livedvd (I use Ubuntu Ultimate Edition so it's a livedvd  instead of a livecd). That was just to clone the 250GB then came expanding the partitions to fill the 500GB drive. So:
250GB x 6 = 1.5TB
8hours x 6 = 48hours

So if you're cloning a 1.5TB drive I would expect it to take a couple days. dd doesn't give any indication that it's doing what you told it to either, you just have the activity light of the drives to tell it's busy.

When it finishes it will stop. dd would return to the command prompt. In gparted it would show it going back and forth at the bottom but no progress bar and it would show "All operations completed successfully" when finished if it was successful.

If there's a "Cancel" option then yes you can. I would reformat the TARGET drive after canceling it if it were me. Also it may take it a while to even cancel the operation.

If you're not cloning your operating system, just external to external then just do it from your running system and not from a livecd/livedvd and it should be considerably faster since your RAM would be available as well as your swap for use by the system.

---

### Post by pkm4o93 on 2010-02-02
If possible I would void the warranty and pop those sata drives in,and rid myself of usb 2.0 for these mega file operations.  But Im lazy and impatient. Im about to get a PCMCIA 2xsata for similar reasons.

---


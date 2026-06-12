---
title: "Defragmenting question"
date: 2010-11-26
forum: General Help
---

### Post by Habeouscorpus on 2010-11-26
Okay, I know Linux doesn't need to be defragmented, and Windows does. My Windows desperately needs a defragging, because it's sprawling all over the drive and generally making a mess of things. 42% fragmentation! (Yes, they are on the same partition.)

What I want to know is, will defragmenting the disk in Windows mess up the Ubuntu OS? I analyzed the disk before I did anything. The most fragmented files are all files in the Windows file system. 

(If you need more information, I can also include a copy of the report.)

---

### Post by matt_symes on 2010-11-26
Hi


> What I want to know is, will defragmenting the disk in Windows mess up the Ubuntu OS?

No

Kind regards

---

### Post by Hippytaff on 2010-11-26
When you say they are on the same partition, do you mean you used wubi to install ubuntu?

Either way defraging the window$ shouldn't affect ubuntu (as far as I know) <- caveat :-)

---

### Post by Habeouscorpus on 2010-11-26
AH! Lovely. It's really been ticking me off. Stupid inefficient file system. 

Yes, I did use wubi. (I didn't feel like messing around with boot disks, and I wasn't up for the task of partitioning... :P ) Took about 30 minutes, 20 of which were downloading the package. Wonderful experience.

---

### Post by lisati on 2010-11-26
> **Hippytaff said:**
> When you say they are on the same partition, do you mean you used wubi to install ubuntu?

Either way defraging the window$ shouldn't affect ubuntu (as far as I know) <- caveat :-)

Agreed. As long as the main Windows partition doesn't get horribly messed up in some way, I'm not aware of any risk to a Wubi installation from defragging. Having said that, it doesn't hurt to get in the habit of backing up important data from time to time.

---

### Post by Hippytaff on 2010-11-26
Something to bare in mind - when you do updates with Wubi, the updates sometimes break it. Also Wubi is meant for evaluating ubuntu. If you intend using ubuntu long term it is a good idea to do a 'real' install :-)

> 
Having said that, it doesn't hurt to get in the habit of backing up important data from time to time.


indeed

If you mark this thread as solved in the thread tools at the top of the page others with the same question will benefit :-)

Enjoy the buntu :-D

---

### Post by ivarn on 2010-11-26
Here's a tip since it sounds like you are a long time user of ubuntu. Go for the full installation, install your apps and before you delete ubuntu under wubi, backup your /home/username folder so you don't lose your configurations and stuff.

---


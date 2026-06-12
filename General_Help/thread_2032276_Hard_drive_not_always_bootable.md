---
title: "Hard drive not always bootable"
date: 2012-07-23
forum: General Help
---

### Post by emagar on 2012-07-23
I am relatively new to linux. I did something awfully wrong trying to install an on-line thesaurus for emacs. Now the machine will not boot all the times. Re-starting the machine will take me to BIOS boot sequence, as if the hard drive were not bootable. 

The really mysterious part is that the behavior is not systematic. The machine did in fact boot correctly after switching it off and on for two more times.  I've been hesitant to reboot again, but my wife inadvertently turned the machine off. The same pattern occurred: two failed boot attempts and a successful third. 

Two questions: 

(1) how can I figure out what is broken?

(2) what should I back up to retain my settings in case I can't fix this and need to re-install ubuntu?

Thanks in advance for your advice.

---

### Post by asmoore82 on 2012-07-23
I would check the hard drive for bad sectors.

But back up everything important somewhere else first, a hard drive in bad enough but half working condition can be pushed over the edge by a simple read-only test.

Boot a live cd and run ```
sudo badblocks -sv /dev/sda
```you may need to adjust sda for your device name.

---

### Post by emagar on 2012-07-23
> **asmoore82 said:**
> I would check the hard drive for bad sectors.

Thanks Asmoore. I should add that it is a solid state drive. Does the concept of a bad sector transfer to solid state technology?

---

### Post by emagar on 2012-07-23
> **asmoore82 said:**
> back up everything important somewhere else first

Other than my personal documents, what else constitutes important stuff to back up?

---

### Post by asmoore82 on 2012-07-23
@SSD: Yikes, I'm not sure. There's probably a quicker way to tell the SSD to self check and re-allocate if necessary. I would add SSD to the thread title to hopefully get someone with experience in that.

@Backup: Yes, personal stuff is all I was thinking about.

---

### Post by emagar on 2012-07-23
> **asmoore82 said:**
> @SSD: Yikes, I'm not sure. There's probably a quicker way to tell the SSD to self check and re-allocate if necessary. I would add SSD to the thread title to hopefully get someone with experience in that.

@Backup: Yes, personal stuff is all I was thinking about.

I've added SSD to the title, I hope someone offers advice. Thank you AsMoore82.

---


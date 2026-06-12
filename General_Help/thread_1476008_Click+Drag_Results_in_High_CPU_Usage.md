---
title: "Click+Drag Results in High CPU Usage"
date: 2010-05-07
forum: General Help
---

### Post by theSuperman on 2010-05-07
First thing I did when I installed 10.04 was to re-arrange my icons. I clicked on the first and started to drag. The icon did not move, and nautilus was using 94% of my cpu for a good 15-20 seconds before gtk-window-decorator was using 95-100% of my cpu for a few more seconds. Finally, after a few more unsuccessful tries with the same results, I was able to move the icons.

I assumed this was a bug in nautilus, however the same thing occurred in Chrome when I tried to re-arrange my bookmarks, and the same thing in gnome-panel. 

The only thing in common I see is gtk-window-decorator.

---

### Post by theSuperman on 2010-05-11
Why is it that every issue that I am seeing in Lucid has not been seen by anyone else?? This has by far been the most buggy version of Ubuntu released to date, yet nobody else has seen the issues I am running into.

---

### Post by mthome on 2010-05-11
My suspicion is that the task scheduler is broken on some machines, resulting in a bafflingly wide range of performance issues.  Adding to my suspicions, when I switched to the preempt kernel, things are rather better (though not up to 9.10 levels).

---

### Post by theSuperman on 2010-05-11
I have not heard of broken task scheduler in Lucid though.
Which kernel did you update to? I'm currently on 2.6.32-22-generic, which seems to be the latest one in the lucid-proposed repo.

---

### Post by mthome on 2010-05-11
I've been running on 2.6.32-22-preempt

---

### Post by theSuperman on 2010-05-11
I would think 2.6.32-22-generic is the later version of 2.6.32-22-preempt, correct?\


EDIT: I just remembered, I am using EXT4...maybe that is the cause for this click+drag issue?

---

### Post by theSuperman on 2010-05-11
I tried a little experiment..I changed fstab to mount root as ext3 instead of ext4, still had the performance issues.  I then remembered that I added "elevator=deadline" to my grub boot options, and after disabling that, performance increased a bit, however I still get the click+drag issue.   Ill probably switch back to mount my drive as ext4, since thats what the drive is partitioned and configured for.

---

### Post by mthome on 2010-05-12
No - generic, preempt, and server are three different feature sets of the same kernel version.  generic is, well, for general purpose use, preempt has a set of patches that implement kernel level preemptive multitasking that is crucial for rt and media workstations, and server is (IIRC) tuned for throughput over responsiveness.

---

### Post by theSuperman on 2010-05-12
> **mthome said:**
> No - generic, preempt, and server are three different feature sets of the same kernel version.  generic is, well, for general purpose use, preempt has a set of patches that implement kernel level preemptive multitasking that is crucial for rt and media workstations, and server is (IIRC) tuned for throughput over responsiveness.
Hm so how would I go about getting the preempt kernel? Is it somewhat easy?

---

### Post by mthome on 2010-05-12
The flip answer is that you can just install it from synaptic and select it at boot time to see if it helps.  The ugly secret though is that I had all sorts of problems getting my video driver working properly - if you use one of the standard ones, you'll probably be fine.  If not... well, your mileage may vary.

---

### Post by theSuperman on 2010-05-12
I dont see 2.6.32 preempt kernel in the repos. I do see a 2.6.32-22-generic-pae though..is that it? Luckily its easy to revert back to a prior kernel, so I really dont have anything to lose by trying it out.

---


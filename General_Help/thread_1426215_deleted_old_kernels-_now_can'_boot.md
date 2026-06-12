---
title: "deleted old kernels- now can' boot"
date: 2010-03-10
forum: General Help
---

### Post by crashus on 2010-03-10
Hey,

yesterday I removed old kernels via. the synaptic manager- I'm 100% certain I did not removed the latest stable kernel, and the version before- I did however removed the oldest two. Now after restart I'm dead in the water- i cant get past the initial boot- the screen goes black.
I i'm running ubuntu 9.10 double-booted with windows vista, and right now I cant even get into vista... 

Let's say that I messed up with removing old kernels, and removed sth, that shouldn't be removed- but how does this mess up vista? 

And ideas how to solve this?

---

### Post by pastalavista on 2010-03-10
I dout it messed up Vista, just Grub. You'll need to boot from a liveCD and re-install grub.

'' pasted from another post:
>    1. Boot to the desktop of your Ubuntu Live CD, and open a Terminal  window (Terminal is usually in Applications/Accessories).
   2. First get to a GRUB prompt. Type:
      sudo grub
   3. GRUB extends beyond the very small MBR and has different Stages.
      Find and note the location of GRUB's Stage 1. Type:
      find /boot/grub/stage1
      You will be shown the location of Stage1, like (hd0,4)
      (if more than one Stage1 is located, you must choose which one to use).
   4. Replace the following hd?,? with the location just found. Type:
      root (hd?,?)
   5. hd0 is the GRUB label for the first drive's MBR (that 0 is a zero). Type:
      setup (hd0)
   6. Type:
      quit
      exit
   7. Open Partition Editor and right-click the partition where GRUB is setup - usually (hd0).
      Select Manage Flags and make sure the Boot flag is ticked for this partition.
   8. Exit GParted, and Restart. Remove the CD when it pops out. 

---

### Post by bumanie on 2010-03-10
Those instructions won't work as you are using 9.10, you should have grub 2 installed - those instructions are for grub-legacy (9.04 and earlier).
Look [here]("http://ubuntuforums.org/showthread.php?t=1195275") for grub 2 reinstallation instructions off a live cd - go to point 13. Would be a good idea to read the entire guide to get to understand grub 2 - but point 13, should help with your present issue.

---

### Post by crashus on 2010-03-10
tried it with liveCD and via. usb- both of them could not boot. with usb it just says- Remove disks or other media(i have nothing else pluged in or in the cddrive), and with the live cd it just won't load, and I stll get the black screen... I have changed the boot priority in both cases, either to cddrive or to USB, and still no luck

Is there a way to boot into vista or any other way to fix this, because right now the loss of all my data seems a real possibility...?

---


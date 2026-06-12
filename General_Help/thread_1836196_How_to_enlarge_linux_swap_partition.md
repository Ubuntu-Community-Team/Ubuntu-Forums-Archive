---
title: "How to enlarge linux swap partition?"
date: 2011-08-30
forum: General Help
---

### Post by Shvesley on 2011-08-30
Gone Partition editor? I have 3 gigs of ram and my swap partition is only 2.99 gigs I want to make it 6.01 gigs.

---

### Post by Enigmapond on 2011-08-30
With 3GB of RAM you don't even need swap. I never use swap...don't even have it. Is there a specific reason why? However if you have your heart set...boot into a liveCD and use gparted to re-size. The partition needs to be un-mounted.

---

### Post by haqking on 2011-08-30
> **Enigmapond said:**
> With 3GB of RAM you don't even need swap. I never use swap...don't even have it. Is there a specific reason why? However if you have your heart set...boot into a liveCD and use gparted to re-size. The partition needs to be un-mounted.

+1

there is too much mind paid to swap.  Make it the size of ram if you use hibernation say on a laptop other than that no real issue.  The double the size thing is a bit excessive nowadays where alot of machines have a alot of ram

---

### Post by YesWeCan on 2011-08-30
To list your active swap partitions:

[COLOR=Navy]swapon -s[/COLOR]

To deactivate a swap partition (eg: before trying to resize it):

[COLOR=Navy]sudo swapoff /dev/sdxy[/COLOR]      (x=drive letter, y=partition number)


To activate a swap partition:

[COLOR=Navy]sudo swapon /dev/sdxy[/COLOR]

---

### Post by WyleECoyote on 2011-08-30
just creat a swapfile you can delete any time if you need it

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

@Enigmapond and haqking 

If you do a lot of graphic art like with blender you do from time to time use swap, I have 4G ram and 8G swap now because I am getting tired of losing work when blender crashes from lack of memory. The swap is extra space to throw it in and save my work, but I do agree ordinarily you really don't need much swap space if all you do is browse the net and do low memory operations that use less ram.

---

### Post by Shvesley on 2011-08-30
MY cd drive is not working right? How can I resize? USB? Thats it nvm

---


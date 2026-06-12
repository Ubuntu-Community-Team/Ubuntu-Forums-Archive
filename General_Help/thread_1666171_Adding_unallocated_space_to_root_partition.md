---
title: "Adding unallocated space to root partition"
date: 2011-01-13
forum: General Help
---

### Post by toi_c on 2011-01-13
Hello Ubuntu-gurus,

I am having an issue adding unallocated space to my root partition. Based on other threads I figured out that the unallocated space needs to be right next to the partition that one wants to extend. In my case, I would like to extend 'ext3' in attached screenshot of gparted. I carved out a 1002MB space and moved this unallocated space right under the ext3 partition (/dev/sda3). How do I add this unallocated space to /dev/sda3 please? When I run 'gparted' on bootup (using linux running on a usb stick), I don't get the option to increase the size of /dev/sda3. Basically the unallocated space is not being 'seen' when I try to resize /dev/sda3. Any ideas here please?

Regards
S.

$df -l

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3              3844152   2935868    713008  81% /
none                    502400       260    502140   1% /dev
none                    508008       248    507760   1% /dev/shm
none                    508008        88    507920   1% /var/run
none                    508008         0    508008   0% /var/lock
/dev/sda5             19462432    968924  17504896   6% /home
/dev/sda2            119140620  92518508  26622112  78% /media/windows-xp

---

### Post by Quackers on 2011-01-13
The unallocated space that you have created is within the extended partiton (sda4) so cannot be used to extend sda3.
What you could do is to shrink sda4 by 1000MB. Then that free space would be outside sda4 and usable by sda3. Please be careful, this can go wrong!. 
This should be done from the live cd desktop (not your real desktop), and swap partition should be turned off first (right-click - swapoff).
Please only do one thing at a time, then click the green tick, to apply the change. 
When all is finished, don't forget to turn swap back on!

---

### Post by toi_c on 2011-01-13
Thanks for the quick response. To start with, in order to get the 1002MB, I did a resize of /dev/sda4. Is 'shrink' a separate option in gparted? Sorry about the dumb questions.

---

### Post by Quackers on 2011-01-13
Resize is the correct terminology for gparted, I believe :-) Shrink is a Windows used term.
So you've resized sda4? Is the free space now shown before sda4 in the gparted screen?

---

### Post by toi_c on 2011-01-13
> **Quackers said:**
> Resize is the correct terminology for gparted, I believe :-) Shrink is a Windows used term.
So you've resized sda4? Is the free space now shown before sda4 in the gparted screen?

Correct. I have resized sda4 by 1002 MB. As a consequence, the unallocated space became available at the end, so I had to move the unallocated space right below /dev/sda3.

---

### Post by Quackers on 2011-01-13
Please post a screenshot of gparted as it is now, thanks. You shouldn't need to move the sapce.

---

### Post by toi_c on 2011-01-13
> **Quackers said:**
> Please post a screenshot of gparted as it is now, thanks. You shouldn't need to move the sapce.

Perhaps you misunderstood or maybe I am not being very clear. The screenshot attached in my first post has the details of gparted ==> I ended up with this screenshot after I resized /dev/sda4 and moved the unallocated space right below /dev/sda3.

---

### Post by Quackers on 2011-01-13
Hmm, I thought when you said
"Correct. I have resized sda4 by 1002 MB. As a consequence, the unallocated space became available at the end, so I had to move the unallocated space right below /dev/sda3."
You meant that you had done it. If you resize "from the left" you won't need to move the unallocated space later.

---

### Post by toi_c on 2011-01-13
Yes indeed. I didn't know there was an option to resize from the left. Now I do & thanks :-).

But my original problem remains. Any further ideas?

---

### Post by Quackers on 2011-01-13
What have you done so far please?

---

### Post by toi_c on 2011-01-13
Hi - I would like to extend 'ext3' in screenshot of gparted. This is my starting point. I have made no changes since I posted the screenshot and started this thread.

You had said
"Resize is the correct terminology for gparted, I believe :smile: Shrink is a Windows used term.
So you've resized sda4? Is the free space now shown before sda4 in the gparted screen?"

My response
"Yes, the screenshot in the first post is the outcome of this resizing + I had to move the unallocated chunk of 1002MB to the top of /dev/sda4 because I did not know that there was an option to resize from the left before I posted this thread".

---


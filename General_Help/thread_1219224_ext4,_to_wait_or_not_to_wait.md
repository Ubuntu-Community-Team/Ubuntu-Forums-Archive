---
title: "ext4, to wait or not to wait?"
date: 2009-07-21
forum: General Help
---

### Post by adempewolff on 2009-07-21
Hello I am upgrading my laptop's hdd in the near future and am considering use ext4 as the linux filesystem.  I've heard rumors that this will be the default filesystem for Karmic but am confused as to how I should go about switching over.

A small art of me feels I should wait until Karmic comes out to switch to ext4 because any remaining bugs will be worked out.  However I will almost certainly need a new hdd before then and am not sure if I should just start off with ext4, or start with ext3 and upgrade it later.

Anyone have any advice on advantages and disadvantages of either path (or a completely different way to go about this)?

Thanks!

---

### Post by elliotn on 2009-07-21
4 me ext4 works gr8 4 me

---

### Post by grayn0de on 2009-07-21
Works great for me in 9.04. I am using it with noatime set. I haven't benchmarked it to see the performance, but you can find that online.

---

### Post by Kimm on 2009-07-21
As far as I know ext4 is pretty much bug free at the moment, Linux < 2.6.30 has some issues with it though (Jaunty uses 2.6.26), so its not risk free.

I used ext4 for a couple of months without issues though, so I think its pretty safe, and you can always upgrade the kernel manually to 2.6.30 (I did that on my neetbook using [this guide](http://www.ramoonus.nl/2009/06/10/linux-kernel-2-6-30-installation-guide-for-ubuntu-and-debian-linux/) which also gave me much better wireless support :) )

I recently helped a friend of mine install Ubuntu on his new laptop and then opted for ext4, mainly because of the much faster filesystem check, we also upgraded the kernel to make sure it would be safe :)

---

### Post by philinux on 2009-07-21
I'm running Karmic on my second HD. Testing and reporting bugs etc. I recently re-installed the alpha2. Used ext4 and grub2. Seems to be working fine. But If i were you I'd wait for the testing cycle to finish. October not far off really.
Follow the testing. 
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

Only diff at moment is slightly quicker boot times.

---

### Post by sefs on 2009-07-21
I'm not risking it with critical data, but I do have it running on a secondary drive where non-critical data is stored, and so far so good.

---

### Post by Arup on 2009-07-21
ext4 since day one on Jaunty and not a single issue faced on either of my Samsung 1TB Spinpoints.

---

### Post by adempewolff on 2009-07-21
Thanks for all the replies.

I guess my question is: if I plan on upgrading to Karmic in october but will be getting a new hard drive before then should I format the new one (which will run juanty till oct) with ext3 then upgrade later, or start off with ext4 and manually upgrade the Kernel?

---


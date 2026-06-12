---
title: "Crash after sleep, no init on next boot"
date: 2010-11-29
forum: General Help
---

### Post by Ollytheninja on 2010-11-29
After I wake my computer from suspension it will work for 30s to a minute then it will freeze (the cursor still moves but nothing I click on responds).

I have to "pull the plug" to make anything happen again.

When I then turn it on again it stops part way through and drops to busy box shell say that there is no init (try init= bootarg)

I found a solution on the net which was to boot into my other linux distro (backtrack) and run fsck -y /dev/sda8 (sda8 is my ubuntu partition)

Then ubuntu will boot up again. until the next time it crashes and I have to go through the whole thing again.

It may be related that since last weeks kernel update I haven't been able to wake up from suspension, and so have had to go back to using the old kernel.
To get the old kernel to sleep properly I had to add nohz=off and highres=off to the grub menu.

---


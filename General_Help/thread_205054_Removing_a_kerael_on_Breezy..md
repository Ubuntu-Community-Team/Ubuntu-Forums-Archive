---
title: "Removing a kerael on Breezy."
date: 2006-06-27
forum: General Help
---

### Post by Compucore on 2006-06-27
I was just wondering about something here. I had done a installation on my Aptiva 2185-281 which is a AMD K6-2 400 with 192 megs of ram and a 20 gig fujitsu hard drive. When I updated from Hoary Hedgehog to Breezy Badger. I know with the update manager. Sometimes they suggest to install a better Kernel from time to time. Well when I was updated from Hoary to Breezy. I went from Kernel 2.6.10-6-386 to Kernel 2.6.12-1.386. Now when I went to the updated kernel The kernel kepted timing out on IRQ14. I don't remember the exact error. I can reboot the machine again to check it out to give you the full details. But what I wanted to know is if I did a rollback on just the kernel with Synaptic package manager to remove the 2.6.12-10-386. Will it make the changes in Grub so that it doesn't try and use the lastest one and fall back to my earlier kernel which works very well Which is Kernel 2.6.10-6-386. I know it sounds confusing here. But I just wanted to find out in advance before making any drastic changes. I did a manual change within grub to the earlier version in grub by hitting the escape key and told it to use the other kernel instead.

\Compucore

---

### Post by woedend on 2006-06-28
as long as its still there, yes it will be rather automated.  before you do this, use escape key when you boot to make sure
a) your old kernel appears on the list
b)your old kernel still works.

---

### Post by Compucore on 2006-06-28
Yes I still have two other kernels in the list. All I really needed to do is to get rid of the most recent one. Since it's basically choking on the AMD k62-400 CPU and searching for a IRQ14 for something. The one later than this is working fine as the first install from Hoary is working well too. Its just to take out the most recent kernel.and let it use the last one that works well. Its weird sometimes when your using kernels. Some kernels well well on some processors. And then sometimes they won't due to what ever else you know. 

Compucore

---

### Post by Compucore on 2006-06-29
I've fuinally fixed it. Since the newer kernels could not be removed for some reasion. What I did do was to edit the grub menu that was on my Aptiva computer and just remarked off the latest version of the kernel. And left the other two on there for booting into. And it is wrking fine now. And more satisfactory for me. Thankes for the help anyways Woend. 

Compucore

---

### Post by woedend on 2006-06-29
the newer kernel probably wasnt removed because of the meta packages installed(such as linux-386, linux-image-386, linux-restricted-modules-386).  If you remove those first it should let you remove the kernel.  Just be careful it doesnt remove the one you want to keep

---


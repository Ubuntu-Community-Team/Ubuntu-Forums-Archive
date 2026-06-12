---
title: "Should i remove old kernels ?"
date: 2011-07-22
forum: General Help
---

### Post by papaapa on 2011-07-22
Hello!

I use Ubuntu 11.04. I update my system and now I have two kernels. I restart the system and I open Ubuntu-tweak-->Package Cleaner-->Old kernels but i could not see the old kernels. I also open Computer Janitor but i could not see even here the old kernels. I open the synaptic and i see that the old kernels are installed also on grub-menu i can see the old kernels. I will backup my system as soon as possible. I'm worried to remove old kernels now because i will backup the system. Should i remove them from synaptic ? And why i can not see them from other softwares(ubuntu-tweak, Computer Janitor) ?

Thank you!

---

### Post by nothingspecial on 2011-07-22
I always keep atleast one old kernel around. Sometimes new kernels break stuff and booting the old one is the easiest way to get around it.

---

### Post by malspa on 2011-07-22
What I do is go to Synaptic and search for **linux-image**. For example, in Ubuntu Lucid I currently find linux-image-2.6.32-32-generic and linux-image-2.6.32-33-generic. I keep the current one and the most recent one. Anything older, I remove with the "Mark for Complete Removal" option.

---

### Post by dasan on 2011-07-22
It is always recommended to keep one old kernel until you are pretty sure that new one is not breaking and has nothing missing

---

### Post by Quackers on 2011-07-22
There are 3 entries for each kernel in synaptic. If you use the "mark for complete removal" option you will only have to remove 2 entries manually (the third is done automatically).
Once previous kernels are removed open up a terminal and run ```
sudo update-grub
``` to clean the grub menu up.

---

### Post by malspa on 2011-07-22
> **Quackers said:**
> There are 3 entries for each kernel in synaptic. If you use the "mark for complete removal" option you will only have to remove 2 entries manually (the third is done automatically).

When you speak of the other 2 entries here, do you mean the two linux-headers packages? For example, I removed linux-image-2.6.32-31-generic but I still have linux-headers-2.6.32-31 and linux-headers-2.6.32-31-generic showing up in Synaptic.

> **Quackers said:**
> Once previous kernels are removed open up a terminal and run ```
sudo update-grub
``` to clean the grub menu up.

Looks like this might not be necessary. Synaptic seems to be running it; I haven't needed to run sudo update-grub.

---

### Post by Quackers on 2011-07-22
Question 1, yes.
Question 2, Is your grub menu reduced in terms of number of kernel entries?

---

### Post by malspa on 2011-07-22
> **Quackers said:**
> Is your grub menu reduced in terms of number of kernel entries?

Yes.

(This is in Lucid.)

---

### Post by Quackers on 2011-07-22
That's good then :-)
If you mark everything for "complete removal" you may free up some more space too. From memory I think it's about 250MB per kernel in total.

---

### Post by malspa on 2011-07-22
Thanks, Quackers, I never thought about getting rid of the old linux-headers. I had a bunch of 'em accumulated; gone now.

But, yeah, next time you remove an old linux-image, watch the terminal output after you apply the changes, you should see that update-grub is being run (at least, I see that here), so you don't have to run sudo update-grub later.

---

### Post by Quackers on 2011-07-22
Are you using synaptic to remove them? I've never had the terminal open when using synaptic - and certainly never checked it :-)

---

### Post by sisco311 on 2011-07-22
> **Quackers said:**
> Are you using synaptic to remove them? I've never had the terminal open when using synaptic - and certainly never checked it :-)

You have to click on *Details*.

[[img]http://ompldr.org/tOWwxMQ[/img]](http://ompldr.org/vOWwxMQ)

---

### Post by Quackers on 2011-07-22
Ah, not the terminal as such then :-) I see.
Thanks

---

### Post by malspa on 2011-07-22
In Synaptic: Settings > Preference > General tab > Applying Changes section > put a check mark next to "Apply changes in a terminal window."

---

### Post by Dave_L on 2011-07-22
> **Quackers said:**
> There are 3 entries for each kernel in synaptic.

There are four entries, at least in my case.

Here's how I remove an old kernel, in this case 2.6.32-30, using synaptic:

Select Status "Installed" in the left pane, search for "2.6.32-30", select the four packages found, and remove completely:

```
linux-backports-modules-alsa-2.6.32-30-generic will be removed with configuration
linux-headers-2.6.32-30 will be removed with configuration
linux-headers-2.6.32-30-generic will be removed with configuration
linux-image-2.6.32-30-generic will be removed with configuration
```

---

### Post by Quackers on 2011-07-22
Ok thanks.
Only 3 here
Linux Headers
Linux Headers generic
Linux image generic
Backports seems to be the difference.

---


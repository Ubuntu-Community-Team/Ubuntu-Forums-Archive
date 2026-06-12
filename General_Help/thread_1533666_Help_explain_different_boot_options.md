---
title: "Help explain different boot options"
date: 2010-07-18
forum: General Help
---

### Post by LargeAl on 2010-07-18
I have Windows Vista and Ubuntu on my computer and when I first turn it on I am giving more options than I really know what to do with. It looks something like this:
Ubuntu, with Linux 2.6.32-23-Generic
Ubuntu, with Linux 2.6.32-23-Generic (Recovery Mode)
Ubuntu, with Linux 2.6.32-22-Generic
Ubuntu, with Linux 2.6.32-22-Generic (Recovery Mode)
Ubuntu, with Linux 2.6.32-21-Generic
Ubuntu, with Linux 2.6.32-21-Generic (Recovery Mode)
Memory test (memtest 86+)
Memory test (memtest 86+, serial consol 115200)
Windows Vista (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)

I select the first option to use Linux and I select the second to last option to use Windows. But what are all the other options for? 

Thank-you, Al

---

### Post by 23dornot23d on 2010-07-18
The other options are older kernels .... and are not needed as long as the first one boots ok

there is a link on this ..... 

I have just been looking at ..... [link here]("http://www.ubunturoot.com/2010/03/how-to-remove-old-kernel-images-in-grub.html")

You can install Ubuntu Tweak from synaptic.

( I think there are plans to show only the main ones too in the future )

The others are left as a safeguard - ensures that if a upgrade fails that you can get back and boot an older one.

Some more information ....[more in depth]("http://ubuntuforums.org/showthread.php?p=9603253#post9603253") as I too have been trying to alter this and set it up as I want it to display the entries

The Custom Menu for Grub2 is probably the best thing - but it still takes a bit of setting up at the moment.

You could then possibly remove all of these ( Memtest is upto you - I rarely have ever used this )

> 
Ubuntu, with Linux 2.6.32-22-Generic
Ubuntu, with Linux 2.6.32-22-Generic (Recovery Mode)
Ubuntu, with Linux 2.6.32-21-Generic
Ubuntu, with Linux 2.6.32-21-Generic (Recovery Mode)
Memory test (memtest 86+)
Memory test (memtest 86+, serial consol 115200)


---

### Post by Megaptera on 2010-07-18
Another vote for Ubuntu Tweak unless you're OK using synaptic.

---

### Post by dino99 on 2010-07-18
be carefull using tweak, it often have issue, better to only use synaptic for all install/uninstall packages

---

### Post by Megaptera on 2010-07-18
Hi,
What issues please? Just so I don't run in to problems.

Thanks.

---


---
title: "Dual boot from second disc -won't boot"
date: 2009-12-29
forum: General Help
---

### Post by SallyK on 2009-12-29
I've previously installed Ubuntu to a couple of Windows computers without any problems, using the installation program to partition the one hard disc. 

This time though, I was trying to install NBR on a second hard disc - the first contains Windows XP. The installation seemed to work flawlessly, but when I came to boot the computer, it stuck just after the point when it could boot from a CD and before any Grub boot menu came up.

I got into the Grub CLI and used this page ([http://members.iinet.net/~herman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html")) to boot into NBR and check the grub.cfg file. It seemed to be fine, but still the same problem.

So, at the moment I can get into NBR by a long-winded CLI process and not into Windows at all. Can anybody help? Is the problem anything to do with the fact that the drive NBR is installed to is sdb, rather than sda, and is set up as the slave rather than the master?

---

### Post by b0b138 on 2009-12-29
Get into NBR and run "sudo update-grub" and see if that will make it work.

---

### Post by SallyK on 2009-12-29
Thank you very much for the reply - I've just tried that, and also I tried the new [B]grub-mkconfig command as well.

Now, the system sits on Loading Grub for about 7 mins, and then it goes to the Grub menu screen. So, progress, I can now get into Windows, but still - 7 mins? 

Any bright ideas as to what is taking the time?

In any case, thank you for trying to help.
[/B]

---

### Post by b0b138 on 2009-12-29
Maybe try reinstalling grub?  [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)  has a lot of info but basically after "sudo update-grub" you can "sudo grub-install /dev/sda"  and if there are any errors "grub-install --recheck /dev/sda"

---

### Post by SallyK on 2010-01-02
Thank you very much for the suggestion - today's the first chance I've had to try it.

I've been working with the information on the page you linked to, and also on here - [http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html) but unfortunately it hasn't helped. Still the long delay before the Grub menu comes up.

I don't suppose anyone else has any ideas?

At the moment, I'm wondering whether to either physically swap round the drives, so that NBR is on dev/sda, or to make a Linux boot partition on the existing master drive, I'd rather avoid having the installation split like that, if I can help it - but maybe it would fix the problem.

---

### Post by oldfred on 2010-01-02
Part of the problem may be this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

But I have seen users who could not even get slave drives to boot at all. I would try setting it to master. 

I like to have each operating system on each drive with its own boot loader in the MBR. Then if there is an issue I can switch drives and still boot something.

---

### Post by SallyK on 2010-01-02
Thank you very much - that does read very much like the problems I'm having.

I'll try swapping the drives, and hopefully that might help.

---

### Post by SallyK on 2010-01-24
It's been a couple of weeks since I've had a chance to work on this, but today I tried the experimental version of Grub 2 from the PPA listed in the bug discussion linked to earlier in this thread - [https://launchpad.net/~fzielcke/+archive/grub-ppa](https://launchpad.net/~fzielcke/+archive/grub-ppa)

It worked like a dream, no more 7 minute wait. I didn't have to swap the drives, or anything.

So if anyone is having the same problem, it's probably worth trying.

---


---
title: "GRUB - Master of difficulties"
date: 2010-09-26
forum: General Help
---

### Post by user:hackIt on 2010-09-26
Hey all,

I have had it with the frustration of trying to figure out how to successfully install grub on my own, so I am hitting the forums. What can you tell me about installing grub/grub2 (whichever is best -- I want something that works) to my single hard drive computer.

Operating systems: Windows XP, xUbuntu 9.10
Hard drive: Samsung SATA 2, 1 TB

Desired result: Menu that loads upon boot so that I can select which OS I would like to load without inserting media device or disk.

I thought [this individual]("http://ubuntuforums.org/showthread.php?t=224351") had the most straight forward and thorough tutorial (of any I have seen) on the subject but precluded at least one thing for me that I cannot afford to ignore: I don't seem to have a "stage1" that can be loaded by the grub shell. 

Trying to find it in /boot/grub/stage1 in the grub shell, I get...

"Error 15: File not found"

What I do have in that directory is 'grubenv'.

When I boot up, it loads grub, but it comes up with an error message saying, "File not found". Then, all I get is the 'grub rescue' prompt: "grub rescue>".

Obviously, after spending hours on this thing, this is not the whole story. But there have been so many attempts to try fix it with one thing or another, that I cannot easily relate them all, if I could even remember each one.

I would really (*really*) appreciate some help leading to a solution here. Thanks.

---

### Post by harrismh777 on 2010-09-26
What are you using now?  lilo?  other?   just curious.

The easiest way to get this accomplished is to backup your user data from /home at a minimum, and then reload ubuntu 10.x and have the best ubuntu version as well the default grub2.

Grub2 is the default boot loader on the later distros (above 9.04 I think). You probably don't want to try to load and configure grub manually. Just load ubuntu 10.x and enjoy.

:rolleyes:

---

### Post by drs305 on 2010-09-26
If you are getting a grub rescue prompt you have Grub2. Rather than try to fix whatever you have, I'd recommend just purging all your Grub configurations and reinstall Grub2. It takes a couple of minutes and is safe as long as you have a steady power supply and internet connection.

Here is a guide on how to accomplish it. 

If you boot normally to your Xubuntu installation without a LiveCD, you don't have to chroot and you can just accomplish steps 2-5 and include "sudo" in the commands.

If you can't boot normally, boot the LiveCD and accomplish all the steps.

[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

After the last step, run "sudo update-grub" to ensure Grub2 finds your Windows install and puts it into the Grub menu.

Ask here if you have questions.

---

### Post by user:hackIt on 2010-09-26
Not Lilo. Super Grub 2 CD--very cumbersome and rather annoying, but better than nothing.

---

### Post by Quackers on 2010-09-26
I can vouch for drs305's advice. I have used it..........once or twice, or three or four times.......this week! What can I say, I'm reckless! :-)

---

### Post by user:hackIt on 2010-09-26
Ok, I tried harrismh777's advice. That is, I upgraded to 10.04 (without Live CD) and during the installation process it asked me if I wanted to overwrite 'grub.d'. I was only too happy to assent. Not long after, it asked me where I wanted grub to be installed. I had three options:

- Something roughly 1 TB in size. I suspect this would be referring to the drive as a whole, and so I thought it might refer to the MBR.
- A partition of 100 Gbs. That would be my Linux partition.
- And a 2 Gb Flash drive. Oh hey, I have had that plugged in for a while.

Anyways, when prompted for help, it said that if I did not know where it was supposed to install, I should install it to all partitions/drives that I wanted to boot (or something like that, I don't remember exactly). So, I selected both the whole hard drive and my Linux partition. Installation finished, and I rebooted the system. This time I did not try and load my CD drive to boot with Super Grub. 

But, presto! The grub menu (which I have been so earnestly seeking--give me a break, I grew up on this thing) popped up, with both Linux and Windows boot options. I was thrilled. After more testing to confirm, I was even more thrilled. Thanks for the upgrade suggestion, Harris.

I guess it is needless to say that I did not try drs305's advice. I expect, now, that it would also work, Quackers, but I must say that if I have learned anything over my troubles with grub, it is that there are a whole lot of unique situations out there that don't all seem to fit the mold of even a thorough tutorial.

Kind of embarrassing that this proved so easy to fix. Hopefully, though, this thread will be useful for others out there looking for the answer to a grub install.

---

### Post by drs305 on 2010-09-26
Glad you got everything working.

Just a note: Even though the Grub installer said to install on all partitions, the Grub developers have decided that doing so is generally not recommended and the instructions have changed in later releases of the Ubuntu family. This would also apply to 9.10.

The current recommendation is *not* to install it on partitions, since if the location of the files change it can break Grub. You didn't do anything wrong - you followed the instructions. Just make a mental note that if you ever have to reinstall Grub2 to select the drive but not the partition.

You can help others seeking assistance as well as the 'helpers' by marking the thread SOLVED via the Thread Tools link near the top right of the first post. (It's also reversible.) Thanks.

And by the way, welcome to the Ubuntu forums!   :P

---


---
title: "HD formatted &#8210; help &#8210; two questions."
date: 2010-08-13
forum: General Help
---

### Post by sarabiasaurus on 2010-08-13
Hi. This is my first time on the forums, so if I make some mistake or anything, please point it out and excuse me. Also, I'm not a native english speaker, so also forgive any errors I may have when writing.

As the post title says, I want to make two questions. One is very technical (I supose), and the other one is more like a need for an explanation. But let's get to the point.

My main and only Ubuntu partition got automatically formatted and replaced by an Ubuntu Studio one, dragging all my data in the process. The technical question is, can I rescue something? I know if a partition gets erased there is the possibility of recover some information, but I'm not sure that's the case when another OS comes on top of it. If something can be rescued, then, what tool would you recomend? I've heard PhotoRec is simple and effective, but don't know if it's the best one in my case. Of course I haven't been using the partition, in the case that some info is still there, only that time I turned my computer on and found out everything was gone.

The second question is: what the hell happened?
So the story goes: I ran Ubuntu, as I said, and decided to install Ubuntu Studio ('ubuntustudio-desktop' in Synaptic). After I installed it, I rebooted not in my HD immediatly, but in a live USB (with puredyne, a Debian-based media distro). There I mounted my HD to get some files, dabbled a bit, and rebooted again, now into my HD. As the system was running, something loaded (a big white UBUNTU with blue letters on the foreground) and then I came out in this pretty new Studio desktop with all my data gone. Again, what the hell happened? Was it the installing of the Studio, the external mounting, or what?
That's just to know and don't do it again.
And here's hoping I haven't been too boring or complicated to read. Thank you.

---

### Post by sarabiasaurus on 2010-08-14
bumpy
please, guys, this is important to me :(

---

### Post by ranch hand on 2010-08-14
It is hard to tell what happened.  I would say that you probably hit the wrong option on the first partitioner page of the installer.

When you want to dual boot it really is safer to choose the "manual" install option and create the partitions you want to install on your self.

I say partitions because a separate / (root) partition is a very nice thing to have if  you ever have real problems with an install.  It helps protect your data if it is all on a /home partition.

I always use gparted from the Live Session to resize and create partitions, write down the partition numbers, and then install.  Choose the manual option on the partitioner page, select the / partition and then the /home partition and then let it install.

I would really like to say you could recover your data but I have my doubts.  I hope that some one will come on and say I am wrong and that you can.

You have formatted and over written the data.  There is probably some way to get to that data but it would be hard and probably require removing the drive and letting some one else work on it that is in the business of data recovery.

---

### Post by sarabiasaurus on 2010-08-18
But it wasn't an installer! I just got the thing from synaptic - it's just a collection of programs, not another operating system. That's why I don't get the new system install.

Anyway, I think there's no salvation for my data.
A / partition separate from /home. Got it. But what if I want to install two systems and do a double boot? Could I use the same /home for both of them?

---

### Post by ranch hand on 2010-08-18
So, I misunderstood your post.

Do I have it straight now.  You have ubuntu install and then added, through synaptic, Ubuntu Studio.

If this is the case the thing to do is reboot and at the login page there is a bottom panel.  On that panel there is an option to select the "session". It should have;
xterm
failsafe-gnome
Ubuntu
Ubuntu Studio

The one you are going to go into should be visible in the little box.  See  if that helps.

Unless you somehow changed users all the files should be available in both the Ubuntu and Ubuntu Studio.  I am not sure why they wouldn't be.

If you can login to the other session and the files are there we will worry about getting them to be available correctly then.

If you use auto login you will have to go to System>Administration>Login Screen and change that to not be automatic.

---


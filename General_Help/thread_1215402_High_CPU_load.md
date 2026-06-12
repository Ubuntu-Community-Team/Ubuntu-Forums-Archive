---
title: "High CPU load"
date: 2009-07-17
forum: General Help
---

### Post by Niksko on 2009-07-17
Ever since installing Jaunty I have been experiencing very high CPU load. This means 95-97% CPU usage at all times. Any idea on how to fix this?

What information do you need?
Kernel: 2.6.28-13 generic on i686
Processor: Pentium 4 2.8Ghz

---

### Post by akshay.sulakhe on 2009-07-17
Firstly..i really wonder abt ur pc specs...why a 750gb hd and 40gb hd on P4...k...anywayz...u areusing 13series kernel..try upgrading it or downgrading it...u can do that from Synaptic...if problem persists..manually check which process is taking that much..ince i had anacron taking 95% of CPU..on a AMD Phenom 9950 which is  a quad core..

---

### Post by Niksko on 2009-07-17
Um, because I like to have a lot of space and since processor performance has nothing to do with disk space...

I've tried looking at individual processes, both through the system monitor and top, and both report nothing out of the ordinary, that is, X will use about 10% cpu and everything else 0 or 1%.

I'll try booting into 2.6.28-11 kernel and see if that fixes it.

---

### Post by Niksko on 2009-07-17
...and booting into 2.6.28-11 has done nothing.

---

### Post by lovinglinux on 2009-07-17
> **Niksko said:**
> Um, because I like to have a lot of space and since processor performance has nothing to do with disk space...

I've tried looking at individual processes, both through the system monitor and top, and both report nothing out of the ordinary, that is, X will use about 10% cpu and everything else 0 or 1%.

I'll try booting into 2.6.28-11 kernel and see if that fixes it.

I bet all my chips on Remote Desktop. It usually goes crazy, using a lot of CPU and does not show in top.

Go to "System >> Preferences >> Startup Applications", then disable Remote Desktop there and reboot.

---

### Post by egalvan on 2009-07-17
> **Niksko said:**
> Um, because **I like to have a lot of space and since processor performance has nothing to do with disk space.**..


+1

Amen, tell it like it is, brother!

I've set up systems with 10G for the OS, and 1TB for storage...

Or a super-fast Raptor (60GB) for the OS and a pair of 1TB for storage...

(Or a 6GB boot, and the rest on the internal network...
Or no drives, and verything over the internal network...)

About the only drawback that "smaller" (10G,20G,etc) drives might have is that they tend to be older, and thus may only be 4200 or 5400 RPM...
which CAN impact overall system performance (I/O times).
Otherwise, they work well.

---

### Post by Niksko on 2009-07-17
Oh, heh, I guess I should explain. My PC was basically obtained for free from my Dad's work, and I added the 750GB hard drive. The 40GB drive has a single NTFS partition that I almost never use since I'm now almost always running Linux. The 750GB HD is where the Jaunty install is along with a dedicated /home partition, and a large NTFS formatted partition for data. The 40GB hard drive is only there because I figure it's not doing any harm.

Back to my problem. Nice suggestion lovinglinux, but I read that somewhere else and tried it to no avail. Any other suggestions?

Not sure if this has too much relevance, but when I installed Jaunty, I actually installed from a Kubuntu Live CD and then removed KDE and installed GNOME (don't ask why). The instructions I followed are [here]("http://www.psychocats.net/ubuntu/puregnome").

One other thing I should mention. I'm pretty sure that back on Intrepid (ie. before I had this problem) I was running an i386 kernel build (as opposed to my current i686 build). I've been doing some reading and concluded that ideally I should be running an i786 build. I was thinking of compiling a kernel from scratch tonight. Would this help at all? If so, could someone point me to a good guide on optimizing a kernel?

-Nik

---

### Post by 3rdalbum on 2009-07-17
> **akshay.sulakhe said:**
> u areusing 13series kernel..try upgrading it or downgrading it...u can do that from Synaptic...

Disregard this suggestion; the kernel is the absolute last thing to be fiddling with in this situation.

A runaway program is what's going to be using your CPU power. If you go into the terminal and type the word "top" and press Enter, you will see a list that is updated every 5 seconds, with the programs that are using the most amount of CPU time. If one of those constantly stays near the top of the list showing a large amount in the "%CPU" column, then that's the culprit. You can usually kill that program or possibly change its settings to fix the problem.

---

### Post by lovinglinux on 2009-07-17
> **Niksko said:**
> Back to my problem. Nice suggestion lovinglinux, but I read that somewhere else and tried it to no avail. Any other suggestions?

I guess I have lost all my chips then :)

Do you have the proper driver for your graphics card installed?

If you have Intel graphics card, visit [Jaunty Intel Graphics Performance Guide](http://ubuntuforums.org/showthread.php?t=1130582).

> **3rdalbum said:**
> A runaway program is what's going to be using your CPU power. If you go into the terminal and type the word "top" and press Enter, you will see a list that is updated every 5 seconds, with the programs that are using the most amount of CPU time. If one of those constantly stays near the top of the list showing a large amount in the "%CPU" column, then that's the culprit. You can usually kill that program or possibly change its settings to fix the problem.

See quote below 

> **Niksko said:**
> I've tried looking at individual processes, both through the system monitor and top, and both report nothing out of the ordinary, that is, X will use about 10% cpu and everything else 0 or 1%.

---

### Post by Niksko on 2009-07-17
Ha. I'm rather silly. Solved it.

You were right lovinglinux. I guess I'd best give you your chips back :D

You were right about it being a runaway process. I just didn't think it would be a process that I had written. It's a simple script that checks to see whether the mouse is in the visible part of the desktop and adjusts if it isn't (I have a strange arrangement of screens).

First off, I had two of these scripts running (I'd somehow entered it twice in my startup applications). Cutting it down to only one instance managed to drop cpu usage to 70%. Then, I went back into the script and looked at it. I had put in a while loop to check and adjust mouse position, but hadn't included a wait between checks. It was just checking as often as it could (and evidently using up all the spare cpu cycles). All it needed was a 'sleep 0.25' before the end of the loop and cpu usage is down to 6%.

It's strange, because I had exactly the same script back on Intrepid and nothing bad ever came of it.

Thanks for your help anyway.

-Nik

---

### Post by LightningCrash on 2009-07-17
In my office we call this kind of gotcha "outsmarting yourself." :D

---


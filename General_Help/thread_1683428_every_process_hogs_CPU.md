---
title: "every process hogs CPU"
date: 2011-02-07
forum: General Help
---

### Post by adempewolff on 2011-02-07
Sometime in the last week I noticed that Firefox was running really slow and slowing down the entire system as well.  I suspected that the problem might only occur after resuming from RAM and might have something to do with a plugin.  The computer has also (as a result) been running extremely hot to the touch during this same period.

Long story short, I finally had time to do some troubleshooting and discovered that not only does it have nothing to do with suspending/resuming but it also is not just Firefox.

Every single program and process, when actively doing something, uses up about 6x as much of the CPU resources as I would expect it to.  From gnome-panel to firefox-bin to compiz to xorg, even htop all are hogging CPU like it is their business.

I've restarted multiple times to no avail, and scoured the log files to look for error messages.  Anyone have any idea what this could be?  Or even just suggestions for where else to look. It literally started out of nowhere in the last half-week so I feel like it must either be a regression from an update or something I installed.

I'm running Lucid Lynx, kernel: 2.6.32-28-generic 64 bit on a Dell Latitude 630

CPU: Core 2 Duo T7100 1.8ghz
Mobo: Latitude 630 one with the Nvidia chip (NVS 135M)
Memory: 4 GB

I can supply more info if people have ideas what would be useful.

Thanks!
Austin

---

### Post by mikewhatever on 2011-02-07
Can you post a screenshot of htop running. That would, hopefully, make your story a little less vague.

---

### Post by adempewolff on 2011-02-07
Sure, although I really wasn't kidding when I said *every* process has ridiculous CPU usage when doing any task: in every sceenshot you can see the processes associated with taking the screenshot going wild.  While I hope this proves my point by showing that literally every process is having abnormal CPU usage, it is annoying because I can't take a screenshot of the other processes that are the biggest perpetrators (ie. firefox).

I'm beginning to think that it might be a hardware problem.  I booted of an old copy of fedora on another partition and it had the same problem.

Then I ran Dell diagnostics twice, having the computer spontaneously shut down during a memory test (at different places though) each time.  So I ran memtest86+ and the computer also shut down suddenly in under two minutes.

So now I am trying to figure out whether it is my memory, cpu or motherboard.  I feel like if it were the memory, the computer wouldn't power off, and it is the stress the memory tests are putting on some other component that is making the memory tests crash.  I really have no idea though, and would appreciate any suggestions for further diagnostics.

---

### Post by mikewhatever on 2011-02-07
I'd say, the cpu usage of processes that top the htop list is a bit high, but those down below are mostly at 0.0. The output of uptime (top rightmost) is also curious, as it shows the average load as very low.

---

### Post by quadproc on 2011-02-07
> **adempewolff said:**
> 
Then I ran Dell diagnostics twice, having the computer spontaneously shut down during a memory test (at different places though) each time.  So I ran memtest86+ and the computer also shut down suddenly in under two minutes.

The unexpected shutdown is almost certainly a result of overheating; most systems will monitor at least the CPU temperature and, if it gets too high, will shut off in order to protect the hardware.  Of course, this observation does not contribute enlightenment regarding the excessive CPU usage.

Are you overclocking?  If so, then I would suggest reducing the clock rate.  Otherwise, I suspect some kind of a hardware problem but I have no clue where to look.  The only guess that I have is that possibly something is creating a lot of interrupts at a high rate and the CPU and OS are dispatching those by sending them to the bit bucket.

quadproc

---


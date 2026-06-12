---
title: "UNR slows computer down"
date: 2009-07-15
forum: General Help
---

### Post by killerabbit on 2009-07-15
I'm using Ubuntu Netbook Remix on my Acer Aspire One. When I first got it it worked great, everything ran smoothly. Now, about a month later, it takes forever (~1 minute) to simply change menus, and even longer for more advanced tasks. I got it for normal, cpu light work, but its going so slow that its becoming unusable. Any ideas to speed it up again?

---

### Post by TeamJ on 2009-07-15
1. perhaps one prcess is slowing it down. check the process list to see if there are any ountanding ones
2. the disk may be full or fragmented. if iles are fragmented it is hard for the system to navigate between them. the computer needs some HDD space for temporary storage, etc. so make sure there is at least 8% left.

---

### Post by killerabbit on 2009-07-15
nope, process list is showing nothing, but the cpu is idling at around 80 percent while no active processes. Disk is has loads of space, that is definitely not the issue.

---

### Post by TeamJ on 2009-07-15
hmm. I guess I can't help you then. I sometimes get that with all operating systems, the processes don't add up to the CPU and something mysterious is eating away at it. but that is usually either solved by restarting, or because the os is junky, exausted, etc. after 3 years of use. so no, I don't know

---

### Post by t4thfavor on 2009-07-15
Use regular jaunty, I have no issues on my eeepc 900a.

Perhaps its a sign that your SSD is getting old, and has alot of remapping of worn out blocks to process. The ssd that comes on most netbooks is not the greatest quality.

---

### Post by killerabbit on 2009-07-15
Its a month old, and it has a hdd. I'll try swapping it to normal Jaunty, have been thinking about doing that.

---

### Post by TeamJ on 2009-07-15
> **t4thfavor said:**
> has alot of remapping of worn out blocks to process

that's what I meant by fragmented. on ssds and hdds this can happen.try defragmenting it

---

### Post by digitalsp on 2009-07-15
I have UNR on two netbooks, a Acer One and Asus Eeepc. Both still running fine. 

Have you tried running UNR from a USB stick ? If you still have performance issues running via USB I would suggest maybe running memtest to see if there is something wrong with your memory. If the performance comes back when running via USB I would maybe suggest reinstalling UNR. After reinstalling UNR and you still have performance issues, I would suspect your harddisk might be faulty.I had performance issues with a desktop drive (1TB hitachi) on a Synology Nas that drove me nuts. Luckily the drive died eventually and the performance on NAS returned once I removed the faulty drive.

---

### Post by killerabbit on 2009-07-15
Tried defrag (have done some torrenting) and that helped a bit but what really did the trick was simply switching desktop modes from UNR to regular jaunty. Sped everything up. Thanks for the help.

---

### Post by treeingwalker on 2009-07-23
I am experiencing a similar issue on my Lenovo S10.  When I first installed Jaunty NBR, the Netbook layout was responsive and quite snappy.  At some point, though, it became very slow, and remains this way.  

I should note that it is only the Netbook main menu that is glacier-slow.  All other applications run just fine.

I do have quite a few applications installed, but as an experiment I pulled up the menu editor and disabled all but a few from every group, to see if it was having trouble dealing with so many menu items, but that did not change the behavior.

I am using xfs and not ext3 for all but the /boot and /root partitions, but like I said, at one point, the Netbook layout worked fine, and it has had xfs from the get-go. 

However, when I switch to the standard GNOME layout, it works just fine.

I tried rebuilding all my gconf data from scratch, but it made no difference.  There has to be something specific about the netbook layout.

I'm not very conversant in the way GNOME works, but can anyone point me to a log or config file that I could at least send to the NBR team so that they can try to figure it out?  I like the Netbook layout, but I like to switch to the standard layout when I hook it up to a larger external monitor.

---


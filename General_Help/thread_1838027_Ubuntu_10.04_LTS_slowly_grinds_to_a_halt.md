---
title: "Ubuntu 10.04 LTS slowly grinds to a halt"
date: 2011-09-02
forum: General Help
---

### Post by luds34 on 2011-09-02
Okay,

I've been using a form of linux as a file server, firewall, http host at home for a number of years going back to older versions of mandrake.

Recently my configuration was an old dual PII 350 system with 256 megs of RAM running ubuntu 10.04. While trying to do much in gnome was a little slow and not very responsive, the machine would run for months and serve it's purpose.

A few months ago a brown out (combine with my UPS being so old the battery was shot) causes the machine to lose power, boot up, lose power during boot, etc. Being everything was running from a hardware RAID 5 controller from LSI (with no battery cache) it corrupted enough of the system that I had to reinstall.

I took the opportunity to upgrade the aging PII hardware and picked up the new AMD E-350 "APU" for the performance boost and the very nice low TDP of 18 watts.

The issue I seem to have is the performance of the system slowly crawls to a halt the longer it runs. After a clean boot everything works great, it's responsive, etc. But even after a day it seems to be considerably slower. And after a week, say just trying to move a window causes it to pause for a long time period before it responds. doing things across SSH are even very slow to respond. The linux cpu usage will reach numbers like 5 or 6. Running top show's hi "waiting on IO" typically during this time.

I've been hitting up google off and on the last couple months and have not found anything that has helped.

Let's see, I have 4 gigs of RAM and it seems to all get used within a day which seemed strange to me. No single process stands out as eating up all of it (largest was 3 or 4%). It took a tiny bit of work, but I did install the E-350 video drivers by downloading them from AMD's website soon after install. Oh, and I do have that LSI Megaraid-4 or something RAID 5 controller. But that has worked fine in the past.

Is there some potential system board driver issue or something I might have with using too new of hardware with an older release? I wanted the 3 years of updates and such so went with the 10.04 LTS.

Any thoughts, ideas, probing questions from the linux guru's would be much appreciated. I've had a couple runs of 1+ year uptime with this old box. I'd like to get back to a point where I can leave it up and running for a month or two.

Thanks in advance.

---

### Post by switch10 on 2011-09-02
Is there a reason you need a GUI?  Or are you using this system as a file server strictly?  You can save yourself a lot of headaches (unneeded programs, video card drivers, etc.) and just install the stripped down server edition of Ubuntu.

Is there a chance that you have some scripts running in a loop somewhere?  I had a similar problem with an rsync script (with one little mistake....) I wrote that was running as a cron job in the background.

---

### Post by Overcast32 on 2011-09-02
Here's a link to a page that shows how to not load the UI at default, easily reversible. 


[http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/](http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/)


Could run it without the GUI a while; if it runs steady for a while it's probably some app or a looping script I would guess.

Or maybe boot a live CD and see if you get the same results - that should narrow it between hardware and software.

---

### Post by luds34 on 2011-09-03
No,

I technically do not need a gui. In fact historically when using the RPM based distros I would just boot to INIT 3.

But the gui is handy from time to time. Since it is a machine that is always on, just having quick access to a web browser to check weather before running out the door, etc. is useful.

That was one of the thoughts with upgrading the hardware on this box, so that it could be used for light workstation use.

While I agree you make some good points, that something related to the Xwindow system is probably the most likely culprit, I just have the feeling it is something more fundamental.

Thanks for the help so far.

---

### Post by switch10 on 2011-09-03
Paste the output of "top" when your system is running slowly.  At least the first 10 or so programs.  

```
top
```

Do you have any scripts in crontab?

---

### Post by .... on 2011-09-03
Some people get confused about the amount of RAM "used" because of how virtual memory works. I'll use my system as an example:
```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3902       2892       1009          0        133       2099
-/+ buffers/cache:        659       3242
Swap:         4094         55       4039
```

Most people would think that 2892 KB of RAM is used, but in reality there's just a lot of old, cached data that could be swapped out to disk if there was a sudden demand for lots of memory. The important number in the above example is 3242 KB of available RAM.

---

### Post by luds34 on 2011-09-03
Sorry for the slow response, I've been doing a lot of work on the house today getting it in top shape for a possible sale.

Okay, I'm running no cron jobs. I've been this close to adding a "reboot every night" one though. :)

Valid point on the memory. I thought about that too, good to have that confirmed. The linux kernal for quite some time has been quite aggressive at caching and such. In short, I'm using zero swap.

Nothing exciting to paste from top in terms of top processes, especially since killing the gui. My top process is polkitd using 1.3%. After that a number of mysqld. Should I see 8 of those guys?

After posting with you guys last night. I decided to kill GDM and run without it for a bit to see what happens.

My only connection is an ssh connection I just initiated. It takes like 10 seconds or something to finally get logged in. Running uptime shows

0.53, 0.19, 0.11

As if the machine was cool hanging out until I just stressed it with a login request.

I'm starting to think my issue is related to some poor driver or something related to the new system board. I'm definitely running into some sort of I/O issue as both top and htop are showing lots of waiting on I/O if anything is trying to be accomplished.

Is it worth considering the latest greatest version of Ubuntu or something to see if it covers this potential scenario? 

Totally off topic but could I take a short cut and install a new OS over the current one without having to format and keep all my config files and software installed?

So in short I'm back to this concept of really poor I/O performance. The thing is, although I have a RAID controller with a number of 2 TB drives. The system boots and runs from just a 250 gig Samsung drive that is connected directly to the motherboard's built in controller. My point being it's not just limited to the RAID partitions. And ironically they both bench well on synthetic benching software.

Hmmm... just has me a bit perplexed. Thanks again so far.

---

### Post by Overcast32 on 2011-09-03
Just a thought... maybe check some BIOS settings? Could be an issue with a driver plus those - maybe Hyperthreading, etc - maybe worth a shot.

---


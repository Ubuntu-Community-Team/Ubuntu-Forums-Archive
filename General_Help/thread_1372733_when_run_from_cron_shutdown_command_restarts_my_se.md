---
title: "when run from cron shutdown command restarts my server instead of shutting it down"
date: 2010-01-04
forum: General Help
---

### Post by silark on 2010-01-04
I want my server to automatically shutdown at 23:59 and startup at 8:00. The startup is handled through by bios but the shutdown is to be managed through cron. I thought I had this working, I actually swear I had it working because I thought the uptime command showed the appropriate uptime. I happened to be up and was streaming a movie from my server when at the time it should've shutdown it actually just restarted. If I run the shutdown -h now command by itself it works well but the scheduled command just restarts the server. Here is the what is shown when I enter crontab -e.

# m h  dom mon dow   command
59 23 * * * /sbin/shutdown -h now

This well and truly has me stumped any ideas?

---

### Post by jamesisin on 2010-01-04
You could try using the -P (or perhaps the -H) argument instead.

Are you sure the problem is in the command and not with whatever your bios is supposed to do to start it up automatically?

You could create a temporary job to shutdown at, say, 20:00 and up again at 20:10 to watch what it does exactly (and play with whatever settings you are able).

---

### Post by x33a on 2010-01-04
Try disabling the bios restart and see if the scheduled shutdown runs properly then.

---

### Post by silark on 2010-01-04
Thanks for the quick responses. I tried disabling the bios setting but no luck. Could I ask the difference between the -h and the -p switch?

---

### Post by jamesisin on 2010-01-04
Case is important: -P powers off the machine, -H halts the machine, -h halts the machine but gives the system the option to either halt or power off.

---

### Post by dcstar on 2010-01-05
> **jamesisin said:**
> ........
You could create a temporary job to shutdown at, say, 20:00 and up again at 20:10 to watch what it does exactly (and play with whatever settings you are able).

Starting off a cron job at 23:59 may cause issues if the process is still running when the midnight date changeover occurs - especially the shutdown process which must kill off various parts of the running system as it proceeds.

A test at a different time might be illuminating.

---

### Post by silark on 2010-01-05
Hi guys thanks again for all the help on this one. I had the chance to test running the job at a couple of different times and it doesn't matter what time of day I set it for it always restarts the server instead of shutting it down. I will try the different switches that were suggested and come back with results.

Also this is the message I see in my SSH session when the reboot happens:

Broadcast message from root@albert
        (unknown) at 15:44 ...

The system is going down for halt NOW!

---

### Post by silark on 2010-01-08
I changed the time my cron job ran so it ran at midnight instead of 23:59 and it worked well. The weird thing is I put the cron job back the way it was (running at 23:59) to prove conclusively that the time was the issue but it worked fine this time. 

My current uptime shows that the server has been up only 2hrs 10mins which means it turned on at 8:00am as it should. This has me completely puzzled as the job is now shutting down properly with the bios settings enabled and the time at 23:59. Anyone have any ideas on this as I'd like to ensure this doens't happen again.

Thanks

---

### Post by jamesisin on 2010-01-08
So, you futzed with it but returned it to the previous state and yet it is now working as expected rather than failing as it had been?

---

### Post by silark on 2010-01-09
Correct. I only changed the time to test that theory and it worked properly. I then changed it back to the way it was and it still worked properly and has been working for a couple of days. This one is a mystery.

---

### Post by dcstar on 2010-01-10
> **silark said:**
> Correct. I only changed the time to test that theory and it worked properly. I then changed it back to the way it was and it still worked properly and has been working for a couple of days. This one is a mystery.

Has the hardware had a total power disconnect (that means the cable is unplugged for at least 30 seconds) recently?

---

### Post by silark on 2010-01-11
no, and the server is stored behind a tv cabinet with no access so nobody else has removed the power cord.

---

### Post by dcstar on 2010-01-12
> **silark said:**
> no, and the server is stored behind a tv cabinet with no access so nobody else has removed the power cord.

PC hardware can get itself into an unstable state that only a total power disconnection can clear up.

---

### Post by silark on 2010-01-14
Ok I'm back...last night the same thing happened, my shutdown turned into a restart. Nothing at all has changed on the device. I had left the cron job to run at 23:59 and the shutdown had been working well until last night. I could ssh into the server 4 minutes before it was meant to switch itself on this morning, and the uptime indicated at 23:59 it restarted. 

This really doesn't add up at all. I'm going to leave the cron job setup as is and see if I get a restart tonight. If I do I think I'll change the time to 0:00 and test that for a couple of days to see what happens. Can anyone else can think of a different test I should run to pin this down.

---


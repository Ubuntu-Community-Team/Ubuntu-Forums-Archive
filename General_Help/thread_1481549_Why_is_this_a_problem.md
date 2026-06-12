---
title: "Why is this a problem?"
date: 2010-05-12
forum: General Help
---

### Post by isecore on 2010-05-12
I used to get upset over the I/O bug. Whatever it is. I try to post bug-reports that just disappear or are marked "invalid". I try posting here in the forum, and I know I'm not alone.

But I've grown tired. Either I will accept that Ubuntu will never actually fix the I/O load bug (or whatever it is) or I will change distro. Or, third (and scariest) alternative: I go back to Windows after three years of using Ubuntu and Linux.

I'm so tired of this. I'm tired of having a desktop that becomes gray for no reason. I'm tired of having apps that act sluggish, and I'm tired of having a monstrous system that feels much slower than my computer I had six years ago.

Most of all I'm tired of how nobody seems to think this is a real issue, and tired of people being very quick to blame some kind of user-error.

I attach a small screenshot of my system load applet. This is what it looks like most of the time. Load shoots up for no apparent reason and applications turn grey and unresponsive. A minute or two later the background load goes down a bit, and I can return to using my computer, even though it's incredibly sluggish.

If anyone cares, well then great. I'm tired of this.

---

### Post by jocko on 2010-05-12
Do you have any links to these bug reports?
If a bug is marked as invalid, you have probably not included enough information for anyone to even know where to start troubleshooting...

---

### Post by bredman on 2010-05-12
I suggest you try the following to find out what is killing your machine...

Create a file /home/user/toplog with the following contents
/bin/date >> /var/log/top.log
/usr/bin/top -b -n 1 >> /var/log/top.log

Make the file executable
chmod +x /home/user/toplog

Edit the superuser cron table
sudo crontab -e

Enter the following into the crontab
*/5 * * * * /home/user/toplog

You will now be creating a log of the resource usage every 5 minutes. If your machine slows down, take a note of the time, and look in the file /var/log/top.log for the data for this time period.

To stop the logging, use sudo crontab -e and delete the line that you added.

You may need to delete the file on a weekly basis to stop it growing
sudo rm /var/log/top.log

Best of luck...

---

### Post by isecore on 2010-05-12
Here's one bugreport:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268588](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268588)

Here's another:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094)

I can't find the ones I've added, so I guess they disappeared or whatever. They're not listed on my userpage at Launchpad even though I know I filed at least 6-7 of them the last two years. Whatever.

As for the top-logging, that's a nice idea. However, since this is seemingly a kernel-issue it doesn't show up in any monitor software such as top or htop. My guess it's because the process is too low or something (not too knowledgeable about this). All I see in htop is that the most heavy application uses like 2%, yet my computer is greyed out and standing still.

To the extent of my knowledge I have yet to find a way to track this or debug it or whatever. Disk-activity is a trigger, moving/copying files, but it also happens randomly.

---

### Post by mb_webguy on 2010-05-12
Yeah... asking "Why does my CPU/memory keep pegging 100%?" is like telling the doctor "Why do I have a fever?".  Without more information, it's impossible to diagnose.  I don't think anyone doubts that your computer is indeed pegging 100% for short periods, but it could be due to any process you have running.  I don't know about you, but I currently have almost 200 processes running at any given time.

You could try to identify the problem process by running the command "top -d 5 -b > system_resources.txt" in the terminal, which will create a snapshot of your current processes and system resources every five seconds until you hit Ctrl-C.  You can change the interval to whatever you think is appropriate, and you should stop and restart the command periodically since the output file can get rather large if you let it.  Once you manage to capture a period where your system freezes, you'll be able to identify the problem by looking at the system_resources.txt file, and then ask for help or file a bug report.

But without more information about the problem, particularly what's causing it, you're not going to be able to find much help with fixing it.

EDIT: Darn... I've been ninja'd.  Though my version of top logging is a bit simpler than the one above.  And I kind of doubt that it's a kernel-level problem, since a lot of other people would be reporting the same problem if that were the case.

---

### Post by isecore on 2010-05-12
Ah, so by your logic it's like taking your car to the mechanic, saying "there's a weird noise" and then the mechanic tells you "Sorry, until you can tell me precisely what's causing it and how to fix it I can't do a thing".

Look, I'd love to help out with whatever information you need. So let's start off with the basics.

I'm running Ubuntu Lucid 10.04 64-bit on a Phenom II 955. The motherboard is a Gigabyte GA-790FXTA-UD5 (AMD 790FX + SB750 chipset). I've got four gigabytes of DDR3-somespeed RAM, and the system is installed on two virtually identical Western Digital 1TB SATA/300 drives that I've LVM'ed together. The graphics card is a ATI 5870 (yeah, not the most Linux-friendly, I know, but I had the same problem in my previous machine). Filesystem is EXT4.

My previous machine, which was also afflicted by this bug was a AMD Phenom 9500. It sat on a Gigabyte GA-MA790FX-DS5 (AMD 790FX + SB600 chipset). It had four gigabytes of DDR2-somethingspeed RAM. It had one Western Digital SATA/300 1TB drive in LVM (I had planned on expanding it but it never happened) and it ran Karmic on EXT4 filesystem.

I'm logging top-resources now and will do it for the next 24 hours or so, but I doubt it will show anything. Like I said, I don't know WHERE this bug is, but it is a bug and it's somewhere in Ubuntu and I am not the only one affected. I've found threads here and there on the web detailing the same phenomenon as I'm experiencing and there's no red thread as to hardware - I've seen people reporting it with all kinds of hardware, not just AMD/ATI but also various Intel-configurations.

If there's anything else you can think of I'll be happy to try it. Every time I've started a thread about this in the past however it's come to nothing and the general conclusion is that somehow this is my own damn fault (which it isn't).

---

### Post by jocko on 2010-05-13
> **isecore said:**
> Ah, so by your logic it's like taking your car to the mechanic, saying "there's a weird noise" and then the mechanic tells you "Sorry, until you can tell me precisely what's causing it and how to fix it I can't do a thing".
Well, what you're doing is more like calling the mechanic and telling him "there's a weird noise", and expect him to fix it without even seeing your car, or telling him where the noise come from. 
The reason the bug you linked to is not solved is probably because there is not enough information to know what causes it (despite almost 300 posts).
I'm almost sure that many of the people commenting on the bug experience completely different bugs, and some of them are not really bugs. Some of the posts say that "the system becomes slow when the swap file is used", which is exactly what you would expect when the hard drive is used instead of ram, and the solution would be to buy more ram.

> **isecore said:**
> If there's anything else you can think of I'll be happy to try it. Every time I've started a thread about this in the past however it's come to nothing and the general conclusion is that somehow this is my own damn fault (which it isn't).
I'm sure it's not your fault, but to be able to fix it the devs need to know more than just the symptoms. Since this does not happen on all machines (I've never experienced it in any of the three computers I've ran ubuntu on), I guess it's something specific to some of your hardware.

Here's a few things that I can think of to help you narrow things down.
Check the [main bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094") and it's duplicates if anyone else have a similar hardware setup as you.
Both of your machines are amd based. Could it be limited to some amd based machines?
You use LVM on both of the affected machines. Could the problem be with LVM? Is there any way you can try how it works without LVM?
Which pata/sata chipset do you use on those motherboards? Which kernel module(s) do they use? Is there any way you can try another sata controller (I think your motherboard have more than one).
Is there any dmesg output when you experience the bug?
And from the latest comment (#7) in [this report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268588"): Is there anything else that shares the same irq as the sata/pata chipset you're using?
Do you experience any other problem that may (or may not) be connected? Stuttering audio? Graphic glitches?

---

### Post by isecore on 2010-05-13
I understand that this bug is difficult to locate, but I feel that it should be taken more seriously by devs than they're doing. Right now the attitude is "we'll look at it some time in the next ten years maybe".

It's not an AMD-related bug. I remember when googling and finding other forums that various hardware configurations are affected by it. Intel-processors, Intel-chipsets.

It's not LVM. I considered it, and tried running a system without LVM and it made no difference.

My current motherboard has an additional SATA-controller running on a Marvell chipset. I've tried running off of it, no difference. I attach a file with my lsmod output. As for the shared IRQ's, there's no other way. It's a fact in modern computers that all the IRQ's are shared.

But like I said, I don't think this will ever be fixed. It's not a priority, even though it should be, and everyone acts as if it's the users affected who should figure this out and not the other way around. I've pretty much given up, and when I finally can't tolerate this extremely annoying bug any more (or fight in forums and on launchpad) then I'll just either switch to something else or go back to Windows.

I don't mean to be hostile, but every time I bring this up I always get treated as if I'm taking crazy-pills. So pardon my frustration.

---

### Post by jocko on 2010-05-13
> **isecore said:**
> As for the shared IRQ's, there's no other way. It's a fact in modern computers that all the IRQ's are shared.
Yes, all modern computers have shared irq's, but some devices act weirdly when they share irq with something else (haven't happened to me since the windows 95 days, but I guess it can  still happen). Sometimes you may need to switch the irq assignment in the bios (if that's possible). But I'm sure you would get some kind of dmesg output from such a conflict.

Edit: I just checked my bios (gigabyte P55-UD4), and there is no way to change irq's, so I guess this is considered to not happen anymore...

---

### Post by isecore on 2010-05-23
Oh yeah. 28 load average when trying to save a VirtualBox-machine. Lovely.

---

### Post by warfacegod on 2010-05-23
How long have you had this particular install? Your details say your running Karmic testing. This *could* be a beta thing.

Do you use any Firefox add-ons? I've had a few of the F.F. add-ons make my system behave like your describing. CPU spikes, greyouts, etc.

---

### Post by isecore on 2010-05-23
Oops, I fixed that. I'm running Lucid, release, upgraded from a Karmic (non-beta) install.

Firefox has nothing to do with this. The symptoms are there even with no applications running. Sometimes load just shoots through the roof, and all I can do is twiddle my thumbs until my computer realizes it's a computer and not a doorstop.

I'm considering doing (yet another) fresh install, but it's not tempting since I'm pretty sure it won't fix the problem, and it will require a lot of work. I still maintain that this is an Ubuntu-bug and should be fixed by the developers.

> **warfacegod said:**
> How long have you had this particular install? Your details say your running Karmic testing. This *could* be a beta thing.

Do you use any Firefox add-ons? I've had a few of the F.F. add-ons make my system behave like your describing. CPU spikes, greyouts, etc.

---

### Post by warfacegod on 2010-05-23
Don't be so sure about Firefox. One of the add-ons that gave me trouble didn't care if F.F. was running or not. Wish I could remember its name.

---

### Post by llamabr on 2010-05-23
For my part, a fresh install isn't really that much work at all.  And is a nice way to be sure that it's not a problem with some setting that you made years ago, and forgot to change, etc.

I'd back up my home dir, burn a new disk, and start over.  I find that I can do a install in 30 minutes these days.

---

### Post by isecore on 2010-05-29
Well, FWIW this is not an LVM or 64-bit related problem. I took backups of my 500 gigs of data, then spent the day doing a variety of fresh installs. 

I did 64-bit installations with and without LVM, and I did 32-bit installs with and without LVM. Fresh installs each time, identical every time except for those variances, always on the exact same machine.

Every single time the bug was there. Oh happy days.

---


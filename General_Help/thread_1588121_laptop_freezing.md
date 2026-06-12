---
title: "laptop freezing"
date: 2010-10-04
forum: General Help
---

### Post by ajy0852 on 2010-10-04
Hi,

I have a Toshiba laptop that seems to be freezing on extended operations involving the file system/hard drive.

(that's kind of a guess on my part).
The system has frozen during the last day or two when I:
- try a large file operation with Nautilus
- try exporting a large video file from Kdenlive
- try formatting the disk for a new install of Maverick (I decided that with the new version almost out, I might try upgrading in case I broke my system)

What I see is the screen freezing and the mouse does not move. As I said, I tried installing the Maverick RC from the Alternate CD (I wanted to do a minimal install). The install hung on the partitioning step and the caps-lock key started blinking (though I don't get this in other cases). I have booted into my Lucid live-cd and a Puppy live-cd to try Gparted, with the same results - the system freezes (but the caps-lock key doesn't blink).

Puppy HAS performed better generally, for example I was able to complete my large file operation (backing things up!) but it is freezing on the partitioning step.

Any ideas? am I going to need to invest in a new HD or other hardware?

Thanks in advance, this is NOT an area that I'm familiar with.

---

### Post by Mark Phelps on 2010-10-04
The one thing that all your experiences had in common is that you were trying to do a large number of writes to the hard drive.

When bad blocks (or nearly-bad blocks) are encountered, the write will be tried repeatedly until the writing source simply gives up.

This will give the impression of the system "freezing", when, in fact, it's running full-throttle but just trying to write (or maybe, read) the same block over and over and over.

To check your drive, you need to find the make and model number, go to the manufacturer's website and see if they have a drive health utility you can download and run.

Some of these have to be run in MS Windows, others can be burned to a CD and booted from that CD.  It depends on the utility in question.

---

### Post by ajy0852 on 2010-10-04
Mark, thanks for your reply. I had noticed everything involved the HD as well.

My hard drive is a Toshiba-branded drive. I couldn't find any diagnostics tools on their site, so I called them (sat on the phone for a while) and the guy told me Toshiba actually doesn't produce diagnostics software for their drives.

Is there a Linux utility that checks/repairs drives? Otherwise, I'm probably stuck with buying a new one, right?

---

### Post by ajy0852 on 2010-10-05
I decided to go ahead and get another HD (extra space, anyway). After installing it I'm still encountering the same problems: I can't get through formatting the drive. I've tried in the Maverick RC Alternate CD (hangs at 33% of formatting the drive and the caps-lock key blinks), and using GParted on the Puppy live cd as well as the Lucid live CD that I had used back in April to install Lucid. On the live CD's, GParted gets started going and then the system "freezes" (no caps lock key blinking). So I'm guessing it's not the HD, unless I got a bad one, which I don't think is too likely). Any other ideas? Thanks again.

EDIT: Solved. I needed a new stick of RAM.

---

### Post by SriNarayanan on 2010-10-20
**Freese - blinking caps and scroll lock - acpi**  			 			 			 		   		 		 		Sony Vaio EB 16 FG - running ubuntu 10.10  froze while resuming from dimmed screen with blinking scroll lock and  caps log LED.

The scenario was this :-
I just downloaded the acpi using synaptic package manager.
Then installed laptop mode tool using synaptic.

*cat* /proc/sys/vm/laptop_mode
0

Means its not yet enabled.

But decided to remove it .(read  drive spin up and down is not good for HDD)

Had left the laptop for some time , it dimmed screen . When I resumed it froze.
No mouse movement.only blinking caps and scroll.

Just wondering if acpi is the culprit,since haven't seen this behaviour before and it happened after removing  laptop mode tools

It happened again , this time while playing a movie on totum .
I was running top on another terminal just to see cpu usage .

Now remove acpi , let me see if it happens again after the removal.

Also I am using a USB mouse , may be it has something to do ?

---

### Post by SriNarayanan on 2010-10-22
just today had another kernel panic , also just now came to know that this system behaviour is called kernel panic

see if this help

[http://ubuntuforums.org/showthread.php?t=1603231](http://ubuntuforums.org/showthread.php?t=1603231)

---


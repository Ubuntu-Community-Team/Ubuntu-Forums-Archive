---
title: "Ubuntu Driver Compatibility and Availablity"
date: 2011-02-09
forum: General Help
---

### Post by rabih_aa on 2011-02-09
Hello,
I have been a Windows user for a long time now. I have played around with Ubuntu and I am beyond impressed with the OS. I would like to make a complete migration to Ubuntu on a machine the I bought recently, however, I am worried about hardware incompatibilities and issues. These are the specs of the machine:

CPU: Intel® Core™ i7-950 3.06 GHz (overclocked at 20% or more)
HDD: 128 GB Kingston 2.5 inch SATA Gaming MLC Solid State Disk
HDD2: 1TB SATA-III 6.0Gb/s 64MB Cache 7200RPM HDD
MEMORY: 12GB DDR3/1600MHz 
MOTHERBOARD: (3-Way SLI Support) MSI X58A-GD45 Intel X58 Chipset SLI/CrossFireX Triple-Channel DDR3 ATX Mainboard w/ 7.1 Audio, eSATA, GbLAN, USB3.0, SATA-III, RAID, IEEE1394a, 3 Gen2 PCIe, 3 PCIe X1 & 1 PCI
VIDEO: NVIDIA GeForce GTS 450 1GB 16X PCIe Video Card
WIFI: Linksys WMP600N Wireless-N Dual-Band Adapter

I found the 64 bit driver for the video card at the NVIDIA website and I plan on using that. 
I am mostly concerned about the drivers for the motherboard and the Linksys WMP600N wifi card. Are these two pieces of hardware supported by Ubuntu 10.04 (64 bit)? How should I make them work properly and with full capabilities with a clean installation of Ubuntu? 
How can I make the whole system perform at its optimal levels, meaning are there any considerations to take for example to use all cpu cores or is this done by default?

Thank you.

---

### Post by gdonwallace on 2011-02-09
To get the most out of your Hard Drives and Memory, You will have to use the 64 bit version of Ubuntu.  Even then, I think the cap may be 8 gig of ram.  Someone else may be better able to answer that questions.

For Nvidia, Ubuntu has pretty decent driver support already built into it for the video cards.  There is a utility that You will have to run after installing to let it know to run video with "restricted" drivers (i.e. drivers provided by Nvidia)  After that no problems.

The wireless in Ubuntu has been real firm for me.  Although I see some threads about people having problems with wireless, I personally have not.  So your Linksys should not be an issue.

The only thing I am not 100% about is SLI.  In theory it should work, but I don't have a clue on this one.  You might want to search the forums for that one.

As for drivers, 95% of the time you won't need them.  I have been using Ubuntu for three years and only twice have I run into any issues where I have to force a driver to work.  

Good luck and welcome to the forums.

---

### Post by DrReaper on 2011-02-09
My advice is to dual boot windows and Ubuntu. You don't have to give much space to the windows but it's nice to have if you need a program running and you can't do it in Ubuntu. 

I have a system that is windows/ubuntu and it's running Ubuntu 95% of the time.

---

### Post by quadproc on 2011-02-09
> **rabih_aa said:**
> Hello,
I am worried about hardware incompatibilities and issues. 
I would suggest checking out the sticky threads at the beginning of the Hardware and Laptop forum - those are the hardware compatibility and incompatibility lists.  There is a good chance that your hardware will be found somewhere in those lists.
> 
How can I make the whole system perform at its optimal levels, meaning are there any considerations to take for example to use all cpu cores or is this done by default?
The kernel knows how to use multiple processors and will use as many as makes sense.  Most applications are written to use only one processor and there usually isn't anything that you can do about that.  But there is nothing to prevent you from running several copies of a program simultaneously - whether that would be useful is up to the design of the program.  Mostly, not useful.  If a task forks and does not extinguish one of the branches then multiple processors are a benefit, but most code is not written that way.

I decided on a 4 core processor because I figure my usage is usually similar to this: task 1 is whatever my main project is at the instant, for example, a word processor or a video display; task 2 is system stuff such as daemons, loggers, etc.; task 3 is something running in the background.  Since nobody makes a three core processor, I settled on four.

quadproc

---

### Post by rabih_aa on 2011-02-10
Thank you for the quick response guys:

@gdonwallace: I am installing Ubuntu 10.04 as I am type this, and I will try installing it tonight. I will go with your advice on the VGA and Wifi. SLI is not really important to me. The important thing is to get my GWT / Java environment up and running. Also, after I install tonight I'm gonna check if there is a cap on memory as you said.

@DrReaper: Makes perfect sense. I have another machine that has Windows only on it, and I think I will keep it that way. At least until I become proficient with Linux.

@quadproc: I will definitely check the sticky threads you mentioned before installation to double check. The installation should run smoothly, in theory.
> The kernel knows how to use multiple processors and will use as many as makes sense. Most applications are written to use only one processor and there usually isn't anything that you can do about that. But there is nothing to prevent you from running several copies of a program simultaneously - whether that would be useful is up to the design of the program. Mostly, not useful. If a task forks and does not extinguish one of the branches then multiple processors are a benefit, but most code is not written that way.

I decided on a 4 core processor because I figure my usage is usually similar to this: task 1 is whatever my main project is at the instant, for example, a word processor or a video display; task 2 is system stuff such as daemons, loggers, etc.; task 3 is something running in the background. Since nobody makes a three core processor, I settled on four.

I guess what you said there makes perfect sense. Its just that with windows I never thought about this. I like having this level of control under Ubuntu. Is there a specific way to dedicate tasks to processors or is it done again by the kernel? For example, following the logic you are using, I plan on having task 1 dedicated to Eclipse for java dev, task 2 for DB, task 3 for daemons and loggers.

---

### Post by quadproc on 2011-02-10
> **rabih_aa said:**
> 
I guess what you said there makes perfect sense. Its just that with windows I never thought about this. I like having this level of control under Ubuntu. Is there a specific way to dedicate tasks to processors or is it done again by the kernel? For example, following the logic you are using, I plan on having task 1 dedicated to Eclipse for java dev, task 2 for DB, task 3 for daemons and loggers.
As far as the operating system is concerned, processors are simply tools to be used when needed so the OS does not usually attempt to assign particular processors to particular tasks.  Of course, during initialization, only one processor is used until the OS has learned enough about its environment to make use of more processors so you might consider this to be an example of selecting a particular processor.

If you want to see a little bit of what the system does with multiple processors, look in the system log (/var/log/syslog) for strings including the word "processor" at a time shortly after you booted the system.

BTW, even though a task will begin its execution on a particular processor, it likely will not stay on that processor.  Each time the running processor gets interrupted, the task will be suspended.  When the task resumes it may very well be assigned to a different processor.  But this normally doesn't matter because the processors are identical.

There are normally quite a few tasks present in a system, even if the user is not doing anything.  Take a look at the output of ```
ps -e | more
``` - you will probably find 2000 to 3000 tasks.  Or, run the System Monitor utility located under the System>Administration choice, select the Processes tab, and look at the more interesting tasks.  While you are at it, select the Resources tab and see how much time each processor is busy.  Most of the time, most of my system is not doing anything.

quadproc

---

### Post by rabih_aa on 2011-02-10
Thank you so much quadproc for your time and valuable feedback. 
I dont know about this topic much right now, but by tonight I will learn more starting by your last reply. 
I will report back also.
Thank you.

---

### Post by quadproc on 2011-02-10
> **rabih_aa said:**
> 
I dont know about this topic much right now, but by tonight I will learn more starting by your last reply. 
I will report back also.
Thank you.
You are welcome, and welcome to the world of real computing :)

One more loosely related thought, if you ever encounter strange system behavior, especially intermittent problems, I would suggest reducing the overclocking some to see if that could be a problem.

A final thought: if you are satisfied with the responses that this thread has provided then please consider using the Thread Tools near the top of the page to indicate that the thread is Solved.  But if you would like to leave the thread open for more input then don't mark it solved, at least not yet.  Of course, you can always start another thread if you wish to start another discussion.

quadproc

---

### Post by rabih_aa on 2011-02-11
Hello quadproc. I worked on all the stuff we discussed last night and here is what happened. 
First, I installed Ubuntu 10.04 64-bit. I was not able to pick up the VGA drivers automatically (proprietary hardware drivers). Also the Wifi connection could never be established. It would always try to connect to my network, then asks for authentication again. This happens over and over. 
Then, I installed Ubuntu 10.10 64-bit. Everything seemed to go pretty well. I can see all processor cores working as you explained (thank you) and I can see that all 12 gigs of ram are in use. VGA works great and I can connect to the internet wirelessly. However, I keep getting this message on boot after post  (and on the terminal if you are able to somehow switch off the gui):

[	3.890588] Too many connections
[	4.167613] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[	4.168188] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[	4.168749] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
[	4.188995] phy0 -> rt2x00pci_mcu_status: Error - MCU request failed, no response from hardware

I'm starting to suspect that this is a wifi card issue, but I am not sure. Where should I go from here? I still have to investigate this further. Should I post this in a more relevant thread? 

Thank you.

---

### Post by quadproc on 2011-02-12
> **rabih_aa said:**
> . However, I keep getting this message on boot after post  (and on the terminal if you are able to somehow switch off the gui):

[    3.890588] Too many connections
[    4.167613] phy0 -> rt2x00pci_regbusy_read: Error - Indirect register access failed: offset=0x00007010, value=0xffffffff
{redundant entries deleted}
I'm starting to suspect that this is a wifi card issue, but I am not sure. Where should I go from here? I still have to investigate this further. Should I post this in a more relevant thread? 

This certainly does look like a wifi issue and unfortunately I cannot help with that because I do not use any wireless hardware - too much of a security leak.  But I have seen lots of wifi issues posted in the forums so I would suggest two things: one, search the forums for your wifi model to see if someone has already figured out how to deal with it, and two, start a new thread related to just the wifi issue.

But otherwise, it sounds like you are well on your way.  Congratulations!

quadproc

---

### Post by rabih_aa on 2011-02-12
Thank you so much quadproc.
I will look around for problems of this nature and possible solutions and try them out. 
If all else fails I will start a new thread.

---


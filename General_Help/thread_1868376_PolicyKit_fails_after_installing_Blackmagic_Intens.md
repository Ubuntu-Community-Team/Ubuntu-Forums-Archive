---
title: "PolicyKit fails after installing Blackmagic Intensity Pro drivers"
date: 2011-10-24
forum: General Help
---

### Post by 10fingers on 2011-10-24
Hi.

I have Ubuntu 11.04 64bit installed on my desktop. I installed latest driver for Blackmagic Intensity Pro PCIe card and broke PolicyKit. Sympthoms are: there is no sound devices, I can't mount disks, can't manage groups and users and so on. When I'm turning driver off all sympthoms disappears.

My dmesg [http://pastebin.com/dcqjuEsu](http://pastebin.com/dcqjuEsu), lsmod [http://pastebin.com/vmJja9x5](http://pastebin.com/vmJja9x5).

TIA

---

### Post by Smithy856 on 2012-01-06
Did you figure out a fix for this?

Just stumbled across your post. I too have installed an Intensity Pro PCIe into my Ubuntu 11.04 64bit build. Spent the past week getting the blackmagic card working, only to find out that it appears to have broken policykit. Experiencing exactly same symptoms as you've described. Can't edit/add users through users-admin and also can't shutdown machine without sudo -h shutdown now.

---

### Post by 10fingers on 2012-01-06
Unfortunately not. I've tried to get answer from support with no luck. Please write them request. Maybe they will pay attention to this problem.

---

### Post by Smithy856 on 2012-01-09
I emailed Blackmagic support, they came back fairly quickly with this..

> Thanks for reporting the Linux issues. The shutdown issue has been logged as a bug (reference #15006) to be addressed by a software engineer when possible. You can get around this issue by shutting down via the command line (using administrator privileges).
I was unable to reproduce the other issue that you reported - regarding being unable to add/ edit user accounts. I added test accounts using the GUI with Ubuntu 9.10 and Ubuntu 11.10 (we didn’t have a Ubuntu 11.04 installation available). Could you please elaborate on how you added and edited the accounts and what errors were reported.I think the issue relates to 11.04. I have installed Ubuntu 10.10  and it works perfectly with the latest blackmagic desktopvideo 9.0 driver.

---

### Post by 10fingers on 2012-01-09
> **Smithy856 said:**
> I emailed Blackmagic support, they came back fairly quickly with this..

I think the issue relates to 11.04. I have installed Ubuntu 10.10  and it works perfectly with the latest blackmagic desktopvideo 9.0 driver.

Great! I'll switch back to 10.04 (LTS) and try. BTW what do you do with your Intensity under Linux?

---

### Post by Smithy856 on 2012-01-09
I'm using the Intensity Pro to stream/record HDMI from my Android tablet. Luckily it works with Ubuntu 10.10 meaning that I won't have to resort to a Windows 7 build - which really would have been a very last resort.

---

### Post by 10fingers on 2012-01-09
What software do you use to stream? I'm going to use GStreamer with Intensity plugin but when I used it with webcam and ALSA audio source there was an issue with video and audio sync.

---

### Post by Smithy856 on 2012-01-09
I'm puling the HDMI-in into VLC to display the output. Used experimental VLC 1.2 which includes Blackmagic Decklink support, which covers Intensity too. Trial and error really.

What are you going to be capturing and doing with your Intensity?

---

### Post by 10fingers on 2012-01-09
>> What are you going to be capturing and doing with your Intensity?

I'm streaming live video from events. Now I'm using Win7 and XSplit Broadcaster which has pretty good functionality but I need to build "black box" without any proprietary software.

---


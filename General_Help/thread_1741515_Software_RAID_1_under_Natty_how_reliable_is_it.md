---
title: "Software RAID 1 under Natty: how reliable is it?"
date: 2011-04-28
forum: General Help
---

### Post by Gerhard Kremer on 2011-04-28
Hi,

I have put together a desktop system, which for business reasons I need to run with zero downtime; therefore, it has two HDDs to be used under RAID 1. 

I plan to use a software RAID with mdadm under Natty, but the (somewhat out of date) community page at
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) 
warns of the "fragile" state of RAID support under Ubuntu, which has me worried. 

I have searched the web and these forums, but the documentation about RAID on Linux that I've found is either years old or incomplete, which makes me wonder about the development state of mdadm. I want to use Linux very much, but not at the expense of sacrificing my business due to unreliable software. Stability is crucial for me. 

My question: Can I expect a RAID 1 array under Ubuntu + mdadm to be substantially more reliable, bugs and all, than a single HDD? If not, is there any better software RAID solution under Linux?

Also: this is my first experience with RAID of any kind. Is there anything I should be specially careful with when setting up or using the array?

Thank you very much for your help!

GK

Relevant parts of my system:
CPU: Intel Core i7 2500
Motherboard: Asus P8H67
HDD: 2 x Samsung Spinpoint F3 1 TB
RAM: 4 x G.Skill Ripjaws 4 GB

---

### Post by SeijiSensei on 2011-04-28
There's not much recent documentation for mdadm because it's already well-developed and works so well.  I don't why the documentation would suggest SW RAID is "fragile."

I've run servers for years with software RAID 1 and 5 arrays without incident.  

If you're still leery, get yourself a decent RAID card and use that instead.  [Newegg]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607%204025&IsNodeId=1&name=%2425%20-%20%2450") has some that get good reviews and work with Linux for under $50.

---

### Post by rubylaser on 2011-04-28
You can rest assured that mdadm is VERY stable.  I have also been running it for years on many systems, in RAID1,5,6,and 10.  I love the cost (free :) ), the portability to any Linux system, and the fact that I'm not dependent on a hardware controller.  When a hardware controller fails I would be forced to find a similar card to be working again.

I use hardware controllers on most of my servers at work because all of the servers are under service warranties, but at home I solely rely on mdadm.

---

### Post by wizard10000 on 2011-04-28
I have only two things to add but I think they're important.

1.  RAID is not a backup solution.  Someone who works for me almost became unemployed assuming that a big SCSI RAID5 array on a big HP server that was still under warranty didn't need to be backed up.  The big expensive RAID controller failed and wrote garbage to the array - the RAID controller was replaced under warranty but the data was unrecoverable.  Several years' worth of critical data was lost.

2.  An untested backup solution isn't a backup solution either  ;)

cheers -

---

### Post by Gerhard Kremer on 2011-04-29
Guys, thank you very much for your output! I appreciate it.

> **SeijiSensei]I don't why the documentation would suggest SW RAID is "fragile."[/quote]

Well, it says so up front on the page I linked  said:**
> the fact that I'm not dependent on a hardware controller. When a hardware controller fails I would be forced to find a similar card to be working again.

This is very good, since it removes a failure point in a proprietary, closed element (if the controller has a bug, good luck with the company tech support).

> RAID is not a backup solution.
Very true, and I don't plan to use it as such. I have external backup of all my data in another computer and an external HDD, plus cloud storage through Dropbox for the truly critical files.

I set up the array yesterday, and will test it thoroughly with all the data safely backed up somewhere else. If something interesting happens, I'll let you know.

Thank you again,

GK

---

### Post by sor on 2011-09-03
(Yes I know this is a few months old)

I can attest that what they mean by 'fragile' does not refer to the reliability of the excellent software RAID. It refers to Ubuntu's support for working out of the box with it. By that I mean making sure initramfs/grub rebuilds in such a way that the system will boot next time, etc, when things change on the system.

They should really add software raid to their graphical install partitioner dialog and test it well. Other distros have had it working for quite awhile.

---


---
title: "Problem with Dual Monitor"
date: 2011-05-05
forum: General Help
---

### Post by imafatmess on 2011-05-05
Hi there,

Earlier in natty this was working completely. It's only just started happening about a week ago. I don't know what changed, all I know is it suddenly stopped working. Basically the bar at the top is still there but there is black underneath. I can put windows there but I cannot see them (Just black). If I click on an indicator it looks on the bar as if it is being clicked but I cannot see the menu. I have attached a screenshot.

I hope someone can help,

Thanks very much!
David

---

### Post by nithska on 2011-05-09
I'm seeing this same issue across all accounts on the machine.  Interesting that on boot, the dual monitors work fine, but on login, the OP screenshot accurately represents what I see.
 
results of sudo lshw -C display; lsb_release -a
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:b0000000-b03fffff memory:a0000000-afffffff ioport:3050(size=8)
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty
-----------------------------------

Incidentally, and perhaps unrelated, I also see my one processor spike to 100% and beyond when I open gnome-appearance-properties, and once I close it both processors will spike until I kill the process.

Thank you for any help.

BB

CC-BY-SA Fiction Magazine: [http://www.fantastique-unfettered.com](http://www.fantastique-unfettered.com)

---

### Post by andrei_1 on 2011-05-09
> **imafatmess said:**
> Hi there,

Earlier in natty this was working completely. It's only just started happening about a week ago. I don't know what changed, all I know is it suddenly stopped working. Basically the bar at the top is still there but there is black underneath. I can put windows there but I cannot see them (Just black). If I click on an indicator it looks on the bar as if it is being clicked but I cannot see the menu. I have attached a screenshot.

I hope someone can help,

Thanks very much!
David

See this bug: [https://bugs.launchpad.net/unity/+bug/779681](https://bugs.launchpad.net/unity/+bug/779681)

Also my comment there suggests it was introduced by a massive update including X that came a few days after Natty was released.

Bummer! They should work on fixing it, not breaking it even more :(

---

### Post by andrei_1 on 2011-05-09
> **imafatmess said:**
> Hi there,

Earlier in natty this was working completely. It's only just started happening about a week ago. I don't know what changed, all I know is it suddenly stopped working. Basically the bar at the top is still there but there is black underneath. I can put windows there but I cannot see them (Just black). If I click on an indicator it looks on the bar as if it is being clicked but I cannot see the menu. I have attached a screenshot.

I hope someone can help,

Thanks very much!
David

See my message here for how I fixed this: [https://bugs.launchpad.net/unity/+bug/779681/comments/3](https://bugs.launchpad.net/unity/+bug/779681/comments/3)

---

### Post by Antarctica32 on 2011-05-09
I had this same problem but the opposite. My panel would only stay on my main screen but my desktop would go on both. I fixed it by setting the xorg.config file back to only 1 screen, saving it, shutting down, rebooting and trying it all over again with complete success.

---

### Post by nithska on 2011-05-11
andrei_1's suggestion is helpful (thank you!) but not a true fix.  I just wanted to note this since for a business, pinning these files is not a good option.  I probably should have stuck with the LTS version, but these last two releases were so stable, that I made the jump to 11.04 prematurely.  

This is the machine I use exclusively for the magazine, and I need the dual monitors for my workflow. 

Thanks to anyone working on these things, it is much appreciated.

BB
----------

---


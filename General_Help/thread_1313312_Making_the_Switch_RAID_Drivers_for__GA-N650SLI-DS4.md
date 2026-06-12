---
title: "Making the Switch: RAID Drivers for  GA-N650SLI-DS4L"
date: 2009-11-03
forum: General Help
---

### Post by ldavid on 2009-11-03
I have finally done it. Windows is gone. Linux Ubuntu is in. ;)

Before I install Ubuntu 9.10, I am trying to find linux drivers for my motherboard- however it seems my Gigabyte [COLOR=#fd6724]GA-N650SLI-DS4L[/COLOR][COLOR=#fd6724] [COLOR=Black]doesn't have drivers for linux on their website ([http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ProductID=2679#anchor_os](http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ProductID=2679#anchor_os)).

Basically, I want to run RAID 1 configuration- however I believe I need to provide the drivers for the RAID support (I needed to do this for windows). Is this right? If so, where am I able to get these linux drivers for my mobo? I've done a quick google search, but no luck...possibly I am not looking in the right areas.

Hoping all goes well- I can't wait to say goodbye to windows. :D

Cheers

David
[/COLOR][/COLOR]

---

### Post by ldavid on 2009-11-04
[COLOR=Red]**UPDATE**[/COLOR]

I tried to install ubuntu 9.10 anyway with the RAID setup and everything seemed to be working really well.

I set up the following partiitions:

#1: Ext4 - / (root directory for the OS) - 100GB~
#2: Ext4 - /home - 450GB~
#3: Swap - Swap Space - 50GB~

Everything was working smoothly, until I ran into the following installation error at 94%:

**"The 'grub' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot."**

Does this everytime without a doubt with a fresh install of ubuntu 9.10. :(

Any ideas?

Cheers

David

ps. Is 50GB too much for swap space? Unsure.. What is a good amount for this?

---

### Post by ldavid on 2009-11-04
I worked out my issues.

I changed the file system to ext3 and everything worked smoothly.

It seems there still have be a few bugs in ext4 that need to be ironed out.

Just posted this result in case anyone came across the same problem as me.

David

---


---
title: "hang at &quot;Begin: Adding live session user... ...&quot;"
date: 2011-03-24
forum: General Help
---

### Post by joeymac2011 on 2011-03-24
[SIZE=2]I'm trying to troubleshoot why I am not being able to log in to my persistent usb. Ubuntu 10.10.

I suspect the problem may have been when I resized and moved partitions to make more room for the home-rw and casper-rw directories. (I used Linux Live RescueCD) Something to do with "Ophaned nodes."

It boots up fine when I select the "Try Ubuntu without install.." option. Thats what I am on now but when I select my "Default" option which is the persisternt image I want to use. That is where the problems start.

Pressing TAB on the default option says [/SIZE][SIZE=2]"/ubnkern initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper -- persistent"[/SIZE].

Below is the errors I get:
___________________________________________________

Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/casper-premount ... done.
done.
Warning: Impossible to include the casper-sn Snapshot
Warning: Impossible to include the home-sn Snapshot
done.
Begin: Creating debconf-communicate fifo mechanism ... done.
Begin: Running /scripts/casper-bottlom ... Begin: Moving mount points... ... done.
Begin:  Adding live session user... ...
___________________________________________________

After a while the "splash screen" comes back. I hit alt-t and the same error is repeated.

Can someone please point me in the right direction to start looking. I know it's corrupt but not sure where.

Thank you in advance.


----------------------------------------------------------------------------------

UPDATE:

After cloning the USB to the HDD as a test facility.

I deleted the "casper-rw" partition.

Now it lets me boot properly but now its asking for a username & password. I've tried the default user and passwords given but still no luck.

Error says: "...not in the sudoers list..". 

:confused::confused::confused::confused::confused::confused::confused::confused:

---


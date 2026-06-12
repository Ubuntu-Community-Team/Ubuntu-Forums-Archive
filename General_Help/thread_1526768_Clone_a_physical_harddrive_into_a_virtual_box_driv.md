---
title: "Clone a physical harddrive into a virtual box drive"
date: 2010-07-08
forum: General Help
---

### Post by bgrohe on 2010-07-08
I have two old windows 95 computers. The problem is I have files and programs that have specific settings that I need. The computers are old and I want to just make a copy of the hard drive and insert it into virtual box. How can I do this?
Thanks in advance.

---

### Post by jkid on 2010-07-08
guy windows 95..omg just try to put ur things in CDs or something

---

### Post by gdonwallace on 2010-07-08
There are several open source programs that can be used to clone / ghost hard drives.

Clonezilla is a good option ([www.clonezill.org](www.clonezill.org)). You can clone to an existing hard drive, or to a networked hard drive if you have the IP address, DNS gateway. 

 Also, you might check [www.softpedia.com/linux](www.softpedia.com/linux) and search for clone or ghost software.  That will get you a linux alternative.

Good luck.

---

### Post by bgrohe on 2010-07-08
Jkid: There is software that is not developed anymore that is on there

gdonwallace: can clonezilla export to virtualbox?

---

### Post by dabl on 2010-07-08
Clonezilla can make a compressed image of a hard drive -- I have done that.

I would suppose that you could do something like:

1. Use clonezilla to image a Win 95 drive to some other hard drive/partition.

2. Set up a VBox or VMware VM that has an empty partition on the virtual drive.

3. Use clonezilla in the VM, and assuming bridged or NAT networking, or a USB-connected external drive with the image on it, restore the backed-up image to the empty partition on the VM.

That's pretty high level -- I'm sure there are details to deal with, but I don't see why it couldn't work.  Before imaging the Windows drive, I would remove every bit of software that is not needed, then run disk cleanup, then run defrag, to get it to the smallest size possible.

---

